---
title: "Serviço básico XAML apenas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fbf8a719647199439e2333ba5e26cbe51be3add
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="f86f9-102">Serviço básico XAML apenas</span><span class="sxs-lookup"><span data-stu-id="f86f9-102">Basic XAML only Service</span></span>
<span data-ttu-id="f86f9-103">Este exemplo demonstra como criar um serviço XAML somente.</span><span class="sxs-lookup"><span data-stu-id="f86f9-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="f86f9-104">O cenário é um serviço de diagnóstico para carro- problemas relacionados.</span><span class="sxs-lookup"><span data-stu-id="f86f9-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="f86f9-105">O serviço é implementado como um fluxo de trabalho que faz a um cliente a série de perguntas diagnosticar o problema.</span><span class="sxs-lookup"><span data-stu-id="f86f9-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="f86f9-106">Há dois tipos de problemas que o serviço pode diagnosticar (o carro não inicia ou o ar condicionamento que não funciona).</span><span class="sxs-lookup"><span data-stu-id="f86f9-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="f86f9-107">O modelo solicitação/resposta usos de fluxo de trabalho de designer expor três operações de serviço simples.</span><span class="sxs-lookup"><span data-stu-id="f86f9-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="f86f9-108">O serviço está hospedado no IIS criando um diretório virtual no IIS e copiando o service1.xamlx e os arquivos web.config no diretório virtual, nenhum código compilado é necessário.</span><span class="sxs-lookup"><span data-stu-id="f86f9-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="f86f9-109">Por padrão Este exemplo copiará automaticamente os arquivos necessários para o diretório virtual criado quando você seguir as instruções de instalação para os exemplos do WCF e WF: [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) quando compilado no Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f86f9-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f86f9-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="f86f9-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="f86f9-111">Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="f86f9-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="f86f9-112">Executam aplicativo cliente gerado em [] do diretório da solução cliente \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="f86f9-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="f86f9-113">As cópias do aplicativo - out as opções, selecione uma opção.</span><span class="sxs-lookup"><span data-stu-id="f86f9-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="f86f9-114">O aplicativo faz em algumas questões, responde-lhes sim ou nenhum (usando chaves de Y/N).</span><span class="sxs-lookup"><span data-stu-id="f86f9-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="f86f9-115">Quando o serviço é feito que diagnostica problemas, o aplicativo imprime para fora um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="f86f9-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="f86f9-116">O aplicativo volta em padrões.</span><span class="sxs-lookup"><span data-stu-id="f86f9-116">The application goes back to the options.</span></span> <span data-ttu-id="f86f9-117">Você pode diagnosticar outro problema ou sair do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f86f9-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f86f9-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f86f9-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f86f9-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f86f9-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f86f9-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f86f9-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f86f9-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f86f9-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`  
  
## <a name="see-also"></a><span data-ttu-id="f86f9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f86f9-122">See Also</span></span>