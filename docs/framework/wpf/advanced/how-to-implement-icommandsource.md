---
title: Como implementar ICommandSource
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
helpviewer_keywords: ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdff5ebeb51daff4e8848e9a7c8282c2eee6f208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="11532-102">Como implementar ICommandSource</span><span class="sxs-lookup"><span data-stu-id="11532-102">How to: Implement ICommandSource</span></span>
<span data-ttu-id="11532-103">Este exemplo mostra como criar uma fonte de comandos, implementando <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="11532-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span>  <span data-ttu-id="11532-104">Uma fonte de comando é um objeto que sabe como invocar um comando.</span><span class="sxs-lookup"><span data-stu-id="11532-104">A command source is an object that knows how to invoke a command.</span></span>  <span data-ttu-id="11532-105">O <xref:System.Windows.Input.ICommandSource> interface expõe três membros: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, e <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="11532-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, and <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>.</span></span>  <span data-ttu-id="11532-106"><xref:System.Windows.Input.ICommandSource.Command%2A>é o comando que será chamado.</span><span class="sxs-lookup"><span data-stu-id="11532-106"><xref:System.Windows.Input.ICommandSource.Command%2A> is the command which will be invoked.</span></span> <span data-ttu-id="11532-107">O <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> é um tipo de dados definido pelo usuário que é passado da fonte de comandos para o método que trata o comando.</span><span class="sxs-lookup"><span data-stu-id="11532-107">The <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> is a user-defined data type which is passed from the command source to the method which handles the command.</span></span> <span data-ttu-id="11532-108">O <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> é o objeto que o comando está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="11532-108">The <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> is the object that the command is being executed on.</span></span>  
  
 <span data-ttu-id="11532-109">Neste exemplo, uma classe é criada que herda do <xref:System.Windows.Controls.Slider> controle e implementa <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="11532-109">In this example, a class is created which subclasses the <xref:System.Windows.Controls.Slider> control and implements <xref:System.Windows.Input.ICommandSource>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11532-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11532-110">Example</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="11532-111">Fornece um número de classes que implementam <xref:System.Windows.Input.ICommandSource>, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, e <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="11532-111"> provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Controls.ListBoxItem>.</span></span>  <span data-ttu-id="11532-112">Uma fonte de comandos define como se invoca um comando.</span><span class="sxs-lookup"><span data-stu-id="11532-112">A command source defines how it invokes a command.</span></span>   <span data-ttu-id="11532-113"><xref:System.Windows.Controls.Button>e <xref:System.Windows.Controls.MenuItem> invocar um comando quando eles são clicados.</span><span class="sxs-lookup"><span data-stu-id="11532-113"><xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.MenuItem> invoke a command when they are clicked.</span></span>  <span data-ttu-id="11532-114">Um <xref:System.Windows.Controls.ListBoxItem> invoca um comando quando é clicada duas vezes.</span><span class="sxs-lookup"><span data-stu-id="11532-114">A <xref:System.Windows.Controls.ListBoxItem> invokes a command when it is double clicked.</span></span> <span data-ttu-id="11532-115">Essas classes tornam-se apenas um comando de origem quando seus <xref:System.Windows.Input.ICommandSource.Command%2A> está definida.</span><span class="sxs-lookup"><span data-stu-id="11532-115">These classes only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>  
  
 <span data-ttu-id="11532-116">Para esse exemplo nós iremos invocar o comando quando o controle deslizante for movido, ou mais precisamente, quando o <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade é alterada.</span><span class="sxs-lookup"><span data-stu-id="11532-116">For this example we will invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>  
  
 <span data-ttu-id="11532-117">A seguir está a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="11532-117">The following is the class definition.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 <span data-ttu-id="11532-118">A próxima etapa é implementar o <xref:System.Windows.Input.ICommandSource> membros.</span><span class="sxs-lookup"><span data-stu-id="11532-118">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span>  <span data-ttu-id="11532-119">Neste exemplo, as propriedades são implementadas como <xref:System.Windows.DependencyProperty> objetos.</span><span class="sxs-lookup"><span data-stu-id="11532-119">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span>  <span data-ttu-id="11532-120">Isso permite que as propriedades usem associação de dados.</span><span class="sxs-lookup"><span data-stu-id="11532-120">This enables the properties to use data binding.</span></span>  <span data-ttu-id="11532-121">Para obter mais informações sobre o <xref:System.Windows.DependencyProperty> de classe, consulte o [visão geral de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11532-121">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  <span data-ttu-id="11532-122">Para obter mais informações sobre associação de dados, consulte [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="11532-122">For more information about data binding, see the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="11532-123">Somente o <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade é mostrada aqui.</span><span class="sxs-lookup"><span data-stu-id="11532-123">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 <span data-ttu-id="11532-124">A seguir está o <xref:System.Windows.DependencyProperty> alterar o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="11532-124">The following is the <xref:System.Windows.DependencyProperty> change callback.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 <span data-ttu-id="11532-125">A próxima etapa é adicionar e remover o comando que está associado à fonte de comando.</span><span class="sxs-lookup"><span data-stu-id="11532-125">The next step is to add and remove the command which is associated with the command source.</span></span>  <span data-ttu-id="11532-126">O <xref:System.Windows.Input.ICommandSource.Command%2A> propriedade não pode ser simplesmente sobrescrita quando um comando novo é adicionado, pois os manipuladores de eventos associados ao comando anterior, se houver algum, devem ser removidas primeiro.</span><span class="sxs-lookup"><span data-stu-id="11532-126">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 <span data-ttu-id="11532-127">A última etapa é criar a lógica para o <xref:System.Windows.Input.ICommand.CanExecuteChanged> manipulador e <xref:System.Windows.Input.ICommand.Execute%2A> método.</span><span class="sxs-lookup"><span data-stu-id="11532-127">The last step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler and the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span>  
  
 <span data-ttu-id="11532-128">O <xref:System.Windows.Input.ICommand.CanExecuteChanged> evento informa a fonte de comando que a capacidade do comando a ser executado no seu atual destino pode ter sido alterado.</span><span class="sxs-lookup"><span data-stu-id="11532-128">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span>  <span data-ttu-id="11532-129">Quando uma fonte de comandos recebe esse evento, ela normalmente chama o <xref:System.Windows.Input.ICommand.CanExecute%2A> método no comando.</span><span class="sxs-lookup"><span data-stu-id="11532-129">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span>  <span data-ttu-id="11532-130">Se o comando não puder executar no destino do comando atual, geralmente, a fonte de comando se desabilitará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="11532-130">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span>  <span data-ttu-id="11532-131">Se o comando puder executar no destino do comando atual, geralmente, a fonte de comando se habilitará por conta própria.</span><span class="sxs-lookup"><span data-stu-id="11532-131">If the command can execute on the current command target, the command source will typically enable itself.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 <span data-ttu-id="11532-132">A última etapa é o <xref:System.Windows.Input.ICommand.Execute%2A> método.</span><span class="sxs-lookup"><span data-stu-id="11532-132">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span>  <span data-ttu-id="11532-133">Se o comando for um <xref:System.Windows.Input.RoutedCommand>, o <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> método é chamado; caso contrário, o <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> método é chamado.</span><span class="sxs-lookup"><span data-stu-id="11532-133">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a><span data-ttu-id="11532-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11532-134">See Also</span></span>  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="11532-135">Visão geral dos comandos</span><span class="sxs-lookup"><span data-stu-id="11532-135">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)