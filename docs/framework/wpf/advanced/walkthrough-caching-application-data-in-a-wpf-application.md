---
title: "Instruções passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF"
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
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c04a2860b46460065a09de3dafedc7010753d36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="6ef50-102">Instruções passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="6ef50-103">O cache permite que você armazene dados na memória para acesso rápido.</span><span class="sxs-lookup"><span data-stu-id="6ef50-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="6ef50-104">Quando os dados são acessados novamente, os aplicativos podem obter os dados do cache em vez de recuperá-los da fonte original.</span><span class="sxs-lookup"><span data-stu-id="6ef50-104">When the data is accessed again, applications can get the data from the cache instead retrieving it from the original source.</span></span> <span data-ttu-id="6ef50-105">Isso pode melhorar o desempenho e a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="6ef50-105">This can improve performance and scalability.</span></span> <span data-ttu-id="6ef50-106">Além disso, o cache torna os dados disponíveis quando a fonte de dados está temporariamente indisponível.</span><span class="sxs-lookup"><span data-stu-id="6ef50-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>  
  
 <span data-ttu-id="6ef50-107">O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece classes que permitem que você use o cache em aplicativos do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="6ef50-108">Essas classes estão localizadas no <xref:System.Runtime.Caching> namespace.</span><span class="sxs-lookup"><span data-stu-id="6ef50-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ef50-109">O <xref:System.Runtime.Caching> namespace é novo no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="6ef50-110">Esse namespace torna o cache disponível para todos os aplicativos do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="6ef50-111">Nas versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], o cache estava disponível apenas no namespace <xref:System.Web> e, portanto, exigia uma dependência das classes do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6ef50-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>  
  
 <span data-ttu-id="6ef50-112">Este passo a passo mostra como usar a funcionalidade de cache que está disponível no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] como parte de um aplicativo do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="6ef50-113">No passo a passo, você armazenará em cache o conteúdo de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-113">In the walkthrough, you cache the contents of a text file.</span></span>  
  
 <span data-ttu-id="6ef50-114">As tarefas ilustradas nesta explicação passo a passo incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ef50-114">Tasks illustrated in this walkthrough include the following:</span></span>  
  
-   <span data-ttu-id="6ef50-115">Criação de um projeto de aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="6ef50-115">Creating a WPF application project.</span></span>  
  
-   <span data-ttu-id="6ef50-116">Adição de uma referência ao [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="6ef50-117">Inicialização de um cache.</span><span class="sxs-lookup"><span data-stu-id="6ef50-117">Initializing a cache.</span></span>  
  
-   <span data-ttu-id="6ef50-118">Adição de uma entrada de cache que contém o conteúdo de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-118">Adding a cache entry that contains the contents of a text file.</span></span>  
  
-   <span data-ttu-id="6ef50-119">Fornecimento de uma política de remoção para a entrada de cache.</span><span class="sxs-lookup"><span data-stu-id="6ef50-119">Providing an eviction policy for the cache entry.</span></span>  
  
-   <span data-ttu-id="6ef50-120">Monitoramento do caminho do arquivo armazenado em cache e notificação da instância de cache a respeito de alterações ao item monitorado.</span><span class="sxs-lookup"><span data-stu-id="6ef50-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6ef50-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6ef50-121">Prerequisites</span></span>  
 <span data-ttu-id="6ef50-122">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="6ef50-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="6ef50-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="6ef50-124">Um arquivo de texto que contenha uma pequena quantidade de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="6ef50-125">(Você exibirá o conteúdo do arquivo de texto em uma caixa de mensagem). O código ilustrado no passo a passo presume que você esteja trabalhando com o seguinte arquivo:</span><span class="sxs-lookup"><span data-stu-id="6ef50-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>  
  
     `c:\cache\cacheText.txt`  
  
     <span data-ttu-id="6ef50-126">No entanto, você pode usar qualquer arquivo de texto e fazer pequenas alterações no código neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>  
  
## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="6ef50-127">Criação de um projeto de aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-127">Creating a WPF Application Project</span></span>  
 <span data-ttu-id="6ef50-128">Você começará criando um projeto de aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="6ef50-128">You will start by creating a WPF application project.</span></span>  
  
#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="6ef50-129">Para criar um aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-129">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="6ef50-130">Inicie o [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-130">Start [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ef50-131">No menu **Arquivo**, clique em **Novo** e, em seguida, clique em **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>  
  
     <span data-ttu-id="6ef50-132">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-132">The **New Project** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="6ef50-133">Em **Modelos Instalados**, selecione a linguagem de programação que você deseja usar (**Visual Basic** ou **Visual C#**).</span><span class="sxs-lookup"><span data-stu-id="6ef50-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>  
  
4.  <span data-ttu-id="6ef50-134">Na caixa de diálogo **Novo Projeto**, selecione **Aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-134">In the **New Project** dialog box, select **WPF Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ef50-135">Se você não vir o modelo do **Aplicativo WPF**, verifique se tem como destino uma versão do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] que dá suporte ao WPF.</span><span class="sxs-lookup"><span data-stu-id="6ef50-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="6ef50-136">Na caixa de diálogo **Novo Projeto**, selecione [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] na lista.</span><span class="sxs-lookup"><span data-stu-id="6ef50-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>  
  
5.  <span data-ttu-id="6ef50-137">Na caixa de texto **Nome**, insira um nome para o projeto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="6ef50-138">Por exemplo, você pode inserir **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-138">For example, you can enter **WPFCaching**.</span></span>  
  
6.  <span data-ttu-id="6ef50-139">Marque a caixa de seleção **Criar diretório para a solução**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-139">Select the **Create directory for solution** check box.</span></span>  
  
7.  <span data-ttu-id="6ef50-140">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-140">Click **OK**.</span></span>  
  
     <span data-ttu-id="6ef50-141">O WPF Designer é aberto modo de exibição de **Design** e exibe o arquivo MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="6ef50-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="6ef50-142">O [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] cria a pasta **Meu Projeto**, o arquivo Application.xaml e o arquivo MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="6ef50-142">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="6ef50-143">Direcionamento ao .NET Framework e adição de uma referência aos assemblies de cache</span><span class="sxs-lookup"><span data-stu-id="6ef50-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>  
 <span data-ttu-id="6ef50-144">Por padrão, os aplicativos do WPF se destinam ao [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="6ef50-145">Para usar o <xref:System.Runtime.Caching> namespace em um aplicativo WPF, o aplicativo deve se destinar a [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (não o [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) e deve incluir uma referência ao namespace.</span><span class="sxs-lookup"><span data-stu-id="6ef50-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>  
  
 <span data-ttu-id="6ef50-146">Portanto, a próxima etapa é alterar o destino do .NET Framework e adicione uma referência para o <xref:System.Runtime.Caching> namespace.</span><span class="sxs-lookup"><span data-stu-id="6ef50-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ef50-147">O procedimento para alterar o destino do .NET Framework é diferente em um projeto do Visual Basic e em um projeto Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6ef50-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="6ef50-148">Para alterar o .NET Framework de destino no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ef50-148">To change the target .NET Framework in Visual Basic</span></span>  
  
1.  <span data-ttu-id="6ef50-149">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="6ef50-150">A janela Propriedades para o aplicativo é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-150">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="6ef50-151">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-151">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="6ef50-152">Na parte inferior da janela, clique em **Opções Avançadas de Compilação...**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>  
  
     <span data-ttu-id="6ef50-153">A caixa de diálogo **Configurações Avançadas do Compilador** é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="6ef50-154">Na lista **Estrutura de destino (todas as configurações)**, selecione [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="6ef50-155">(Não selecione [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="6ef50-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>  
  
5.  <span data-ttu-id="6ef50-156">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-156">Click **OK**.</span></span>  
  
     <span data-ttu-id="6ef50-157">A caixa de diálogo **Alteração da Estrutura de Destino** é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-157">The **Target Framework Change** dialog box is displayed.</span></span>  
  
6.  <span data-ttu-id="6ef50-158">Na caixa de diálogo **Alteração da Estrutura de Destino** clique em **Sim**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>  
  
     <span data-ttu-id="6ef50-159">O projeto é fechado e, em seguida, é reaberto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-159">The project is closed and is then reopened.</span></span>  
  
7.  <span data-ttu-id="6ef50-160">Adicione uma referência ao assembly do cache, seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6ef50-160">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="6ef50-161">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="6ef50-162">Selecione a guia **.NET**, selecione `System.Runtime.Caching` e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="6ef50-163">Para alterar o .NET Framework de destino em um projeto do Visual C#</span><span class="sxs-lookup"><span data-stu-id="6ef50-163">To change the target .NET Framework in a Visual C# project</span></span>  
  
1.  <span data-ttu-id="6ef50-164">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto e, em seguida, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>  
  
     <span data-ttu-id="6ef50-165">A janela Propriedades para o aplicativo é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-165">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="6ef50-166">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-166">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="6ef50-167">Na lista **Estrutura de destino**, selecione [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ef50-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="6ef50-168">(Não selecione **.NET Framework 4 Client Profile**).</span><span class="sxs-lookup"><span data-stu-id="6ef50-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>  
  
4.  <span data-ttu-id="6ef50-169">Adicione uma referência ao assembly do cache, seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6ef50-169">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="6ef50-170">Clique com o botão direito do mouse na pasta **Referencias** e, em seguida, clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-170">Right-click the **References** folder and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="6ef50-171">Selecione a guia **.NET**, selecione `System.Runtime.Caching` e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="6ef50-172">Adicionar um botão à janela do WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-172">Adding a Button to the WPF Window</span></span>  
 <span data-ttu-id="6ef50-173">Em seguida, você adicionará um controle de botão e criará um manipulador de eventos para o evento `Click` do botão.</span><span class="sxs-lookup"><span data-stu-id="6ef50-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="6ef50-174">Depois, você adicionará código para que quando o botão for clicado, o conteúdo do arquivo de texto será armazenado em cache e exibido.</span><span class="sxs-lookup"><span data-stu-id="6ef50-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>  
  
#### <a name="to-add-a-button-control"></a><span data-ttu-id="6ef50-175">Para adicionar um controle de botão</span><span class="sxs-lookup"><span data-stu-id="6ef50-175">To add a button control</span></span>  
  
1.  <span data-ttu-id="6ef50-176">No **Gerenciador de Soluções**, clique duas vezes no arquivo MainWindow.xaml para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>  
  
2.  <span data-ttu-id="6ef50-177">Na **Caixa de ferramentas**, em **Controles Comuns do WPF**, arraste um controle `Button` para a janela `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="6ef50-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>  
  
3.  <span data-ttu-id="6ef50-178">Na janela **Propriedades**, defina a propriedade `Content` do controle `Button` como **Obter Cache**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="6ef50-179">Inicializar o cache e armazenar uma entrada em cache</span><span class="sxs-lookup"><span data-stu-id="6ef50-179">Initializing the Cache and Caching an Entry</span></span>  
 <span data-ttu-id="6ef50-180">Em seguida, você adicionará o código para realizar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="6ef50-180">Next, you will add the code to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6ef50-181">Criar uma instância da classe cache — ou seja, você instanciará uma nova <xref:System.Runtime.Caching.MemoryCache> objeto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>  
  
-   <span data-ttu-id="6ef50-182">Especificar que o cache usa um <xref:System.Runtime.Caching.HostFileChangeMonitor> objeto para monitorar as alterações no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>  
  
-   <span data-ttu-id="6ef50-183">Ler o arquivo de texto e armazenar seu conteúdo em cache como uma entrada de cache.</span><span class="sxs-lookup"><span data-stu-id="6ef50-183">Read the text file and cache its contents as a cache entry.</span></span>  
  
-   <span data-ttu-id="6ef50-184">Exibir o conteúdo do arquivo de texto armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="6ef50-184">Display the contents of the cached text file.</span></span>  
  
#### <a name="to-create-the-cache-object"></a><span data-ttu-id="6ef50-185">Para criar o objeto do cache</span><span class="sxs-lookup"><span data-stu-id="6ef50-185">To create the cache object</span></span>  
  
1.  <span data-ttu-id="6ef50-186">Clique duas vezes no botão que você acabou de adicionar para criar um manipulador de eventos no arquivo MainWindow.xaml.cs ou MainWindow.Xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="6ef50-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>  
  
2.  <span data-ttu-id="6ef50-187">Na parte superior do arquivo (antes da declaração de classe), adicione as seguintes instruções `Imports` (Visual Basic) ou `using` (C#):</span><span class="sxs-lookup"><span data-stu-id="6ef50-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  <span data-ttu-id="6ef50-188">No manipulador de eventos, adicione o seguinte código para instanciar o objeto de cache:</span><span class="sxs-lookup"><span data-stu-id="6ef50-188">In the event handler, add the following code to instantiate the cache object:</span></span>  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <span data-ttu-id="6ef50-189">O <xref:System.Runtime.Caching.ObjectCache> classe é uma classe interna que fornece um cache de objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="6ef50-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>  
  
4.  <span data-ttu-id="6ef50-190">Adicione o seguinte código para ler o conteúdo de uma entrada de cache chamada `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="6ef50-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  <span data-ttu-id="6ef50-191">Adicione o seguinte código para verificar se a entrada de cache chamada `filecontents` existe:</span><span class="sxs-lookup"><span data-stu-id="6ef50-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     <span data-ttu-id="6ef50-192">Se a entrada de cache especificada não existe, leia o arquivo de texto e adicione-o como uma entrada de cache no cache.</span><span class="sxs-lookup"><span data-stu-id="6ef50-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>  
  
6.  <span data-ttu-id="6ef50-193">No `if/then` em bloco, adicione o seguinte código para criar um novo <xref:System.Runtime.Caching.CacheItemPolicy> objeto que especifica que a entrada de cache expire após 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="6ef50-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     <span data-ttu-id="6ef50-194">Se nenhuma informação de remoção ou expiração for fornecida, o padrão é <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, que significa que as entradas de cache nunca expirar com base apenas em um tempo absoluto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="6ef50-195">Em vez disso, as entradas de cache expiram somente quando há pressão de memória.</span><span class="sxs-lookup"><span data-stu-id="6ef50-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="6ef50-196">Como uma melhor prática, você deve sempre fornecer explicitamente uma expiração absoluta ou alternativa.</span><span class="sxs-lookup"><span data-stu-id="6ef50-196">As a best practice, you should always explicitly provide either an absolute or a siding expiration.</span></span>  
  
7.  <span data-ttu-id="6ef50-197">Dentro do bloco `if/then` e depois do código adicionado na etapa anterior, adicione o seguinte código para criar uma coleção para os caminhos de arquivo que você deseja monitorar e para adicionar o caminho do arquivo de texto à coleção:</span><span class="sxs-lookup"><span data-stu-id="6ef50-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6ef50-198">Se o arquivo de texto que você deseja usar não for `c:\cache\cacheText.txt`, especifique o caminho em que se encontra o arquivo de texto que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="6ef50-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>  
  
8.  <span data-ttu-id="6ef50-199">Após o código que você adicionou na etapa anterior, adicione o seguinte código para adicionar um novo <xref:System.Runtime.Caching.HostFileChangeMonitor> monitora o objeto à coleção de alteração para a entrada de cache:</span><span class="sxs-lookup"><span data-stu-id="6ef50-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <span data-ttu-id="6ef50-200">O <xref:System.Runtime.Caching.HostFileChangeMonitor> objeto monitora o caminho do arquivo de texto e notifica o cache se ocorrerem alterações.</span><span class="sxs-lookup"><span data-stu-id="6ef50-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="6ef50-201">Neste exemplo, a entrada de cache expirará se o conteúdo do arquivo for alterado.</span><span class="sxs-lookup"><span data-stu-id="6ef50-201">In this example, the cache entry will expire if the content of the file changes.</span></span>  
  
9. <span data-ttu-id="6ef50-202">Após o código que você adicionou na etapa anterior, adicione o seguinte código para ler o conteúdo do arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="6ef50-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     <span data-ttu-id="6ef50-203">O carimbo de data/hora é adicionado para que você possa ver quando a entrada de cache expira.</span><span class="sxs-lookup"><span data-stu-id="6ef50-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>  
  
10. <span data-ttu-id="6ef50-204">Após o código que você adicionou na etapa anterior, adicione o seguinte código para inserir o conteúdo do arquivo para o objeto de cache como um <xref:System.Runtime.Caching.CacheItem> instância:</span><span class="sxs-lookup"><span data-stu-id="6ef50-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     <span data-ttu-id="6ef50-205">Especifique informações sobre como a entrada de cache deve ser removida, passando o <xref:System.Runtime.Caching.CacheItemPolicy> objeto que você criou anteriormente como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6ef50-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>  
  
11. <span data-ttu-id="6ef50-206">Depois do bloco `if/then`, adicione o seguinte código para exibir o conteúdo do arquivo armazenado em cache em uma caixa de mensagem:</span><span class="sxs-lookup"><span data-stu-id="6ef50-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. <span data-ttu-id="6ef50-207">No menu **Compilar**, clique em **Compilar WPFCaching** para compilar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6ef50-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>  
  
## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="6ef50-208">Testando o cache no Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-208">Testing Caching in the WPF Application</span></span>  
 <span data-ttu-id="6ef50-209">Agora você pode testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-209">You can now test the application.</span></span>  
  
#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="6ef50-210">Para testar o cache no aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="6ef50-210">To test caching in the WPF application</span></span>  
  
1.  <span data-ttu-id="6ef50-211">Pressione CTRL+F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-211">Press CTRL+F5 to run the application.</span></span>  
  
     <span data-ttu-id="6ef50-212">A janela `MainWindow` é exibida.</span><span class="sxs-lookup"><span data-stu-id="6ef50-212">The `MainWindow` window is displayed.</span></span>  
  
2.  <span data-ttu-id="6ef50-213">Clique em **Obter Cache**.</span><span class="sxs-lookup"><span data-stu-id="6ef50-213">Click **Get Cache**.</span></span>  
  
     <span data-ttu-id="6ef50-214">O conteúdo em cache do arquivo de texto é exibido em uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6ef50-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="6ef50-215">Observe o carimbo de data/hora no arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-215">Notice the timestamp on the file.</span></span>  
  
3.  <span data-ttu-id="6ef50-216">Feche a caixa de mensagem e, em seguida, clique em **Obter Cache** novamente**.**</span><span class="sxs-lookup"><span data-stu-id="6ef50-216">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="6ef50-217">O carimbo de data/hora está inalterado.</span><span class="sxs-lookup"><span data-stu-id="6ef50-217">The timestamp is unchanged.</span></span> <span data-ttu-id="6ef50-218">Isso indica que o conteúdo em cache está exibido.</span><span class="sxs-lookup"><span data-stu-id="6ef50-218">This indicates the cached content is displayed.</span></span>  
  
4.  <span data-ttu-id="6ef50-219">Aguarde 10 segundos ou mais e, em seguida, clique em **Obter Cache** novamente.</span><span class="sxs-lookup"><span data-stu-id="6ef50-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="6ef50-220">Agora, um novo carimbo de data/hora é exibido.</span><span class="sxs-lookup"><span data-stu-id="6ef50-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="6ef50-221">Isso indica que a política deixou a entrada de cache expirar e que o novo conteúdo armazenado em cache fosse exibido.</span><span class="sxs-lookup"><span data-stu-id="6ef50-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>  
  
5.  <span data-ttu-id="6ef50-222">Em um editor de texto, abra o arquivo de texto que você criou.</span><span class="sxs-lookup"><span data-stu-id="6ef50-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="6ef50-223">Não faça nenhuma alteração ainda.</span><span class="sxs-lookup"><span data-stu-id="6ef50-223">Do not make any changes yet.</span></span>  
  
6.  <span data-ttu-id="6ef50-224">Feche a caixa de mensagem e, em seguida, clique em **Obter Cache** novamente**.**</span><span class="sxs-lookup"><span data-stu-id="6ef50-224">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="6ef50-225">Observe o carimbo de data/hora novamente.</span><span class="sxs-lookup"><span data-stu-id="6ef50-225">Notice the timestamp again.</span></span>  
  
7.  <span data-ttu-id="6ef50-226">Faça uma alteração no arquivo de texto e, em seguida, salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-226">Make a change to the text file and then save the file.</span></span>  
  
8.  <span data-ttu-id="6ef50-227">Feche a caixa de mensagem e, em seguida, clique em **Obter Cache** novamente.</span><span class="sxs-lookup"><span data-stu-id="6ef50-227">Close the message box and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="6ef50-228">Essa caixa de mensagem contém o conteúdo atualizado do arquivo de texto e um novo carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="6ef50-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="6ef50-229">Isso indica que o monitor de alteração do arquivo de host removeu a entrada de cache imediatamente após você alterar o arquivo, mesmo que o tempo limite de expiração absoluto não tenha se expirado.</span><span class="sxs-lookup"><span data-stu-id="6ef50-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ef50-230">Você pode aumentar o tempo de remoção para 20 segundos ou mais para permitir mais tempo para fazer uma alteração no arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ef50-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="6ef50-231">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="6ef50-231">Code Example</span></span>  
 <span data-ttu-id="6ef50-232">Depois de concluir este passo a passo, o código para o projeto que você criou será parecido com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ef50-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6ef50-233">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ef50-233">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [<span data-ttu-id="6ef50-234">Cache em aplicativos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6ef50-234">Caching in .NET Framework Applications</span></span>](../../../../docs/framework/performance/caching-in-net-framework-applications.md)