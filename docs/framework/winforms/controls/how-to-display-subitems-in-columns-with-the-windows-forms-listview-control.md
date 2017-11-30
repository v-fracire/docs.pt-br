---
title: Como exibir subitens em colunas com o controle ListView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be1b055c8ea0e7a7c6466033735431a17ecc32f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Como exibir subitens em colunas com o controle ListView dos Windows Forms
Windows Forms <xref:System.Windows.Forms.ListView> controle pode exibir o texto adicional ou subitens, para cada item na exibição de detalhes. A primeira coluna exibe o texto do item, por exemplo, o número de um funcionário. A segunda, terceira e colunas seguintes exibem o primeiro, segundo e subitens associados seguintes.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Para adicionar subitens a um item de lista  
  
1.  Adicione as colunas necessárias. Como a primeira coluna exibirá o item <xref:System.Windows.Forms.ListView.Text%2A> propriedade, você precisa de mais uma coluna que há subitens. Para obter mais informações sobre como adicionar colunas, veja [Como adicionar colunas ao controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Chamar o <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> coleção retornada pelo método de <xref:System.Windows.Forms.ListViewItem.SubItems%2A> propriedade de um item. O exemplo de código a seguir define o nome do funcionário e o departamento para um item de lista.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Como Adicionar Colunas ao Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Como Exibir Ícones do Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)