---
title: Como obter um certificado (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519216"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Como obter um certificado (WCF)
Use qualquer um do Windows Communication Foundation (WCF) recursos do que usam certificados X.509, você apenas primeiro obter certificados.  
  
### <a name="to-obtain-an-x509-certificate"></a>Para obter um certificado x. 509  
  
1.  Escolha uma das seguintes opções:  
  
    -   Compre um certificado de uma autoridade de certificação, como VeriSign, Inc.  
  
    -   Configurar seu próprio serviço de certificado e ter uma autoridade de certificação assinar os certificados. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, o Windows 2000 Server Datacenter e o Windows 2000 Datacenter Server incluem serviços de certificados que dão suporte à infraestrutura de chave pública (PKI). No Windows Server 2008, use o [serviços de certificados do Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) função para gerenciar uma autoridade de certificação.  
  
    -   Configurar seu próprio serviço de certificado e não têm os certificados assinados.  
  
    > [!NOTE]
    >  Qualquer abordagem, o destinatário da solicitação SOAP que contém o certificado X.509 deve confiar no certificado de x. 509. Isso significa que o certificado X.509 ou um emissor na cadeia de certificados no repositório de certificados pessoas confiáveis e que não é o certificado X.509 no repositório de certificados não confiáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
