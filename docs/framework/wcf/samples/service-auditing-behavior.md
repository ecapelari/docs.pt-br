---
title: "Comportamento de auditoria de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e7e85ac2aa5be9614946418f0df676ea1cb7dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="82a33-102">Comportamento de auditoria de serviço</span><span class="sxs-lookup"><span data-stu-id="82a33-102">Service Auditing Behavior</span></span>
<span data-ttu-id="82a33-103">Este exemplo demonstra como usar o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> para habilitar a auditoria de eventos de segurança durante operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="82a33-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="82a33-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="82a33-105">O serviço e o cliente tiverem sido configurados usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-105">The service and client have been configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="82a33-106">O `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definida como `Message` e `clientCredentialType` foi definida como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="82a33-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="82a33-107">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="82a33-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82a33-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="82a33-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="82a33-109">O arquivo de configuração de serviço usa o `serviceSecurityAudit` elemento para configurar a auditoria.</span><span class="sxs-lookup"><span data-stu-id="82a33-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="82a33-110">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="82a33-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="82a33-111">Pressione ENTER na janela do console para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="82a33-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="82a33-112">Os logs de auditoria resultante podem ser vistos ao executar o Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="82a33-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="82a33-113">Por padrão, no Windows XP, os eventos de auditoria podem ser vistos no Log do aplicativo ao mesmo tempo no Windows Server 2003 e Windows Vista, os eventos de auditoria podem ser vistos no Log de segurança.</span><span class="sxs-lookup"><span data-stu-id="82a33-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="82a33-114">No Windows Server 2008 e Windows 7, os eventos de auditoria podem ser vistos nos logs de aplicativos e serviços.</span><span class="sxs-lookup"><span data-stu-id="82a33-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="82a33-115">O local dos eventos de auditoria pode ser especificado definindo a `auditLogLocation` atributo "Aplicativo" ou "Segurança".</span><span class="sxs-lookup"><span data-stu-id="82a33-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="82a33-116">Para obter mais informações, consulte [como: eventos de auditoria de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-116">For more information, see [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="82a33-117">Se os eventos são gravados no Log de segurança do LocalSecurityPolicy -> que habilitar acesso do objeto deve ser definido como "Êxito" e "Falha".</span><span class="sxs-lookup"><span data-stu-id="82a33-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="82a33-118">Ao examinar o log de eventos, a origem dos eventos de auditoria é "ServiceModel auditoria 3.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="82a33-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="82a33-119">Registros de auditoria de autenticação de mensagem tem uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço tem uma categoria de "ServiceAuthorization".</span><span class="sxs-lookup"><span data-stu-id="82a33-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="82a33-120">Eventos de auditoria de autenticação de mensagem abrangem se a mensagem foi violada, se a mensagem expirou, e se o cliente pode autenticar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="82a33-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="82a33-121">Eles fornecem informações sobre se a autenticação foi bem-sucedida ou falhou com a identidade do cliente e o ponto de extremidade a mensagem foi enviado ao junto com a ação associada à mensagem.</span><span class="sxs-lookup"><span data-stu-id="82a33-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="82a33-122">Eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização do serviço.</span><span class="sxs-lookup"><span data-stu-id="82a33-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="82a33-123">Eles fornecem informações sobre se a autorização teve êxito ou falha com a identidade do cliente, o ponto de extremidade a mensagem foi enviado para a ação associada à mensagem, o identificador do contexto de autorização que foi gerado a partir de mensagem de entrada e o tipo do Gerenciador de autorização que fez a decisão de acesso.</span><span class="sxs-lookup"><span data-stu-id="82a33-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82a33-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="82a33-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="82a33-125">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="82a33-126">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="82a33-127">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82a33-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a33-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a33-128">See Also</span></span>  
 [<span data-ttu-id="82a33-129">A auditoria</span><span class="sxs-lookup"><span data-stu-id="82a33-129">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="82a33-130">Como: auditoria de eventos de segurança</span><span class="sxs-lookup"><span data-stu-id="82a33-130">How to: Audit Security Events</span></span>](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)