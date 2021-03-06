---
title: Consultas LINQ to DataSet de depuração
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: fd10e6c715529ba937ba09732a254d311158b0f1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481045"
---
# <a name="debugging-linq-to-dataset-queries"></a>Consultas LINQ to DataSet de depuração
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] oferece suporte a depuração de código de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] . No entanto, há algumas diferenças entre depurar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] código e não-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] código gerenciado. A maioria dos recursos de depuração funcionam com [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instruções, incluindo a depuração, definindo pontos de interrupção e exibir os resultados que são mostrados nas janelas do depurador. No entanto, adiada execução em tem alguns efeitos colaterais que devem ser consideradas durante a depuração de consulta [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] de código e há algumas limitações ao usar Editar e continuar. Este tópico aborda aspectos de depuração que são exclusivos [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] comparado a não -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] código gerenciado.  
  
## <a name="viewing-results"></a>Resultados de exibição  
 Você pode exibir o resultado de uma [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrução usando DataTips, janela de inspeção e a caixa de diálogo QuickWatch. Usando uma janela de origem, você pode pausar o ponteiro em uma consulta na janela de origem e um DataTip aparecerá. Você pode copiar um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] variável e cole-a janela de observação ou a caixa de diálogo QuickWatch. No [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], uma consulta não é avaliada quando ela é criada ou declarada, mas somente quando a consulta é executada. Isso é chamado *execução adiada*. Portanto, a variável de consulta não tem um valor até que seja avaliada. Para obter mais informações, consulte [consultas no LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 O depurador deve avaliar uma consulta para exibir os resultados da consulta. Esta avaliação implícita ocorre quando você exibe um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] resultado da consulta no depurador e ele tem alguns efeitos que você deve considerar. Cada avaliação de consulta leva tempo. Expandir o nó de resultados leva tempo. Para algumas consultas, a avaliação repetida pode causar uma caneta visível de desempenho. Avaliar uma consulta também pode causar efeitos colaterais, que são alterações ao valor de dados ou de estado do seu programa. Nem todas as consultas têm efeitos colaterais. Para determinar se uma consulta pode ser avaliada com segurança sem efeitos colaterais, você deve compreender o código que implementa a consulta. Para obter mais informações, consulte [efeitos colaterais e expressões](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Editar e continuar  
 Editar e continuar não dá suporte a alterações para [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas. Se você adicionar, remover ou alterar um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrução durante uma sessão de depuração, aparece uma caixa de diálogo que informa a alteração não é suportada por editar e continuar. Nesse ponto, você pode desfazer as alterações ou parar a sessão de depuração e reiniciar uma nova sessão com o código editado.  
  
 Além disso, editar e continuar não dá suporte a alteração do tipo ou o valor de uma variável que é usado em um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrução. Além disso, você pode desfazer as alterações ou parar e reiniciar a sessão de depuração.  
  
 No Visual c# no Visual Studio, você não pode usar Editar e continuar em qualquer código em um método que contém um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta.  
  
 No Visual Basic no Visual Studio, você pode usar Editar e continuar em não -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] código, mesmo em um método que contém um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta. Você pode adicionar ou remover o código antes de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrução, mesmo se as alterações afetam o número de linha a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta. Sua experiência de depuração para do Visual Basic não -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] código permanece o mesmo como era antes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] foi introduzido. Você não pode alterar, adicionar ou remover um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] de consulta, no entanto, a menos que você pare a depuração para aplicar as alterações.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](/visualstudio/debugger/debugging-managed-code)  
 [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
