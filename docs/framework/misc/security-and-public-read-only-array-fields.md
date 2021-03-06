---
title: Segurança e campos de matriz públicos somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0110bb42775d8a5df9ca268b35db3abaffec84f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392623"
---
# <a name="security-and-public-read-only-array-fields"></a>Segurança e campos de matriz públicos somente leitura
Nunca use campos de matriz públicos somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos, como campos de matriz públicos somente leitura podem ser modificados.  
  
## <a name="remarks"></a>Comentários  
 Algumas classes do .NET framework incluem campos públicos somente leitura que contêm parâmetros de limite específico da plataforma.  Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho do arquivo.  Muitos campos semelhantes estão presentes no .NET Framework.  
  
 Os valores dos campos públicos somente leitura, como <xref:System.IO.Path.InvalidPathChars> pode ser modificado por seu código ou o código que compartilha o domínio de aplicativo do seu código.  Você não deve usar campos de matriz públicos somente leitura como este para definir o comportamento de limite de seus aplicativos.  Se você fizer isso, código mal-intencionado pode alterar as definições de limite e usem o seu código de maneiras inesperadas.  
  
 Na versão 2.0 e posterior do .NET Framework, você deve usar os métodos que retornam uma nova matriz em vez de usar campos de matriz públicos.  Por exemplo, em vez de usar o <xref:System.IO.Path.InvalidPathChars> campo, você deve usar o <xref:System.IO.Path.GetInvalidPathChars%2A> método.  
  
 Observe que os tipos do .NET Framework não usam os campos públicos para definir tipos de limite internamente.  Em vez disso, o .NET Framework usa campos particulares separados.  Alterando os valores desses campos públicos não altera o comportamento de tipos do .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
