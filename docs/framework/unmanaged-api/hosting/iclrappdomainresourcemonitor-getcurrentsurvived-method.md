---
title: Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c179ba23be07e8ff77e1397ed753d4287b22440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435278"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAppDomainId`  
 [in] A ID do domínio do aplicativo solicitado.  
  
 `pAppDomainBytesSurvived`  
 [out] Um ponteiro para o número de bytes que sobreviveram após a última coleta de lixo que são mantidos por esse domínio de aplicativo. Depois de uma coleção completa, esse número é completas e precisas. Depois de uma coleção efêmera, esse número é potencialmente incompleto. Esse parâmetro pode ser `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Um ponteiro para o número total de bytes que sobreviveram a última da coleta de lixo. Depois de uma coleção completa, esse número representa o número de bytes que são mantidos em heaps gerenciados. Depois de uma coleção efêmera, esse número representa o número de bytes que são mantidos em tempo real em efêmeras gerações. Esse parâmetro pode ser `null`.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|COR_E_APPDOMAINUNLOADED|O domínio de aplicativo foi descarregado ou não existe.|  
  
## <a name="remarks"></a>Comentários  
 As estatísticas são atualizadas somente depois de um completo, bloqueio de coleta de lixo; ou seja, uma coleção que inclui todas as gerações e que interrompe o aplicativo durante a coleta ocorre. Por exemplo, o <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método executa um completo, bloqueio de coleta. Coleta de lixo simultânea ocorre em segundo plano e não bloqueia o aplicativo.  
  
 O `GetCurrentSurvived` método equivale a não gerenciado a gerenciado <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAppDomainResourceMonitor](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Monitoramento de recursos de domínio do aplicativo](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
