---
title: "+ (Concatenação de cadeia de caracteres) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 60661a592e23e230c32b1fd7093f5dfd8e6ed87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-string-concatenation-entity-sql"></a>+ (Concatenação de cadeia de caracteres) (Entity SQL)
Concatena duas cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida de tipos de dados de EDM.String. As duas expressões devem ser do mesmo tipo de dados, ou uma expressão deve poder ser convertido implicitamente para o tipo de dados de outra expressão.  
  
## <a name="result-types"></a>Tipos de resultado  
 O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos. Para obter mais informações sobre a promoção de tipo implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa operador + concatena duas cadeias de caracteres. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Tipos de modelo conceitual (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)