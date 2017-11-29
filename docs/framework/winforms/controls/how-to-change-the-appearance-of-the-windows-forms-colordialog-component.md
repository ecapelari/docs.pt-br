---
title: "Como alterar a aparência do componente ColorDialog dos Windows Forms"
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
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11edb1019b8fedde368d712ab27dd0954a2de50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="67ba1-102">Como alterar a aparência do componente ColorDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ba1-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="67ba1-103">Você pode configurar a aparência dos Windows Forms <xref:System.Windows.Forms.ColorDialog> componente com um número de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="67ba1-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="67ba1-104">A caixa de diálogo tem duas seções, uma que mostra as cores básicas e outra que permite que o usuário defina cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="67ba1-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="67ba1-105">A maioria das propriedades restringe quais cores o usuário pode selecionar da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="67ba1-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="67ba1-106">Se o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> está definida como `true`, o usuário tem permissão para definir cores personalizadas.</span><span class="sxs-lookup"><span data-stu-id="67ba1-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="67ba1-107">O <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> é de propriedade `true` se a caixa de diálogo é expandida para definir cores personalizadas; caso contrário, o usuário deve clicar em um botão "Definir cores personalizadas".</span><span class="sxs-lookup"><span data-stu-id="67ba1-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="67ba1-108">Quando o <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> está definida como `true`, a caixa de diálogo exibe todas as cores disponíveis no conjunto de cores básicas.</span><span class="sxs-lookup"><span data-stu-id="67ba1-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="67ba1-109">Se o <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> está definida como `true`, o usuário não é possível selecionar cores pontilhadas; somente cores sólidas estão disponíveis para seleção.</span><span class="sxs-lookup"><span data-stu-id="67ba1-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="67ba1-110">Se o <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> está definida como `true`, um botão de Ajuda será exibido na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="67ba1-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="67ba1-111">Quando o usuário clica no botão de Ajuda, o <xref:System.Windows.Forms.ColorDialog> do componente <xref:System.Windows.Forms.CommonDialog.HelpRequest> é gerado.</span><span class="sxs-lookup"><span data-stu-id="67ba1-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="67ba1-112">Para configurar a aparência da caixa de diálogo de cor</span><span class="sxs-lookup"><span data-stu-id="67ba1-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="67ba1-113">Definir o <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, e <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> propriedades para os valores desejados.</span><span class="sxs-lookup"><span data-stu-id="67ba1-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67ba1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67ba1-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="67ba1-115">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="67ba1-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="67ba1-116">Visão geral do componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="67ba1-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)