---
title: "Função DeleteMethod (referência de API não gerenciada)"
description: "A função DeleteMethod exclui o método especificado de uma definição de classe do CIM."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: DeleteMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: DeleteMethod
helpviewer_keywords: DeleteMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d931cb76eeaf19ddeb80bdde412fabeea4b70203
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="deletemethod-function"></a><span data-ttu-id="f76b1-103">Função DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="f76b1-103">DeleteMethod function</span></span>
<span data-ttu-id="f76b1-104">Exclui o método especificado de uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="f76b1-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f76b1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f76b1-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f76b1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f76b1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f76b1-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="f76b1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f76b1-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="f76b1-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="f76b1-109">[in] O nome do método para remover da tabela de classe.</span><span class="sxs-lookup"><span data-stu-id="f76b1-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="f76b1-110">`wszName`deve ser um ponteiro para um válida `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f76b1-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f76b1-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f76b1-111">Return value</span></span>

<span data-ttu-id="f76b1-112">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="f76b1-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f76b1-113">Constante</span><span class="sxs-lookup"><span data-stu-id="f76b1-113">Constant</span></span>  |<span data-ttu-id="f76b1-114">Valor</span><span class="sxs-lookup"><span data-stu-id="f76b1-114">Value</span></span>  |<span data-ttu-id="f76b1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f76b1-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f76b1-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f76b1-116">0x80041002</span></span> | <span data-ttu-id="f76b1-117">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="f76b1-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f76b1-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f76b1-118">0x80041006</span></span> | <span data-ttu-id="f76b1-119">Não há memória suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="f76b1-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f76b1-120">0</span><span class="sxs-lookup"><span data-stu-id="f76b1-120">0</span></span> | <span data-ttu-id="f76b1-121">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f76b1-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f76b1-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="f76b1-122">Remarks</span></span>

<span data-ttu-id="f76b1-123">Essa função encapsula uma chamada para o [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="f76b1-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f76b1-124">Não há suporte para a exclusão do método para [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponteiros que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="f76b1-124">Method deletion is not supported for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="f76b1-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f76b1-125">Requirements</span></span>  
 <span data-ttu-id="f76b1-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f76b1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f76b1-127">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f76b1-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f76b1-128">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f76b1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76b1-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76b1-129">See also</span></span>  
[<span data-ttu-id="f76b1-130">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="f76b1-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)