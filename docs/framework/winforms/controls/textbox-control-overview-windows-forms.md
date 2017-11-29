---
title: "Visão geral do controle TextBox (Windows Forms)"
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
f1_keywords: TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8c75392f12b87c7495b1fcdf5419f2463067161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="82492-102">Visão geral do controle TextBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="82492-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="82492-103">Caixas de texto dos Windows Forms são usadas para obter entradas do usuário ou para exibir texto.</span><span class="sxs-lookup"><span data-stu-id="82492-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="82492-104">O controle <xref:System.Windows.Forms.TextBox> geralmente é usado para texto editável, embora também possa ser tornado somente leitura.</span><span class="sxs-lookup"><span data-stu-id="82492-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="82492-105">Caixas de texto podem exibir várias linhas, quebrar o texto para o tamanho do controle e adicionar formatação básica.</span><span class="sxs-lookup"><span data-stu-id="82492-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="82492-106">O <xref:System.Windows.Forms.TextBox> controle fornece um estilo de formato único para o texto exibido ou inseridos no controle.</span><span class="sxs-lookup"><span data-stu-id="82492-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="82492-107">Para exibir vários tipos de texto formatado, use o <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="82492-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="82492-108">Para obter mais informações, consulte [Visão geral do controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="82492-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="82492-109">Trabalhando com o controle TextBox</span><span class="sxs-lookup"><span data-stu-id="82492-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="82492-110">O texto exibido pelo controle está contido no <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="82492-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="82492-111">Por padrão, você pode inserir até 2048 caracteres em uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="82492-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="82492-112">Se você definir o <xref:System.Windows.Forms.TextBox.Multiline%2A> propriedade `true`, você pode inserir até 32 KB de texto.</span><span class="sxs-lookup"><span data-stu-id="82492-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="82492-113">O <xref:System.Windows.Forms.TextBox.Text%2A> propriedade pode ser definida em tempo de design com a janela de propriedades em tempo de execução no código, ou pela entrada do usuário em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="82492-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="82492-114">O conteúdo atual de uma caixa de texto pode ser recuperado em tempo de execução lendo o <xref:System.Windows.Forms.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="82492-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="82492-115">O exemplo de código a seguir define o texto no controle no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="82492-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="82492-116">O `InitializeMyControl` procedimento não será executado automaticamente; ele deve ser chamado.</span><span class="sxs-lookup"><span data-stu-id="82492-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="82492-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82492-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="82492-118">Como controlar o ponto de inserção em um controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82492-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="82492-119">Como criar uma caixa de texto de senha com o controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82492-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="82492-120">Como criar uma caixa de texto somente leitura</span><span class="sxs-lookup"><span data-stu-id="82492-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="82492-121">Como inserir aspas em uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="82492-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="82492-122">Como selecionar texto no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82492-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="82492-123">Como exibir várias linhas no controle TextBox dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82492-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="82492-124">Controle TextBox</span><span class="sxs-lookup"><span data-stu-id="82492-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)