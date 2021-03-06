---
title: Como usar argumentos nomeados e opcionais na programação do Office (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 3fce8a30e9ed663f06fa04c462fc1e1fd249d27a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321867"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Como usar argumentos nomeados e opcionais na programação do Office (Guia de Programação em C#)
Os argumentos nomeados e opcionais, introduzidos em [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], aprimoram a conveniência, a flexibilidade e a legibilidade na programação em C#. Além disso, esses recursos facilitam bastante o acesso a interfaces COM, como as APIs de Automação do Microsoft Office.  
  
 No exemplo a seguir, o método [ConvertToTable](https://msdn.microsoft.com/library/bb216993.aspx) tem 16 parâmetros que representam as características de uma tabela, como o número de colunas e linhas, formatação, bordas, fontes e cores. Todos os 16 parâmetros são opcionais, pois na maioria das vezes você não quiser especificar valores específicos para todos eles. No entanto, sem argumentos nomeados e opcionais, um valor ou um valor de espaço reservado precisa ser fornecido para cada parâmetro. Com argumentos nomeados e opcionais, você especifica valores apenas para os parâmetros que são necessários para seu projeto.  
  
 Você deve ter o Microsoft Office Word instalado em seu computador para concluir esses procedimentos.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Para criar um novo aplicativo de console  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel **Templates Categories (Categorias de Modelos)**, expanda **Visual C#** e clique em **Windows**.  
  
4.  Observe a parte superior do painel **Modelos** para se certificar de que **.NET Framework 4** é exibido na caixa **Estrutura de Destino**.  
  
5.  No painel **Modelos**, clique em **Aplicativo de Console**.  
  
6.  Digite um nome para o projeto no campo **Nome**.  
  
7.  Clique em **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
### <a name="to-add-a-reference"></a>Para adicionar uma referência  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**. A caixa de diálogo **Adicionar Referência** é exibida.  
  
2.  Na página **.NET**, selecione **Microsoft.Office.Interop.Word** na lista **Nome do Componente**.  
  
3.  Clique em **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Para adicionar as diretivas using necessárias  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo **Program.cs** e, em seguida, clique em **Exibir Código**.  
  
2.  Adicione as seguintes diretivas `using` na parte superior do arquivo de código.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Para exibir texto em um documento do Word  
  
1.  Na classe `Program` em Program.cs, adicione o seguinte método para criar um aplicativo do Word e um documento do Word. O método [Add](https://msdn.microsoft.com/library/microsoft.office.interop.word.documents.add.aspx) tem quatro parâmetros opcionais. Este exemplo usa os valores padrão. Portanto, nenhum argumento é necessário na instrução de chamada.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Adicione o código a seguir ao final do método para definir onde exibir o texto no documento e o texto a ser exibido.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Para executar o aplicativo  
  
1.  Adicione a seguinte instrução a Main.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Pressione CTRL+F5 para executar o projeto. É exibido um documento do Word contendo o texto especificado.  
  
### <a name="to-change-the-text-to-a-table"></a>Para alterar o texto para uma tabela  
  
1.  Use o método `ConvertToTable` para colocar o texto em uma tabela. O método tem 16 parâmetros opcionais. O IntelliSense coloca os parâmetros opcionais entre colchetes, como mostrado na ilustração a seguir.  
  
     ![Lista de parâmetros do método ConvertToTable.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
Parâmetros de ConvertToTable  
  
     Os argumentos nomeados e opcionais permitem que você especifique valores apenas para os parâmetros que deseja alterar. Adicione o seguinte código ao final do método `DisplayInWord` para criar uma tabela simples. O argumento especifica que as vírgulas na cadeia de caracteres de texto em `range` separam as células da tabela.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     Em versões anteriores do C#, a chamada para `ConvertToTable` requer um argumento de referência para cada parâmetro, conforme mostrado no código a seguir.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Pressione CTRL+F5 para executar o projeto.  
  
### <a name="to-experiment-with-other-parameters"></a>Para fazer experiências com outros parâmetros  
  
1.  Para alterar a tabela para que ela tenha uma coluna e três linhas, substitua a última linha em `DisplayInWord` pela instrução a seguir e digite CTRL+F5.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Para especificar um formato predefinido para a tabela, substitua a última linha em `DisplayInWord` pela a instrução a seguir e digite CTRL+F5. O formato pode ser qualquer uma das constantes [WdTableFormat](https://msdn.microsoft.com/library/microsoft.office.interop.word.wdtableformat.aspx).  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir inclui o exemplo completo.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
