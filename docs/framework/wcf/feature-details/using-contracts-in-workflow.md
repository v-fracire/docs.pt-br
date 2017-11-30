---
title: Utilizando contratos no fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c84483b2ca18d63f20e64a62bb757e244db9b24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-contracts-in-workflow"></a>Utilizando contratos no fluxo de trabalho
Ao implementar um serviço, você pode definir um número de contratos que descrevem o serviço e os dados que ele envia e recebe. Os dados são representados como contratos de dados e de mensagem; ambos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e serviços de fluxo de trabalho usam definições de contrato de mensagem e contrato de dados como parte de descrições de serviços. O próprio serviço expõe metadados (na forma de WSDL) para descrever as operações do serviço. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], serviço contratos e operação definir o serviço e as operações que ele suporta. No entanto, em um serviço de fluxo de trabalho, esses contratos são parte do processo de negócios em si; eles serão expostos nos metadados por um processo chamado inferência de contrato.  
  
## <a name="contract-inference"></a>Inferência de contrato  
 Quando um serviço de fluxo de trabalho é hospedado usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a definição de fluxo de trabalho é examinada e um contrato é gerado com base no conjunto de atividades encontradas no fluxo de trabalho do sistema de mensagens. Em particular as seguintes atividades e propriedades são usadas para gerar o contrato:  
  
 <xref:System.ServiceModel.Activities.Receive>Atividade  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A> --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply>Atividade  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A>-->  `System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Atividade  
  
 O resultado final de inferência de contrato é uma descrição do serviço usando as mesmas estruturas de dados como contratos de serviço e operação do WCF. Em seguida, essas informações são usadas para expor o WSDL para o serviço de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Atividades de mensagens](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Como: criar um serviço de fluxo de trabalho com atividades de mensagens](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Como criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)