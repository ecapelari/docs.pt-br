---
title: Paralelo estrangulado ForEach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c8336060be48f55b974960e67ca1ebc57e76c63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="322ff-102">Paralelo estrangulado ForEach</span><span class="sxs-lookup"><span data-stu-id="322ff-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="322ff-103">O `ThrottleParallelForEach` atividade é semelhante do <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` atividade com uma exceção que permite definir um fator de simultaneidade para restringir o número de ramificações simultâneas para executar.</span><span class="sxs-lookup"><span data-stu-id="322ff-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="322ff-104">A atividade de `ThrottleParallelForEach` deriva de <xref:System.Activities.NativeActivity>, porque precisa agendar outras atividades (as atividades filho) e isso é acessível somente por meio da classe <xref:System.Activities.NativeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="322ff-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="322ff-105">Projetos</span><span class="sxs-lookup"><span data-stu-id="322ff-105">Projects</span></span>  
  
|<span data-ttu-id="322ff-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="322ff-106">**ProjectName**</span></span>|<span data-ttu-id="322ff-107">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="322ff-107">**Description**</span></span>|<span data-ttu-id="322ff-108">**Arquivos principais**</span><span class="sxs-lookup"><span data-stu-id="322ff-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="322ff-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="322ff-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="322ff-110">Contém a atividade de `ThrottledParallelForEach` e o designer.</span><span class="sxs-lookup"><span data-stu-id="322ff-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="322ff-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="322ff-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="322ff-112">A definição de atividade de `ThrottledParallelForEach` .</span><span class="sxs-lookup"><span data-stu-id="322ff-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="322ff-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="322ff-113">CodeTestClient</span></span>|<span data-ttu-id="322ff-114">Exemplo do aplicativo cliente que configura e executa um fluxo de trabalho com `ThrottledParallelForEach` usando o código obrigatório.</span><span class="sxs-lookup"><span data-stu-id="322ff-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="322ff-115">Module.vb</span><span class="sxs-lookup"><span data-stu-id="322ff-115">Program.cs</span></span><br /><br /> <span data-ttu-id="322ff-116">Define e executa uma instância de fluxo de trabalho de exemplo.</span><span class="sxs-lookup"><span data-stu-id="322ff-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="322ff-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="322ff-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="322ff-118">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de ThrottledParallelForEach.sln.</span><span class="sxs-lookup"><span data-stu-id="322ff-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="322ff-119">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="322ff-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="322ff-120">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="322ff-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="322ff-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="322ff-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="322ff-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="322ff-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="322ff-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="322ff-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="322ff-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="322ff-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`  
  
## <a name="see-also"></a><span data-ttu-id="322ff-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="322ff-125">See Also</span></span>