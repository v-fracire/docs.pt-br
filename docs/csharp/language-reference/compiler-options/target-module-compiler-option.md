---
title: -target:module (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43393120"
---
# <a name="-targetmodule-c-compiler-options"></a>-target:module (opções do compilador C#)
Essa opção faz com que o compilador não gere um manifesto do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o arquivo de saída criado por meio da compilação com essa opção terá uma extensão .netmodule.  
  
 Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo Common Language Runtime do .NET Framework. No entanto, esse arquivo pode ser incorporado no manifesto do assembly de um assembly por meio de [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Se mais de um módulo for criado em uma única compilação, tipos [internos](../../../csharp/language-reference/keywords/internal.md) em um módulo estarão disponíveis para outros módulos na compilação. Quando o código em um módulo referenciar tipos `internal` em outro módulo, os dois módulos deverão ser incorporados em um manifesto do assembly, por meio de **-addmodule**.  
  
 Não há suporte para a criação de um módulo no ambiente de desenvolvimento do Visual Studio.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs`, criando `in.netmodule`:  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a>Consulte também  

- [-target (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
