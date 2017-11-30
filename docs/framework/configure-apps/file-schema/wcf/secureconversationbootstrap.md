---
title: '&lt;secureConversationBootstrap&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66b46f95-fa2d-4b5b-b6ce-0572ab0cdd50
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8b29b9b4253e51f8cc1d0625fb27998a2d10b3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationbootstrapgt"></a><span data-ttu-id="b09d4-102">&lt;secureConversationBootstrap&gt;</span><span class="sxs-lookup"><span data-stu-id="b09d4-102">&lt;secureConversationBootstrap&gt;</span></span>
<span data-ttu-id="b09d4-103">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="b09d4-103">Specifies the default values used for initiating a secure conversation service.</span></span>  
  
 <span data-ttu-id="b09d4-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b09d4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b09d4-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="b09d4-105">\<bindings></span></span>  
<span data-ttu-id="b09d4-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b09d4-106">\<customBinding></span></span>  
<span data-ttu-id="b09d4-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b09d4-107">\<binding></span></span>  
<span data-ttu-id="b09d4-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="b09d4-108">\<security></span></span>  
<span data-ttu-id="b09d4-109">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="b09d4-109">\<secureConversationBootstrap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b09d4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b09d4-110">Syntax</span></span>  
  
```xml  
<secureConversationBootstrap  
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
   defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
   requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
   messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean" >  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="b09d4-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="b09d4-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b09d4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b09d4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b09d4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b09d4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b09d4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b09d4-114">Attributes</span></span>  
  
|<span data-ttu-id="b09d4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b09d4-115">Attribute</span></span>|<span data-ttu-id="b09d4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09d4-116">Description</span></span>|  
|---------------|-----------------|  
|`allowSerializedSigningTokenOnReply`|<span data-ttu-id="b09d4-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b09d4-117">Optional.</span></span> <span data-ttu-id="b09d4-118">Um valor booleano que especifica se um token serializado pode ser usado na resposta.</span><span class="sxs-lookup"><span data-stu-id="b09d4-118">A Boolean value that specifies if a serialized token can be used on reply.</span></span> <span data-ttu-id="b09d4-119">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-119">The default value is `false`.</span></span> <span data-ttu-id="b09d4-120">Ao usar uma associação dupla, a configuração padrão é `true` qualquer configuração feita será ignorada.</span><span class="sxs-lookup"><span data-stu-id="b09d4-120">When using a dual binding, the setting defaults to `true` any setting made will be ignored.</span></span>|  
|`authenticationMode`|<span data-ttu-id="b09d4-121">Especifica o modo de autenticação SOAP usado entre o iniciador e respondente.</span><span class="sxs-lookup"><span data-stu-id="b09d4-121">Specifies the SOAP authentication mode used between the initiator and the responder.</span></span><br /><br /> <span data-ttu-id="b09d4-122">O padrão é sspiNegotiated.</span><span class="sxs-lookup"><span data-stu-id="b09d4-122">The default is sspiNegotiated.</span></span><br /><br /> <span data-ttu-id="b09d4-123">Esse atributo é do tipo <xref:System.ServiceModel.Configuration.AuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-123">This attribute is of type <xref:System.ServiceModel.Configuration.AuthenticationMode>.</span></span>|  
|`defaultAlgorithmSuite`|<span data-ttu-id="b09d4-124">Conjunto de algoritmos de segurança define uma variedade de algoritmos como canonização, Digest, KeyWrap, assinatura, criptografia e keyderivation.</span><span class="sxs-lookup"><span data-stu-id="b09d4-124">Security algorithm suite defines of a variety of algorithms such as Canonicalization, Digest, KeyWrap, Signature, Encryption, and KeyDerivation algorithms.</span></span> <span data-ttu-id="b09d4-125">Cada um dos pacotes de algoritmo de segurança define valores para esses parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="b09d4-125">Each of the security algorithm suites defines values for these different parameters.</span></span> <span data-ttu-id="b09d4-126">Segurança baseada em mensagem é obtida usando esses algoritmos.</span><span class="sxs-lookup"><span data-stu-id="b09d4-126">Message-based security is achieved using these algorithms.</span></span><br /><br /> <span data-ttu-id="b09d4-127">Este atributo é usado quando se trabalha com uma plataforma diferente que aceita um conjunto de algoritmos diferentes do padrão.</span><span class="sxs-lookup"><span data-stu-id="b09d4-127">This attribute is used when working with a different platform that opts for a set of algorithms different than the default.</span></span> <span data-ttu-id="b09d4-128">Você deve conhecer as vantagens e desvantagens dos algoritmos relevantes ao fazer modificações para essa configuração.</span><span class="sxs-lookup"><span data-stu-id="b09d4-128">You should be aware of the strengths and weaknesses of the relevant algorithms when making modifications to this setting.</span></span> <span data-ttu-id="b09d4-129">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-129">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="b09d4-130">O padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-130">The default is `Basic256`.</span></span>|  
|`includeTimestamp`|<span data-ttu-id="b09d4-131">Um valor booleano que especifica se os carimbos de hora são incluídos em cada mensagem.</span><span class="sxs-lookup"><span data-stu-id="b09d4-131">A Boolean value that specifies whether time stamps are included in each message.</span></span> <span data-ttu-id="b09d4-132">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-132">The default is `true`.</span></span>|  
|`keyEntropyMode`|<span data-ttu-id="b09d4-133">Especifica a maneira que as chaves para mensagens de segurança são computadas.</span><span class="sxs-lookup"><span data-stu-id="b09d4-133">Specifies the way that keys for securing messages are computed.</span></span> <span data-ttu-id="b09d4-134">Chaves podem ser baseadas no material de chave do cliente, apenas o material de chave de serviço ou uma combinação de ambos.</span><span class="sxs-lookup"><span data-stu-id="b09d4-134">Keys can be based on the client key material only, on the service key material only or a combination of both.</span></span> <span data-ttu-id="b09d4-135">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="b09d4-135">Valid values are:</span></span><br /><br /> <span data-ttu-id="b09d4-136">-ClientEntropy: A chave de sessão baseada o cliente fornecido o material de chave.</span><span class="sxs-lookup"><span data-stu-id="b09d4-136">-   ClientEntropy: The session key is based off the client provided key material.</span></span><br /><span data-ttu-id="b09d4-137">-ServerEntropy: A chave de sessão baseia-se desativar o serviço fornecido material de chave.</span><span class="sxs-lookup"><span data-stu-id="b09d4-137">-   ServerEntropy: The session key is based off the service provided key material.</span></span><br /><span data-ttu-id="b09d4-138">-CombinedEntropy: A chave de sessão é baseado em cliente e o serviço fornecido material de chave.</span><span class="sxs-lookup"><span data-stu-id="b09d4-138">-   CombinedEntropy: The session key is based off the client and service provided keying material.</span></span><br /><br /> <span data-ttu-id="b09d4-139">O padrão é CombinedEntropy.</span><span class="sxs-lookup"><span data-stu-id="b09d4-139">The default is CombinedEntropy.</span></span><br /><br /> <span data-ttu-id="b09d4-140">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-140">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`messageProtectionOrder`|<span data-ttu-id="b09d4-141">Define a ordem na qual mensagem algoritmos de nível de segurança são aplicados à mensagem.</span><span class="sxs-lookup"><span data-stu-id="b09d4-141">Sets the order in which message level security algorithms are applied to the message.</span></span> <span data-ttu-id="b09d4-142">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b09d4-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b09d4-143">-SignBeforeEncrypt: Entrar pela primeira vez e, em seguida, criptografar.</span><span class="sxs-lookup"><span data-stu-id="b09d4-143">-   SignBeforeEncrypt: Sign first, then encrypt.</span></span><br /><span data-ttu-id="b09d4-144">-SignBeforeEncryptAndEncryptSignature: Assinar, criptografar e criptografar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b09d4-144">-   SignBeforeEncryptAndEncryptSignature: Sign, encrypt, and encrypt signature.</span></span><br /><span data-ttu-id="b09d4-145">-EncryptBeforeSign: Primeiro criptografar e assinar.</span><span class="sxs-lookup"><span data-stu-id="b09d4-145">-   EncryptBeforeSign: Encrypt first, then sign.</span></span><br /><br /> <span data-ttu-id="b09d4-146">SignBeforeEncryptAndEncryptSignature é o valor padrão com certificados mútuos 1.1 do WS-Security.</span><span class="sxs-lookup"><span data-stu-id="b09d4-146">SignBeforeEncryptAndEncryptSignature is the default value when using mutual certificates with WS-Security 1.1.</span></span>  <span data-ttu-id="b09d4-147">SignBeforeEncrypt é o valor padrão com o WS-Security 1.0.</span><span class="sxs-lookup"><span data-stu-id="b09d4-147">SignBeforeEncrypt is the default value with WS-Security 1.0.</span></span><br /><br /> <span data-ttu-id="b09d4-148">Esse atributo é do tipo <xref:System.ServiceModel.Security.MessageProtectionOrder>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-148">This attribute is of type <xref:System.ServiceModel.Security.MessageProtectionOrder>.</span></span>|  
|`messageSecurityVersion`|<span data-ttu-id="b09d4-149">Define a versão do WS-Security é usada.</span><span class="sxs-lookup"><span data-stu-id="b09d4-149">Sets the version of WS-Security that is used.</span></span> <span data-ttu-id="b09d4-150">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b09d4-150">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b09d4-151">-WSSecurityJan2004</span><span class="sxs-lookup"><span data-stu-id="b09d4-151">-   WSSecurityJan2004</span></span><br /><span data-ttu-id="b09d4-152">-WSSecurityXXX2005</span><span class="sxs-lookup"><span data-stu-id="b09d4-152">-   WSSecurityXXX2005</span></span><br /><br /> <span data-ttu-id="b09d4-153">O padrão é WSSecurityXXX2005.</span><span class="sxs-lookup"><span data-stu-id="b09d4-153">The default is WSSecurityXXX2005.</span></span> <span data-ttu-id="b09d4-154">Esse atributo é do tipo <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-154">This attribute is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|`requireDerivedKeys`|<span data-ttu-id="b09d4-155">Um valor booleano que especifica se as chaves podem ser derivadas das chaves de prova originais.</span><span class="sxs-lookup"><span data-stu-id="b09d4-155">A Boolean value that specifies whether keys can be derived from the original proof keys.</span></span> <span data-ttu-id="b09d4-156">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-156">The default is `true`.</span></span>|  
|`requireSecurityContextCancellation`|<span data-ttu-id="b09d4-157">Um valor booleano que especifica se o contexto de segurança deve ser cancelado e encerrado quando não é mais necessário.</span><span class="sxs-lookup"><span data-stu-id="b09d4-157">A Boolean value that specifies whether security context should be cancelled and terminated when it is no longer required.</span></span> <span data-ttu-id="b09d4-158">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-158">The default is `true`.</span></span>|  
|`requireSignatureConfirmation`|<span data-ttu-id="b09d4-159">Um valor booleano que especifica se a confirmação de assinatura de WS-Security está habilitada.</span><span class="sxs-lookup"><span data-stu-id="b09d4-159">A Boolean value that specifies whether WS-Security signature confirmation is enabled.</span></span> <span data-ttu-id="b09d4-160">Quando definido como `true`, assinaturas de mensagem são confirmadas pelo respondente.</span><span class="sxs-lookup"><span data-stu-id="b09d4-160">When set to `true`, message signatures are confirmed by the responder.</span></span> <span data-ttu-id="b09d4-161">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b09d4-161">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b09d4-162">Confirmação de assinatura é usada para confirmar que o serviço está respondendo no reconhecimento completo de uma solicitação.</span><span class="sxs-lookup"><span data-stu-id="b09d4-162">Signature confirmation is used to confirm that the service is responding in full awareness of a request.</span></span>|  
|`securityHeaderLayout`|<span data-ttu-id="b09d4-163">Especifica a ordenação dos elementos no cabeçalho de segurança.</span><span class="sxs-lookup"><span data-stu-id="b09d4-163">Specifies the ordering of the elements in security header.</span></span> <span data-ttu-id="b09d4-164">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="b09d4-164">Valid values are:</span></span><br /><br /> <span data-ttu-id="b09d4-165">-Estrito.</span><span class="sxs-lookup"><span data-stu-id="b09d4-165">-   Strict.</span></span> <span data-ttu-id="b09d4-166">Itens são adicionados ao cabeçalho de segurança de acordo com o princípio geral de "declarar antes do uso".</span><span class="sxs-lookup"><span data-stu-id="b09d4-166">Items are added to the security header according to the general principle of "declare before use".</span></span><br /><span data-ttu-id="b09d4-167">-Incerta.</span><span class="sxs-lookup"><span data-stu-id="b09d4-167">-   Lax.</span></span> <span data-ttu-id="b09d4-168">Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="b09d4-168">Items are added to the security header in any order that confirms to WSS: SOAP Message security.</span></span><br /><span data-ttu-id="b09d4-169">-LaxWithTimestampFirst.</span><span class="sxs-lookup"><span data-stu-id="b09d4-169">-   LaxWithTimestampFirst.</span></span> <span data-ttu-id="b09d4-170">Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP exceto que o primeiro elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.</span><span class="sxs-lookup"><span data-stu-id="b09d4-170">Items are added to the security header in any order that confirms to WSS: SOAP Message security except that the first element in the security header must be a wsse:Timestamp element.</span></span><br /><span data-ttu-id="b09d4-171">-LaxWithTimestampLast.</span><span class="sxs-lookup"><span data-stu-id="b09d4-171">-   LaxWithTimestampLast.</span></span> <span data-ttu-id="b09d4-172">Itens são adicionados ao cabeçalho de segurança em qualquer ordem que confirmam WSS: segurança de mensagem SOAP exceto que o último elemento no cabeçalho de segurança deve ser um elemento wsse:Timestamp.</span><span class="sxs-lookup"><span data-stu-id="b09d4-172">Items are added to the security header in any order that confirms to WSS: SOAP Message security except that the last element in the security header must be a wsse:Timestamp element.</span></span><br /><br /> <span data-ttu-id="b09d4-173">O padrão é estrito.</span><span class="sxs-lookup"><span data-stu-id="b09d4-173">The default is Strict.</span></span><br /><br /> <span data-ttu-id="b09d4-174">Esse elemento é do tipo <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-174">This element is of type <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b09d4-175">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b09d4-175">Child Elements</span></span>  
  
|<span data-ttu-id="b09d4-176">Elemento</span><span class="sxs-lookup"><span data-stu-id="b09d4-176">Element</span></span>|<span data-ttu-id="b09d4-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09d4-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b09d4-178">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b09d4-178">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="b09d4-179">Especifica um token emitido atual.</span><span class="sxs-lookup"><span data-stu-id="b09d4-179">Specifies a current issued token.</span></span> <span data-ttu-id="b09d4-180">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-180">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.</span></span>|  
|[<span data-ttu-id="b09d4-181">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="b09d4-181">\<localClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|<span data-ttu-id="b09d4-182">Especifica as configurações de segurança de um cliente local para esta associação.</span><span class="sxs-lookup"><span data-stu-id="b09d4-182">Specifies the security settings of a local client for this binding.</span></span> <span data-ttu-id="b09d4-183">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-183">This element is of type <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.</span></span>|  
|[<span data-ttu-id="b09d4-184">\<localServiceSettings ></span><span class="sxs-lookup"><span data-stu-id="b09d4-184">\<localServiceSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|<span data-ttu-id="b09d4-185">Especifica as configurações de segurança de um serviço local para esta associação.</span><span class="sxs-lookup"><span data-stu-id="b09d4-185">Specifies the security settings of a local service for this binding.</span></span> <span data-ttu-id="b09d4-186">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.</span><span class="sxs-lookup"><span data-stu-id="b09d4-186">This element is of type <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b09d4-187">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b09d4-187">Parent Elements</span></span>  
  
|<span data-ttu-id="b09d4-188">Elemento</span><span class="sxs-lookup"><span data-stu-id="b09d4-188">Element</span></span>|<span data-ttu-id="b09d4-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="b09d4-189">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b09d4-190">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="b09d4-190">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="b09d4-191">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b09d4-191">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b09d4-192">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b09d4-192">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <span data-ttu-id="b09d4-193">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="b09d4-193">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="b09d4-194">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b09d4-194">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b09d4-195">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="b09d4-195">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b09d4-196">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b09d4-196">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b09d4-197">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b09d4-197">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="b09d4-198">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="b09d4-198">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)