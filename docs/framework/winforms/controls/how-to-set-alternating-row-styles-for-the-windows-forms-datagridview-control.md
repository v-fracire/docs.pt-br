---
title: Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: 9d8c926935b879911d1503579c655a1ab6074681
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525290"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms
Dados tabulares geralmente são apresentados aos usuários em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente. Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.  
  
 Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para linhas alternadas. Isso permite usar as características de estilo como cor e fonte de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.  
  
 Há suporte para esta tarefa no Visual Studio.  Veja também [Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer](https://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Para definir estilos de linha alternada de forma programática  
  
-   Definir as propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> objetos retornados pela <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedades do <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Os estilos especificados usando o <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedades substituem os estilos especificados na coluna e <xref:System.Windows.Forms.DataGridView> de nível, mas são substituídos por estilos definidos no nível de linha e célula individual. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente. Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Formatação e estilos básicos no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Como definir estilos de fonte e cor no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
