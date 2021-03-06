---
# required metadata

title: Novidades na versão 1.4 do ATA | Advanced Threat Analytics
description: Lista as novidades na versão 1.4 do ATA e seus problemas conhecidos
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: cbea47f9-34c1-42b6-ae9e-6a472b49e1a5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades na versão 1.4 do ATA
Essas notas de versão fornecem informações sobre problemas conhecidos na versão 1.4 da Advanced Threat Analytics.

## O que há de novo nesta versão?

-   Suporte do Windows Event Forwarding (WEF) para enviar eventos diretamente dos controladores de domínio para o Gateway de ATA.

-   Aprimoramentos na detecção de “Pass-The-Hash” em recursos corporativos, combinando DPI (inspeção profunda de pacote) e logs de eventos do Windows.

-   Aprimoramentos para o suporte de dispositivos de domínio não unidos e dispositivos não Windows para detecção e visibilidade.

-   Aprimoramentos de desempenho para oferecer suporte a mais tráfego por Gateway de ATA.

-   Aprimoramentos de desempenho para oferecer suporte a mais Gateways de ATA por Centro de ATA.

-   Um novo processo de resolução de nome automático foi adicionado, o que corresponde a nomes de computador e de endereços IP – este recurso exclusivo economizará tempo precioso no processo de investigação e fornecerá provas sólidas de analistas de segurança

-   Maior capacidade de coletar informações de usuários para ajustar automaticamente o processo de detecção.

-   Detecção automática de dispositivos NAT.

-   Failover automático quando os controladores de domínio não estão acessíveis.

-   O monitoramento de integridade do sistema e as notificações agora fornecem o estado de integridade geral da implantação, assim como os problemas específicos relacionados à configuração e conectividade.

-   Visibilidade de sites e os locais onde as entidades operam.

-   Vários domínios.

-   Suporte a domínios de rótulo único (SLD).

-   Suporte para modificar o endereço IP e o certificado dos Gateways de ATA e o Centro de ATA.

-   Telemetria para ajudar a melhorar a experiência do cliente.

## Problemas conhecidos
A seguir estão os problemas conhecidos existentes nesta versão.

### Software de captura de rede
No Gateway de ATA, o único software de captura de rede suportado que você pode instalar é o [Microsoft Network Monitor 3.4](http://www.microsoft.com/en-us/download/details.aspx?id=4865). Não instale o Microsoft Message Analyzer ou qualquer outro software de captura de rede. A instalação de outro software fará com que o Gateway de ATA pare de funcionar corretamente.

### Instalação do arquivo Zip
Ao instalar o Gateway de ATA, certifique-se de extrair os arquivos do arquivo zip para um diretório local e instalá-lo de lá. Não instale o Gateway de ATA diretamente de dentro do arquivo zip ou a instalação falhará.

### Desinstalando versões anteriores de ATA
Se você instalou uma versão anterior do ATA, da Visualização Pública ou da Visualização Privada, você deve desinstalar o Centro de ATA e os Gateways de ATA antes de instalar esta versão do ATA.

Você também deve excluir os arquivos de banco de dados e arquivos de log. Os bancos de dados de versões anteriores do ATA não são compatíveis com a versão GA do ATA.

Ao tentar desinstalar o Centro de ATA ou o Gateway de ATA, se a instalação do ATA abrir em vez da desinstalação, você precisará adicionar a seguinte chave do registro e, em seguida, desinstalar o ATA novamente.

**Centro de ATA**

-   HKLM\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center

-   Adicione um novo valor de cadeia de caracteres chamado `InstallationPath` com um valor de `C:\Program Files\Microsoft Advanced Threat Analytics\Center` . Esta é a pasta de instalação padrão. Se você alterou a pasta de instalação, insira o caminho onde o ATA está instalado.

    ![Editor do registro para o caminho de instalação do Centro de ATA](media/ATA-uninstall-center-bug.jpg)

**Gateway de ATA**

-   HKLM\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Gateway

-   Adicione um novo valor de cadeia de caracteres chamado `InstallationPath` com um valor de `C:\Program Files\Microsoft Advanced Threat Analytics\Gateway`. Esta é a pasta de instalação padrão.  Se você alterou a pasta de instalação, insira o caminho onde o ATA está instalado.

    ![Editor do registro para o caminho de instalação do Gateway de ATA](media/ATA-GW-uninstall-bug.jpg)

Após a desinstalação, exclua a pasta de instalação no Centro de ATA e no Gateway de ATA.  Se você instalou o banco de dados em uma pasta separada, exclua a pasta do banco de dados no Centro de ATA.

### Alerta de integridade – Gateway de ATA desconectado
Se você tiver mais de um Gateway de ATA e tiver desconectado os alertas de Gateway de ATA, a resolução automática funcionará em apenas um deles, deixando os restantes com status em aberto. Você deve confirmar manualmente que o Gateway de ATA está ativo e que o serviço está em execução e resolver manualmente o alerta.

### Base de dados de conhecimento sobre host de virtualização
Não instale a Base de dados de conhecimento 3047154 em um host de virtualização. Isso pode fazer com que o espelhamento de porta pare de funcionar corretamente.

## Consulte também

[Atualizar o ATA para a versão 1.6 — guia de migração](ata-update-1.6-migration-guide.md)

[Confira o fórum do ATA!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)

<!--HONumber=May16_HO3-->


