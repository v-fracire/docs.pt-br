---
title: Confirme automaticamente o padrão
ms.date: 03/30/2017
ms.assetid: 668aec65-78d3-4636-9c7b-deed643a18f9
ms.openlocfilehash: a032c05743b64fe58b0b187328b5216080ba6e19
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552264"
---
# <a name="auto-confirm-pattern"></a>Confirme automaticamente o padrão
Esse exemplo consiste em três situações a execução que ilustra uma atividade personalizado de `AutoConfirmScope` . O primeiro exemplo mostra a execução bem-sucedida de uma sequência de quatro atividades compensáveis onde o segundo e terceiro é aninhado em lugar em `AutoConfirmScope`. O segundo exemplo mostra a mesma sequência com uma exceção que ocorre após a execução do quarto <xref:System.Activities.Statements.CompensableActivity>. O terceiro cenário mostra a mesma sequência com uma exceção que ocorre em `AutoConfirmScope` após segundo <xref:System.Activities.Statements.CompensableActivity> completa.  
  
 O exemplo demonstra o padrão de uma confirmação onde todas as atividades compensáveis filho são confirmadas em cima de conclusão com êxito de escopo. Esse padrão define o tempo de vida de todas as atividades compensáveis filhos, porque não podem mais ser compensados ou confirmado.  
  
 O escopo consiste em <xref:System.Activities.Statements.TryCatch> onde <xref:System.Activities.Statements.TryCatch.Try%2A> é <xref:System.Activities.Statements.CompensableActivity>interno. O corpo especificado pelo usuário de `AutoConfirmScope` é o corpo de <xref:System.Activities.Statements.CompensableActivity>interno. Quando esse <xref:System.Activities.Statements.CompensableActivity> interno for concluída, gerenciar <xref:System.Activities.Statements.CompensationToken> como um argumento para fora-. `AutoConfirmScope` usa <xref:System.Activities.Statements.TryCatch.Finally%2A> para verificar se o símbolo é gerado e tem então ele confirma <xref:System.Activities.Statements.CompensableActivity>interno. <xref:System.Activities.Statements.CompensableActivity> interno chama a compensação padrão para todas as atividades compensáveis que podem existir no corpo.  
  
 O primeiro cenário mostra a execução bem-sucedida de fluxo de trabalho e demonstrar-la que a segunda e terceira atividades compensáveis são confirmadas já quando o fluxo de trabalho e conclui as primeiras e em quarto confirmadas. Isso gerencia uma ordem de confirmação de três, de dois, de quatro, e um.  
  
 O segundo cenário mostra uma exceção depois que as quatro atividades compensáveis terminar. Porque as atividades compensáveis dois e três já estão confirmado eles não são afetadas mas uma e quatro é compensado. Isso gerencia confirma três, confirmar dois, compensa quatro e compensa um.  
  
 A situação final mostra a execução mal sucedido de `AutoConfirmScope`. Nesse cenário, uma exceção ocorre após a conclusão do segundo <xref:System.Activities.Statements.CompensableActivity>. Porque o terceiro e quartas atividades compensáveis não sua execução, não são afetadas. Porque o escopo não terminou com êxito, conforme <xref:System.Activities.Statements.CompensableActivity> não é confirmado. Isso gerenciar e ordem de compensação de dois em um.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de AutoConfirmSample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Compensation\AutoConfirm`