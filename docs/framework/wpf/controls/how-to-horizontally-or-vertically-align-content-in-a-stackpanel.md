---
title: 如何：在 StackPanel 中水平或垂直对齐内容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771028"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>如何：在 StackPanel 中水平或垂直对齐内容
此示例显示了如何调整<xref:System.Windows.Controls.StackPanel.Orientation%2A>内的内容<xref:System.Windows.Controls.StackPanel>元素，以及如何调整<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>的子内容。  
  
## <a name="example"></a>示例  
 下面的示例创建三个<xref:System.Windows.Controls.ListBox>中的元素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 每个<xref:System.Windows.Controls.ListBox>表示的可能值<xref:System.Windows.Controls.StackPanel.Orientation%2A>， <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>的属性<xref:System.Windows.Controls.StackPanel>。 当用户选择的值中的任何<xref:System.Windows.Controls.ListBox>元素中，关联的属性<xref:System.Windows.Controls.StackPanel>及其子<xref:System.Windows.Controls.Button>元素会更改。  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 下面的代码隐藏文件定义所做的更改与关联的事件<xref:System.Windows.Controls.ListBox>选择会有所变化。 <xref:System.Windows.Controls.StackPanel> 由标识<xref:System.Windows.FrameworkElement.Name%2A> `sp1`。  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [面板概述](panels-overview.md)
