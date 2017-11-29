---
title: "Implementar provedores de automação de interface do usuário em um aplicativo cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: "6"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ae7b478ec8d836f1e0772d81185b9bb0119c0fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="69f47-102">Implementar provedores de automação de interface do usuário em um aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="69f47-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
>  <span data-ttu-id="69f47-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="69f47-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="69f47-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="69f47-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="69f47-105">Este tópico contém código de exemplo que mostra como implementar um provedor de automação de interface do usuário do lado do cliente em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69f47-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="69f47-106">Este é um cenário comum.</span><span class="sxs-lookup"><span data-stu-id="69f47-106">This is an uncommon scenario.</span></span> <span data-ttu-id="69f47-107">Geralmente, um aplicativo de cliente de automação de interface do usuário usa no lado do servidor, ou provedores de cliente que residem em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="69f47-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69f47-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69f47-108">Example</span></span>  
 <span data-ttu-id="69f47-109">O exemplo de código a seguir implementa um provedor simples para uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="69f47-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="69f47-110">O código não tem nenhuma funcionalidade útil, mas serve para demonstrar as etapas básicas da configuração de um provedor de dentro do código de cliente e registrando-os usando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span><span class="sxs-lookup"><span data-stu-id="69f47-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="69f47-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69f47-111">See Also</span></span>  
 [<span data-ttu-id="69f47-112">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="69f47-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="69f47-113">Registrar um Assembly do provedor do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="69f47-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)  
 [<span data-ttu-id="69f47-114">Criar um provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="69f47-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)  
 [<span data-ttu-id="69f47-115">Implementação de provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="69f47-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)