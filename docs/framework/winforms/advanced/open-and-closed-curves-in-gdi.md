---
title: Curvas abertas e fechadas no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527142"
---
# <a name="open-and-closed-curves-in-gdi"></a>Curvas abertas e fechadas no GDI+
A ilustração a seguir mostra duas curvas: uma aberta e outra fechada.  
  
 ![Curvas abertas e fechadas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Interface gerenciada para curvas  
 Curvas fechadas têm um interior e, portanto, podem ser preenchidas com um pincel. O <xref:System.Drawing.Graphics> classe em [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece os seguintes métodos para preencher formas fechadas e curvas: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, e <xref:System.Drawing.Graphics.FillRegion%2A>. Sempre que você chame um dos métodos a seguir, você deve passar um dos tipos específicos de pincel (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ou <xref:System.Drawing.Drawing2D.PathGradientBrush>) como um argumento.  
  
 O <xref:System.Drawing.Graphics.FillPie%2A> método é um complemento para o <xref:System.Drawing.Graphics.DrawArc%2A> método. Assim como o <xref:System.Drawing.Graphics.DrawArc%2A> método desenha uma parte da estrutura de tópicos de uma elipse o <xref:System.Drawing.Graphics.FillPie%2A> método preenche uma parte do interior de uma elipse. O exemplo a seguir desenha um arco e preenche a parte correspondente do interior da elipse:  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 A ilustração a seguir mostra o arco e a pizza preenchida.  
  
 ![Curvas abertas e fechadas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 O <xref:System.Drawing.Graphics.FillClosedCurve%2A> método é um complemento para o <xref:System.Drawing.Graphics.DrawClosedCurve%2A> método. Ambos os métodos fecham automaticamente a curva conectando o ponto final ao ponto inicial. O exemplo a seguir desenha uma curva que passa por (0, 0), (60, 20) e (40, 50). Em seguida, a curva é fechada automaticamente conectando (40, 50) ao ponto inicial (0, 0), e o interior é preenchido com uma cor sólida.  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 O <xref:System.Drawing.Graphics.FillPath%2A> método preenche os interiores das partes de um caminho separados. Se uma parte de um caminho não formam uma curva fechada ou forma, o <xref:System.Drawing.Graphics.FillPath%2A> método fecha automaticamente essa parte do caminho antes de preenchê-lo. O exemplo a seguir desenha e preenche um demarcador que consiste em um arco, uma spline cardinal, uma cadeia de caracteres e uma pizza:  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 A ilustração a seguir mostra o demarcador com e sem o preenchimento sólido. Observe que o texto na cadeia de caracteres é descrito, mas não preenchido, pelo <xref:System.Drawing.Graphics.DrawPath%2A> método. É o <xref:System.Drawing.Graphics.FillPath%2A> método que pinta os interiores dos caracteres na cadeia de caracteres.  
  
 ![Cadeia de caracteres em um demarcador](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Como Criar Objetos Gráficos para Desenho](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Construindo e desenhando demarcadores](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
