---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509674"
---
# <a name="1030---startfaultworkitem"></a>1030 - StartFaultWorkItem
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1030|  
|Palavras-chave|WFRuntime|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um FaultWorkItem está sendo a execução.  
  
## <a name="message"></a>Mensagem  
 Iniciando a execução de um FaultWorkItem para a atividade '%1', DisplayName: '%2', InstanceId: '%3'.  A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|O nome do tipo de atividade de falha.|  
|FaultActivityDisplayName|xs:string|O nome para exibição de atividade de falha.|  
|FaultActivityInstanceId|xs:string|A identificação de instância de atividade de falha.|  
|ExceptionActivity|xs:string|O nome do tipo de atividade que apresentou a exceção.|  
|ExceptionActivityDisplayName|xs:string|O nome para exibição de atividade que apresentou a exceção.|  
|ExceptionActivityInstanceId|xs:string|A identificação de instância de atividade que apresentou a exceção.|  
|Exceção|xs:string|Os detalhes de exceção para a exceção|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
