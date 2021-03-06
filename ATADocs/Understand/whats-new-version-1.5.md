---
# required metadata

title: Novidades na versão 1.5 do ATA | Advanced Threat Analytics
description: Lista as novidades na versão 1.5 do ATA e seus problemas conhecidos
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

# Novidades na versão 1.5 do ATA
Essas notas de versão fornecem informações sobre problemas conhecidos nesta versão da Advanced Threat Analytics.

## Quais são as novidades na atualização 1.5 do ATA?
A atualização 1.5 do ATA fornece melhorias nas seguintes áreas:

-   Tempo de detecção mais rápido

-   Algoritmo de detecção automática avançado para os dispositivos NAT (conversão de endereços de rede)

-   Processo de resolução de nomes avançado para dispositivos não associados a um domínio

-   Suporte para a migração de dados durante as atualizações de produto

-   Melhor capacidade de resposta da interface do usuário para atividades suspeitas com milhares de entidades envolvidas

-   Resolução automática de alertas de monitoramento aprimorada

-   Contadores de desempenho adicionais para monitoramento e solução de problemas avançados

## Problemas conhecidos
A seguir estão os problemas conhecidos existentes nesta versão.

### Falha na instalação do novo Gateway do ATA
Depois de atualizar sua implantação do ATA para a versão 1.5, você obterá o seguinte erro ao instalar um novo Gateway do ATA: o gateway do Microsoft Advanced Threat Analytics não está instalado

![Erro de GW do ATA](media/ata-install-error.png)

<b>Solução alternativa:</b> envie um email para <ataeval@microsoft.com> para solicitar etapas de solução alternativa.
### Implantação
A pasta especificada para o "Caminho de dados do banco de dados" e "Caminho de diário do banco de dados" deve estar vazia (sem arquivos ou subpastas).
Se não estiver vazia, a implantação não poderá avançar.

### Instalação do arquivo Zip
Ao instalar o Gateway de ATA, certifique-se de extrair os arquivos do arquivo zip para um diretório local e instalá-lo de lá. Não instale o Gateway de ATA diretamente de dentro do arquivo zip ou a instalação falhará.

### Configuração
Depois de definir a configuração de um Gateway do ATA, ele é iniciado pela primeira vez, o rótulo "Não sincronizado" é exibido até o serviço ter sido totalmente iniciado, o que pode levar até 10 minutos na primeira vez que o serviço é iniciado.

### Software de captura de rede
No Gateway de ATA, o único software de captura de rede suportado que você pode instalar é o [Microsoft Network Monitor 3.4](http://www.microsoft.com/en-us/download/details.aspx?id=4865). Não instale o Microsoft Message Analyzer ou qualquer outro software de captura de rede. A instalação de outro software fará com que o Gateway de ATA pare de funcionar corretamente.

### Base de dados de conhecimento sobre host de virtualização
Não instale a Base de dados de conhecimento 3047154 em um host de virtualização. Isso pode fazer com que o espelhamento de porta pare de funcionar corretamente.

## Consulte também

[Atualizar o ATA para a versão 1.5 — guia de migração](ata-update-1.5-migration-guide.md)

[Atualizar o ATA para a versão 1.6 — guia de migração](ata-update-1.6-migration-guide.md)

[Confira o fórum do ATA!](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO3-->


