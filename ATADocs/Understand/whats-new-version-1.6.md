---
# required metadata

title: Novidades na versão 1.6 do ATA | Microsoft Advanced Threat Analytics
description: Lista as novidades na nova versão 1.6 do ATA e seus problemas conhecidos
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: a0d64aff-ca9e-4300-b3f8-eb3c8b8ae045

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades na versão 1.6 do ATA
Essas notas de versão fornecem informações sobre problemas conhecidos nesta versão da Advanced Threat Analytics.

## Quais são as novidades na atualização 1.6 do ATA?
A atualização 1.6 do ATA fornece melhorias nas seguintes áreas:

-   Novas detecções

-   Aprimoramentos nas detecções existentes

-   O Gateway Lightweight do ATA

-   Atualizações automáticas

-   Melhor desempenho do Centro do ATA

-   Menos requisitos de armazenamento

-   Suporte ao IBM QRadar

### Novas detecções


- A API de Proteção de Dados (DPAPI) da **Solicitação de Informações Particulares de Proteção de Dados Mal-intencionados** é um serviço de proteção de dados baseado em senha. Esse serviço de proteção é usado por vários aplicativos que armazenam segredos do usuário, como senhas de site e as credenciais de compartilhamento de arquivos. Para dar suporte a cenários de perda de senha, os usuários poderão descriptografar os dados protegidos usando uma chave de recuperação que não envolva a senha deles. Em um ambiente de domínio, os invasores podem roubar a chave de recuperação remotamente e usá-la para descriptografar os dados protegidos em todos os computadores ingressados no domínio.


- O Reconhecimento por **Enumeração de Sessão de Rede** é um estágio chave na cadeia avançada de encerramento de ataques. Os DCs (Controladores de Domínio) funcionam como servidores de arquivos para fins de distribuição do Objeto de Política de Grupo, usando o protocolo SMB. Como parte da fase de reconhecimento, os invasores podem consultar o DC de todas as sessões SMB ativas no servidor, o que permite que eles obtenham acesso a todos os usuários e endereços IP associados a essas sessões SMB. A enumeração da sessão SMB pode ser usada pelos invasores para acessar contas confidenciais, o que os ajuda a se mover lateralmente na rede.


- **Solicitações de replicação mal-intencionadas** Em ambientes do Active Directory a replicação ocorre regularmente entre Controladores de Domínio. Um invasor pode falsificar uma solicitação de replicação do Active Directory (às vezes representando um Controlador de Domínio), permitindo que o invasor recupere os dados armazenados no Active Directory, incluindo hashes de senha, sem utilizar técnicas mais invasivas como a Cópia de Sombra de Volume.


- **Detecção da vulnerabilidade MS11-013** Há uma elevação da vulnerabilidade de privilégio no Kerberos que permite que determinados aspectos de um tíquete do serviço Kerberos sejam forjados. Um usuário mal-intencionado ou um invasor que explore com êxito essa vulnerabilidade pode obter um token com privilégios elevados no controlador de domínio.


- **Implementação de protocolo incomum** As solicitações de autenticação (Kerberos ou NTLM) normalmente são executadas usando um conjunto padrão de métodos e protocolos. No entanto, para autenticar com êxito, a solicitação deve atender apenas a um conjunto específico de requisitos. Os invasores podem implementar esses protocolos com pequenos desvios da implementação padrão no ambiente. Esses desvios podem indicar a presença de um invasor tentando executar ataques como Pass-The-Hash, Força Bruta, entre outros.


### Aprimoramentos nas detecções existentes
O ATA 1.6 inclui lógica de detecção aprimorada que reduz cenários de falsos positivos e falsos negativos para detecções existentes, como Golden Ticket, Honey Token, Força Bruta e Execução Remota.

### O Gateway Lightweight do ATA
Essa versão do ATA introduz uma nova opção de implantação para o Gateway do ATA, que permite a um Gateway do ATA ser instalado diretamente no Controlador de Domínio. Essa opção de implantação remove funcionalidades do Gateway do ATA que não são essenciais e introduz gerenciamento dinâmico de recursos com base nos recursos disponíveis no DC, o que garante que as operações existentes do DC não sejam afetadas. O Gateway Lightweight do ATA reduz o custo da implantação do ATA. Ao mesmo tempo, ele facilita a implantação em sites da filial, em que há capacidade limitada de recursos de hardware ou impossibilidade configurar o suporte de espelhamento de porta.
Para saber mais sobre o Gateway Lightweight do ATA, confira [ATA architecture](/advanced-threat-analytics/plan-design/ata-architecture#ata-gateway-and-ata-lightweight-gateway) (Arquitetura do ATA)

Para saber mais sobre considerações de implantação e como escolher o tipo correto de gateways para você, confira [ATA capacity planning](/advanced-threat-analytics/plan-design/ata-capacity-planning#choosing-the-right-gateway-type-for-your-deployment) (Planejamento de capacidade do ATA)


### Atualizações automáticas
Começando na versão 1.6, é possível atualizar o Centro do ATA usando o Microsoft Update. Além disso, os Gateways do ATA agora podem ser atualizados automaticamente usando o respectivo canal de comunicação padrão com o Centro do ATA.
### Melhor desempenho do Centro do ATA
Com essa versão, uma carga mais leve do banco de dados e uma maneira mais eficaz de executar toda a detecção permitem que muito mais controladores de domínio sejam monitorados com uma único Centro do ATA.

### Menos requisitos de armazenamento
O ATA 1.6 necessita consideravelmente de menos espaço de armazenamento para executar o banco de dados do ATA, agora exigindo apenas 20% do espaço de armazenamento usado em versões anteriores.

### Suporte ao IBM QRadar
Agora o ATA pode receber eventos da solução QRadar SIEM da IBM, além das soluções SIEM com suporte anterior.

## Problemas conhecidos
A seguir estão os problemas conhecidos existentes nesta versão.

### Falha ao reconhecer novo caminho em bancos de dados movidos manualmente

Em implantações nas quais o caminho do banco de dados é movido manualmente, a implantação do ATA não usa o novo caminho do banco de dados para a atualização. Isso pode causar os seguintes problemas:


- O ATA pode usar todo o espaço livre na unidade do sistema do Centro do ATA, sem excluir circularmente as atividades de rede antigas.


- Atualizar o ATA para a versão 1.6 pode causar falhas nas Verificações de Preparação de pré-atualização, conforme mostrado na imagem abaixo.
    ![Falha na verificação de preparação](media/ata_failed_readinesschecks.png)
    >[!Important]
Antes de atualizar o ATA para a versão 1.6, atualize a seguinte chave do Registro com o caminho do banco de dados correto:  `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath`

### Falha na migração ao atualizar do ATA 1.5
Ao atualizar para o ATA 1.6, o processo de atualização pode falhar com o seguinte código de erro:

![Erro ao atualizar para o ATA 1.6](http://i.imgur.com/QrLSApr.png) Se você ver esse erro, examine o log de implantação em: **C:\Users\<User>\AppData\Local\Temp** e procure pela seguinte exceção:

    System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> MongoDB.Driver.MongoWriteException: A write operation resulted in an error. E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : "<guid>" } ---> MongoDB.Driver.MongoBulkWriteException`1: A bulk write operation resulted in one or more errors.  E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : " <guid> " }

Você também pode ver este erro: System.ArgumentNullException: o valor não pode ser nulo.
    
Se você ver algum desses erros, execute a seguinte solução alternativa.

**Solução alternativa**: 

1.  Mova a pasta "data_old" para uma pasta temporária (geralmente localizada em %ProgramFiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin).
2.  Desinstale o Centro do ATA v1.5 e exclua todos os dados do banco de dados.
![Desinstalar o ATA 1.5](http://i.imgur.com/x4nJycx.png)
3.  Reinstale o Centro do ATA v1.5. Assegure-se de usar a mesma configuração da instalação anterior do ATA 1.5 (certificados, endereços IP, caminho do DB, etc.).
4.  Interrompa esses serviços na seguinte ordem:
    1.  Central do Microsoft Advanced Threat Analytics
    2.  MongoDB
5.  Substitua os arquivos de banco de dados do MongoDB pelos arquivos na pasta "data_old".
6.  Inicie esses serviços na seguinte ordem:
    1.  MongoDB
    2.  Central do Microsoft Advanced Threat Analytics
7.  Revise os logs para verificar se o produto está sendo executado sem erros.
8.  [Baixe](http://aka.ms/ataremoveduplicateprofiles "Baixe") a ferramenta "RemoveDuplicateProfiles.exe" e copie-a para o caminho de instalação principal (%ProgramFiles%\Microsoft Advanced Threat Analytics\Center)
9.  Em um prompt de comando elevado, execute "RemoveDuplicateProfiles.exe" e aguarde até que ela seja concluída com êxito.
10. Do diretório: …\Microsoft Advanced Threat Analytics\Center\MongoDB\bin: **Mongo ATA**, digite o seguinte comando:

    db.SuspiciousActivities.remove({ "_t" : "RemoteExecutionSuspiciousActivity", "DetailsRecords" : { "$elemMatch" : { "ReturnCode" : null } } }, { "_id" : 1 });

![Solução alternativa de atualização](http://i.imgur.com/Nj99X2f.png)

Isso deve retornar um WriteResult({ "nRemoved" : XX }) em que "XX" é o número de Atividades Suspeitas que foram excluídas. Se o número for maior que 0, saia do prompt de comando e continue o processo de atualização.


### O NET Framework 4.6.1 requer a reinicialização do servidor

Em alguns casos, a instalação do .Net Framework 4.6.1 pode exigir a reinicialização do servidor. Observe que clicar em OK na caixa de diálogo **Configuração da Central do Microsoft Advanced Threat Analytics** reiniciará automaticamente o servidor. Isso é particularmente importante ao instalar o Gateway Lightweight do ATA em um controlador de domínio, pois pode ser conveniente planejar uma janela de manutenção antes da instalação.
    ![Reinicialização do .Net Framework](media/ata-net-framework-restart.png)

### Histórico de atividades de rede não é mais migrado
Essa versão do ATA apresenta um mecanismo de detecção aprimorado, que fornece detecção mais precisa e reduz muitos cenários de falsos positivos, especialmente para Pass-the-Hash.
O mecanismo de detecção novo e aprimorado utiliza tecnologia de detecção embutida, permitindo detecção sem acessar o histórico de atividades de rede, para aumentar consideravelmente o desempenho do Centro do ATA. Isso também significa que é desnecessário migrar o histórico de atividades de rede durante o procedimento de atualização.
O procedimento de atualização do ATA exporta os dados, caso você os queira para investigação futura, para `<Center Installation Path>\Migration` como um arquivo JSON.

## Consulte também
[Confira o fórum do ATA!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)

[Atualizar o ATA para a versão 1.6 — guia de migração](ata-update-1.6-migration-guide.md)

<!--HONumber=May16_HO4-->


