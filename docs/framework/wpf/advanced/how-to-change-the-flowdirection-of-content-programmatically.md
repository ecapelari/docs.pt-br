---
title: "Como alterar o FlowDirection de conteúdo de forma programática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a><span data-ttu-id="b9dea-102">Como alterar o FlowDirection de conteúdo de forma programática</span><span class="sxs-lookup"><span data-stu-id="b9dea-102">How to: Change the FlowDirection of Content Programmatically</span></span>
<span data-ttu-id="b9dea-103">Este exemplo mostra como alterar programaticamente o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade de um <xref:System.Windows.Controls.FlowDocumentReader>.</span><span class="sxs-lookup"><span data-stu-id="b9dea-103">This example shows how to programmatically change the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property of a <xref:System.Windows.Controls.FlowDocumentReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9dea-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9dea-104">Example</span></span>  
 <span data-ttu-id="b9dea-105">Dois <xref:System.Windows.Controls.Button> elementos são criados, cada um representando um dos possíveis valores de <xref:System.Windows.FlowDirection>.</span><span class="sxs-lookup"><span data-stu-id="b9dea-105">Two <xref:System.Windows.Controls.Button> elements are created, each representing one of the possible values of <xref:System.Windows.FlowDirection>.</span></span> <span data-ttu-id="b9dea-106">Quando um botão é clicado, o valor da propriedade associada é aplicado ao conteúdo de um <xref:System.Windows.Controls.FlowDocumentReader> chamado `tf1`.</span><span class="sxs-lookup"><span data-stu-id="b9dea-106">When a button is clicked, the associated property value is applied to the contents of a <xref:System.Windows.Controls.FlowDocumentReader> named `tf1`.</span></span>  <span data-ttu-id="b9dea-107">O valor da propriedade também é gravado em um <xref:System.Windows.Controls.TextBlock> chamado `txt1`.</span><span class="sxs-lookup"><span data-stu-id="b9dea-107">The property value is also written to a <xref:System.Windows.Controls.TextBlock> named `txt1`.</span></span>  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a><span data-ttu-id="b9dea-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9dea-108">Example</span></span>  
 <span data-ttu-id="b9dea-109">Os eventos associados com os cliques de botão definidos acima são tratados em um [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="b9dea-109">The events associated with the button clicks defined above are handled in a [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] code-behind file.</span></span>  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]