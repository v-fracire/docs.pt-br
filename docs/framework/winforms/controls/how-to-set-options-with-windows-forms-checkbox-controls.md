---
title: "Como definir opções com controles CheckBox dos Windows Forms"
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
- cpp
f1_keywords: checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7d3ddb090488f6503c0765f6054308c28d4ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Como definir opções com controles CheckBox dos Windows Forms
Um Windows Forms <xref:System.Windows.Forms.CheckBox> controle é usado para fornecer aos usuários True/False ou Yes/No opções. O controle exibe uma marca de seleção quando ele é selecionado.  
  
### <a name="to-set-options-with-checkbox-controls"></a>Para definir opções com controles CheckBox  
  
1.  Examinar o valor da <xref:System.Windows.Forms.CheckBox.Checked%2A> propriedade para determinar o estado e usar esse valor para definir uma opção.  
  
     No exemplo de código a seguir, quando o <xref:System.Windows.Forms.CheckBox> do controle <xref:System.Windows.Forms.CheckBox.CheckedChanged> é gerado, o formulário <xref:System.Windows.Forms.Control.AllowDrop%2A> está definida como `false` se a caixa de seleção estiver marcada. Isso é útil para situações em que você deseja restringir a interação do usuário.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.CheckBox>  
 [Visão geral do controle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Como responder a cliques em CheckBox dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [Controle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)