---
title: Atribuição de variável do objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: f20a03c4d9a0e33203629ae066686f4c9f25c105
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656052"
---
# <a name="object-variable-assignment-visual-basic"></a>Atribuição de variável do objeto (Visual Basic)
Você pode usar uma instrução de atribuição normal para atribuir um objeto a uma variável de objeto. Você pode atribuir uma expressão de objeto ou o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, como o exemplo a seguir ilustra.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing` significa que não há nenhum objeto atualmente atribuído à variável.  
  
## <a name="initialization"></a>Inicialização  
 Quando seu código começa a execução, o objeto variáveis são inicializadas como `Nothing`. Aqueles cujas declarações incluem inicialização são reinicializados com os valores que você especificar quando as instruções de declaração são executadas.  
  
 Você pode incluir a inicialização na sua declaração usando o [novo](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave. As seguintes instruções de declaração declaram variáveis de objeto `testUri` e `ver` e atribuir a objetos específicos a elas. Cada uma usa um dos construtores sobrecarregados da classe apropriada para inicializar o objeto.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Dissociação  
 Definindo uma variável de objeto `Nothing` interrompe a associação da variável com qualquer objeto específico. Isso impede que você altere acidentalmente o objeto alterando a variável. Ele também permite que você teste se a variável de objeto aponta para um objeto válido, como mostra o exemplo a seguir.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Se o objeto que a variável se refere estiver em outro aplicativo, esse teste não pode determinar se esse aplicativo foi encerrada ou simplesmente invalidou o objeto.  
  
 Uma variável de objeto com um valor de `Nothing` também é chamado de um *referência nula*.  
  
## <a name="current-instance"></a>Instância atual  
 O *atual instância* de um objeto é aquele no qual o código está sendo executado. Como todo o código é executado dentro de um procedimento, a instância atual é aquele no qual o procedimento foi chamado.  
  
 O `Me` palavra-chave atua como uma variável de objeto referindo-se à instância atual. Se um procedimento não é [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md), ele pode usar o `Me` palavra-chave para obter um ponteiro para a instância atual. Procedimentos compartilhados não podem ser associados uma instância específica de uma classe.  
  
 Usando `Me` é particularmente útil para passar a instância atual para um procedimento em outro módulo. Por exemplo, suponha que você tem um número de documentos XML e deseja adicionar um texto padrão para todos eles. O exemplo a seguir define um procedimento para fazer isso.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Cada objeto de documento XML, em seguida, pode chamar o procedimento e passar sua instância atual como um argumento. O exemplo a seguir demonstra isso.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Como fazer uma variável de objeto não se referir a nenhuma instância](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
