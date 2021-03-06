---
title: Как определить, размещена ли страница в браузере
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: c4cb1065807d16c1d1f5a95c8ac9c9cbe5a0fdab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424694"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>Как определить, размещена ли страница в браузере
В этом примере показано, как определить, размещается ли <xref:System.Windows.Controls.Page> в браузере.  
  
## <a name="example"></a>Пример  
 <xref:System.Windows.Controls.Page> может быть независимым от узла и, следовательно, может быть загружена на несколько различных типов узлов, включая <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>или браузер. Это может произойти, если имеется сборка библиотеки, содержащая одну или несколько страниц, на которые ссылается несколько автономных и отображаемых (XBAP) хост-приложений.  
  
 В следующем примере показано, как использовать <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, чтобы определить, размещается ли <xref:System.Windows.Controls.Page> в браузере.  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
