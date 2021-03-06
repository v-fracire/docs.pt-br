---
title: '&lt;transporte&gt; de &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8c2a0de73db2ec4a1c2150fc7e62b7a3a9f086bc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515046"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;transporte&gt; de &lt;netTcpBinding&gt;
Define o tipo de requisitos de segurança de nível de mensagem para um ponto de extremidade configurado com o [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<associações >  
\<netTcpBinding>  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientCredentialType|Opcional. Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança de transporte.<br /><br /> -O valor padrão é `Windows`.<br />-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Opcional. Define a segurança no nível de transporte TCP. Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos. A criptografia fornece privacidade de nível de dados durante o transporte.<br /><br /> O valor padrão é `EncryptAndSign`.|  
|sslProtocols|Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte. O padrão é Tls&#124;Tls11&#124;Tls12.|  
|policyenforcement definido como|Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.<br /><br /> 1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).<br />2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.<br />3.  Sempre – a política sempre é aplicada. Os clientes que não dão suporte a proteção estendida falharão ao autenticar.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|O cliente é anônimo. Isso requer um certificado para o serviço.|  
|Windows|Especifica a autenticação do Windows do cliente usando a negociação do SP (negociação de Kerberos).|  
|Certificado|O cliente é autenticado usando um certificado. Isso usa a negociação SSL e requer um certificado para o serviço.|  
  
## <a name="protectionlevel-attribute"></a>Atributo de protectionLevel  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|Sem proteção.|  
|logon|As mensagens são assinadas.|  
|EncryptAndSign|-As mensagens são criptografadas e assinadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Especifica os recursos de segurança de [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e para autenticação mútua. Se este modo de segurança é selecionado em uma associação, a pilha de canais é configurada usando um transporte seguro e as mensagens SOAP são protegidas usando a segurança de transporte, como Windows (negociação) ou SSL sobre TCP.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
