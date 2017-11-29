---
title: "Cenários assíncronos usando HTTP, TCP ou pipe nomeado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c697069aad590013ff360eb6ee4cba39468b89d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="1992a-102">Cenários assíncronos usando HTTP, TCP ou pipe nomeado</span><span class="sxs-lookup"><span data-stu-id="1992a-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="1992a-103">Este tópico descreve as atividades e transferências para cenários diferentes de solicitação/resposta assíncrono, com multithread solicitações usando HTTP, TCP ou pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="1992a-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="1992a-104">Solicitação/resposta assíncrona sem erros</span><span class="sxs-lookup"><span data-stu-id="1992a-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="1992a-105">Esta seção descreve as atividades e transferências para um cenário de solicitação/resposta assíncrono, com clientes multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="1992a-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="1992a-106">A atividade de chamador termina quando `beginCall` retorna, e `endCall` retorna.</span><span class="sxs-lookup"><span data-stu-id="1992a-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="1992a-107">Se um retorno de chamada é chamado, retorna o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="1992a-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="1992a-108">A atividade chamada termina quando `beginCall` retorna, `endCall` retorna, ou quando o retorno de chamada retorna se ele foi chamado a partir dessa atividade.</span><span class="sxs-lookup"><span data-stu-id="1992a-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="1992a-109">Cliente assíncrona sem retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="1992a-110">Propagação está habilitada nos dois lados, usando HTTP</span><span class="sxs-lookup"><span data-stu-id="1992a-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 <span data-ttu-id="1992a-111">![Cenários assíncronos](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span><span class="sxs-lookup"><span data-stu-id="1992a-111">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span></span>  
  
 <span data-ttu-id="1992a-112">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="1992a-112">Figure 1.</span></span> <span data-ttu-id="1992a-113">Cliente assíncrono, nenhum retorno de chamada, `propagateActivity` = `true` em ambos os lados, HTTP</span><span class="sxs-lookup"><span data-stu-id="1992a-113">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, HTTP</span></span>  
  
 <span data-ttu-id="1992a-114">Se `propagateActivity` = `true`, ProcessMessage indica qual atividade ProcessAction para transferir para o.</span><span class="sxs-lookup"><span data-stu-id="1992a-114">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="1992a-115">Para cenários com base em HTTP, ReceiveBytes for invocado com a primeira mensagem ser enviada e se existe para o tempo de vida da solicitação.</span><span class="sxs-lookup"><span data-stu-id="1992a-115">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="1992a-116">Propagação está desabilitada nos lados tanto, usando HTTP</span><span class="sxs-lookup"><span data-stu-id="1992a-116">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="1992a-117">Se `propagateActivity` = `false` em ambos os lados, ProcessMessage não indica qual atividade ProcessAction para transferir para o.</span><span class="sxs-lookup"><span data-stu-id="1992a-117">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="1992a-118">Portanto, uma nova atividade ProcessAction temporária com uma nova ID é invocada.</span><span class="sxs-lookup"><span data-stu-id="1992a-118">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="1992a-119">Quando a resposta assíncrona corresponde à solicitação de código de ServiceModel, a ID de atividade podem ser recuperada do contexto local.</span><span class="sxs-lookup"><span data-stu-id="1992a-119">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="1992a-120">A atividade ProcessAction real pode ser transferida para com essa ID.</span><span class="sxs-lookup"><span data-stu-id="1992a-120">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="1992a-121">![Cenários assíncronos usando HTTP &#47; TCP &#47; Pipe nomeado](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span><span class="sxs-lookup"><span data-stu-id="1992a-121">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span></span>  
  
 <span data-ttu-id="1992a-122">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="1992a-122">Figure 2.</span></span> <span data-ttu-id="1992a-123">Cliente assíncrono, nenhum retorno de chamada, `propagateActivity` = `false` em ambos os lados, HTTP</span><span class="sxs-lookup"><span data-stu-id="1992a-123">Asynchronous client, no callback, `propagateActivity`=`false` on either side, HTTP</span></span>  
  
 <span data-ttu-id="1992a-124">Para cenários com base em HTTP, ReceiveBytes for invocado com a primeira mensagem ser enviada e se existe para o tempo de vida da solicitação.</span><span class="sxs-lookup"><span data-stu-id="1992a-124">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="1992a-125">Uma atividade de ação de processo é criada em um cliente assíncrono quando `propagateActivity` = `false` no chamador ou receptor e quando a mensagem de resposta não inclui um cabeçalho de ação.</span><span class="sxs-lookup"><span data-stu-id="1992a-125">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="1992a-126">Propagação está habilitada nos dois lados, usando TCP ou Pipe nomeado</span><span class="sxs-lookup"><span data-stu-id="1992a-126">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="1992a-127">![Cenários assíncronos usando HTTP &#47; TCP &#47; Pipe nomeado](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span><span class="sxs-lookup"><span data-stu-id="1992a-127">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span></span>  
  
 <span data-ttu-id="1992a-128">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="1992a-128">Figure 3.</span></span> <span data-ttu-id="1992a-129">Cliente assíncrono, nenhum retorno de chamada, `propagateActivity` = `true` em ambos os lados, Pipe nomeado/TCP</span><span class="sxs-lookup"><span data-stu-id="1992a-129">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, Named-Pipe/TCP</span></span>  
  
 <span data-ttu-id="1992a-130">Para um cenário com base em TCP ou Pipe nomeado, ReceiveBytes é invocado quando o cliente é aberto e existe durante a vida útil de conexão.</span><span class="sxs-lookup"><span data-stu-id="1992a-130">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="1992a-131">Semelhante à Figura 1, se `propagateActivity` = `true`, ProcessMessage indica qual atividade ProcessAction para transferir para o.</span><span class="sxs-lookup"><span data-stu-id="1992a-131">Similar to Figure 1, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="1992a-132">Propagação está desabilitada nos lados tanto, usando TCP ou Pipe nomeado</span><span class="sxs-lookup"><span data-stu-id="1992a-132">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="1992a-133">Para um cenário com base em TCP ou Pipe nomeado, ReceiveBytes é invocado quando o cliente é aberto e existe durante a vida útil de conexão.</span><span class="sxs-lookup"><span data-stu-id="1992a-133">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="1992a-134">Semelhante ao Fig.2, se `propagateActivity` = `false` em ambos os lados, ProcessMessage não indica qual atividade ProcessAction para transferir para o.</span><span class="sxs-lookup"><span data-stu-id="1992a-134">Similar to Fig.2, If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="1992a-135">Portanto, uma nova atividade ProcessAction temporária com uma nova ID é invocada.</span><span class="sxs-lookup"><span data-stu-id="1992a-135">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="1992a-136">Quando a resposta assíncrona corresponde à solicitação de código de ServiceModel, a ID de atividade podem ser recuperada do contexto local.</span><span class="sxs-lookup"><span data-stu-id="1992a-136">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="1992a-137">A atividade ProcessAction real pode ser transferida para com essa ID.</span><span class="sxs-lookup"><span data-stu-id="1992a-137">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="1992a-138">![Cenários assíncronos usando HTTP &#47; TCP &#47; Pipes nomeados](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span><span class="sxs-lookup"><span data-stu-id="1992a-138">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span></span>  
  
 <span data-ttu-id="1992a-139">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="1992a-139">Figure 4.</span></span> <span data-ttu-id="1992a-140">Cliente assíncrono, nenhum retorno de chamada, `propagateActivity` = `false` em ambos os lados, Pipe nomeado/TCP</span><span class="sxs-lookup"><span data-stu-id="1992a-140">Asynchronous client, no callback, `propagateActivity`=`false` on either side, Named-Pipe/TCP</span></span>  
  
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="1992a-141">Cliente assíncrono com retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-141">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="1992a-142">Esse cenário adiciona atividades G e um ', para o retorno de chamada e `endCall`e suas transferências de entrada/saída.</span><span class="sxs-lookup"><span data-stu-id="1992a-142">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="1992a-143">Esta seção demonstra somente usando HTTP com `propragateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="1992a-143">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="1992a-144">No entanto, as atividades adicionais e transferências também se aplicam a outros casos (ou seja, `propagateActivity` = `false`, usando TCP ou Pipe nomeado).</span><span class="sxs-lookup"><span data-stu-id="1992a-144">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="1992a-145">O retorno de chamada cria uma nova atividade (G) quando o cliente chama o código de usuário para notificar que os resultados estão prontos.</span><span class="sxs-lookup"><span data-stu-id="1992a-145">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="1992a-146">Código do usuário, em seguida, chama `endCall` no retorno de chamada (conforme mostrado na Figura 5) ou fora de retorno de chamada (Figura 6).</span><span class="sxs-lookup"><span data-stu-id="1992a-146">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="1992a-147">Porque não se sabe qual atividade de usuário `endCall` está sendo chamado, essa atividade é rotulada `A’`.</span><span class="sxs-lookup"><span data-stu-id="1992a-147">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="1992a-148">É possível que A' pode ser idêntico a ou diferente da.</span><span class="sxs-lookup"><span data-stu-id="1992a-148">It is possible that A’ can be identical to or different from A.</span></span>  
  
 <span data-ttu-id="1992a-149">![Cenários assíncronos](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span><span class="sxs-lookup"><span data-stu-id="1992a-149">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span></span>  
  
 <span data-ttu-id="1992a-150">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="1992a-150">Figure 5.</span></span> <span data-ttu-id="1992a-151">Cliente assíncrono com retorno de chamada, `endCall` no retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-151">Asynchronous client with callback, `endCall` in Callback</span></span>  
  
 <span data-ttu-id="1992a-152">![Cenários assíncronos](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span><span class="sxs-lookup"><span data-stu-id="1992a-152">![Asynchronous Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span></span>  
  
 <span data-ttu-id="1992a-153">Figura 6.</span><span class="sxs-lookup"><span data-stu-id="1992a-153">Figure 6.</span></span> <span data-ttu-id="1992a-154">Cliente assíncrono com retorno de chamada, `endCall` fora de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-154">Asynchronous client with callback, `endCall` outside of Callback</span></span>  
  
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="1992a-155">Servidor assíncrono com retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-155">Asynchronous Server with Callback</span></span>  
 <span data-ttu-id="1992a-156">![Cenários assíncronos usando HTTP &#47; TCP &#47; Chamada &#45; Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span><span class="sxs-lookup"><span data-stu-id="1992a-156">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named&#45;Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span></span>  
  
 <span data-ttu-id="1992a-157">Figura 7.</span><span class="sxs-lookup"><span data-stu-id="1992a-157">Figure 7.</span></span> <span data-ttu-id="1992a-158">Servidor assíncrona, com retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1992a-158">Asynchronous server, with callback</span></span>  
  
 <span data-ttu-id="1992a-159">A pilha de canais chama novamente o cliente de recebimento de mensagens: rastreamentos para esse processamento são emitidos na atividade ProcessRequest em si.</span><span class="sxs-lookup"><span data-stu-id="1992a-159">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="1992a-160">Solicitação/resposta assíncrona com erros</span><span class="sxs-lookup"><span data-stu-id="1992a-160">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="1992a-161">Erros de mensagem de falha for recebidos durante `endCall`.</span><span class="sxs-lookup"><span data-stu-id="1992a-161">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="1992a-162">Caso contrário, atividades e transferências são semelhantes aos cenários anteriores.</span><span class="sxs-lookup"><span data-stu-id="1992a-162">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="1992a-163">Assíncrono unidirecional com ou sem erros</span><span class="sxs-lookup"><span data-stu-id="1992a-163">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="1992a-164">Nenhuma resposta ou a falha é retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="1992a-164">No response or fault is returned to the client.</span></span>