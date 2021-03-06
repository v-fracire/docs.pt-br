---
title: Função QualifierSet_Next (referência de API não gerenciada)
description: A função QualifierSet_Next recupera o próximo qualificador em uma enumeração.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 938044a4e932139eb8a4d0a5d2f998cbc6f193cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507687"
---
# <a name="qualifiersetnext-function"></a>Função QualifierSet_Next
Recupera o próximo qualificador em uma enumeração que começou com uma chamada para a função [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`   
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.

`lFlags`   
[in] Reservado. Esse parâmetro deve ser 0.

`pstrName`   
[out] O nome do qualificador. Se `null`, esse parâmetro é ignorado; caso contrário, `pstrName` não deve apontar para um válido `BSTR` ou ocorre um vazamento de memória. Se não nulo, a função sempre aloca um novo `BSTR` quando ele retorna `WBEM_S_NO_ERROR`.

`pVal`   
[out] Quando obtiver êxito, o valor do qualificador. Se a função falhar, o `VARIANT` apontado por `pVal` não será modificado. Se esse parâmetro for `null`, o parâmetro é ignorado.

`plFlavor`   
[out] Um ponteiro para um longo que recebe o tipo de qualificador. Se as informações de tipo não for desejadas, esse parâmetro pode ser `null`. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | O chamador não chamou [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para iniciar uma nova enumeração. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Não há mais qualificadores são deixadas na enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) método.

Você chama o `QualifierSet_Next` função repetidamente para enumerar todos os qualificadores até o retorno da função `WBEM_S_NO_MORE_DATA`. Para encerrar a enumeração no início, chame o [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) função.

A ordem dos qualificadores retornado durante a enumeração é indefinida.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
