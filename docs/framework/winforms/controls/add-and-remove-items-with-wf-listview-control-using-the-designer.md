---
title: Como adicionar e remover itens com o componente ListView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1fe301f4c504d43fd83eb52e3b32f78af2ca78a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Como adicionar e remover itens com o componente ListView dos Windows Forms usando o designer
O processo de adicionar um item a um Windows Forms <xref:System.Windows.Forms.ListView> controle consiste principalmente especificando o item e atribuir propriedades a ele. A adição ou remoção de itens de lista pode ser feita a qualquer momento.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ListView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Para adicionar ou remover itens usando o designer  
  
1.  Selecione o <xref:System.Windows.Forms.ListView> controle.  
  
2.  No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.ListView.Items%2A> propriedade.  
  
     O **Editor de coleção de ListViewItem** é exibido.  
  
3.  Para adicionar um item, clique no botão **Adicionar**. Você pode definir propriedades do novo item, como o <xref:System.Windows.Forms.ListView.Text%2A> e <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriedades.  
  
4.  Para remover um item, selecione-o e clique no botão **Remover**.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Como Adicionar Colunas ao Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Como Exibir Subitens em Colunas com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Como Exibir Ícones do Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Como agrupar itens em um controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)