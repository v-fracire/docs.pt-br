---
title: "Método INotifyConnection2::RegisterNotifySource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.RegisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 370f19d9fd1cbc268d43b9970b0cf27290796562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="54acb-102">Método INotifyConnection2::RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="54acb-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="54acb-103">Instala uma fonte de notificação especificado.</span><span class="sxs-lookup"><span data-stu-id="54acb-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54acb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54acb-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54acb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54acb-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="54acb-106">[in] Especifica o objeto a ser usado como a origem de notificação.</span><span class="sxs-lookup"><span data-stu-id="54acb-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="54acb-107">[out] Recebe o objeto a ser usado como o coletor de notificação.</span><span class="sxs-lookup"><span data-stu-id="54acb-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54acb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="54acb-108">Return Value</span></span>  
 <span data-ttu-id="54acb-109">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="54acb-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54acb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54acb-110">Requirements</span></span>  
 <span data-ttu-id="54acb-111">**Cabeçalho:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="54acb-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54acb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54acb-112">See Also</span></span>  
 [<span data-ttu-id="54acb-113">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="54acb-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="54acb-114">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="54acb-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="54acb-115">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="54acb-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="54acb-116">Método UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="54acb-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)