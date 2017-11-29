---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: be98c93452c9c7a37ecad5b03f5160ea08f2c82e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="9c8c5-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="9c8c5-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="9c8c5-103">Fornece configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="9c8c5-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-104">\<system.identityModel></span></span>  
<span data-ttu-id="9c8c5-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9c8c5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9c8c5-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c8c5-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c8c5-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c8c5-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c8c5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c8c5-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c8c5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c8c5-111">Attributes</span></span>  
  
|<span data-ttu-id="9c8c5-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c8c5-112">Attribute</span></span>|<span data-ttu-id="9c8c5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c8c5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c8c5-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="9c8c5-114">saveBootstrapContext</span></span>|<span data-ttu-id="9c8c5-115">Especifica se os tokens de inicialização devem ser incluídos no token de sessão.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="9c8c5-116">O valor também pode ser definido em uma coleção de manipulador de token, definindo o `saveBootstrapContext` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="9c8c5-117">Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="9c8c5-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="9c8c5-118">maximumClockSkew</span></span>|<span data-ttu-id="9c8c5-119">Um <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="9c8c5-120">Controla a distorção máxima permitida do relógio ao executar operações de detecção de hora, como validar o tempo de expiração de uma sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="9c8c5-121">O padrão é 5 minutos, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="9c8c5-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="9c8c5-122">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c8c5-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="9c8c5-123">O máximo do relógio também pode ser definido no nível de serviço, definindo o `maximumClockSkew` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="9c8c5-124">Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c8c5-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c8c5-125">Child Elements</span></span>  
  
|<span data-ttu-id="9c8c5-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c8c5-126">Element</span></span>|<span data-ttu-id="9c8c5-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c8c5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c8c5-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="9c8c5-129">Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="9c8c5-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-130">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-131">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="9c8c5-132">Registra os caches usados para detecção de reprodução de token e tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="9c8c5-133">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="9c8c5-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-134">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="9c8c5-136">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="9c8c5-137">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="9c8c5-138">Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validados.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="9c8c5-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-139">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="9c8c5-141">Configura o registro de nome de emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9c8c5-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-142">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="9c8c5-144">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9c8c5-145">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="9c8c5-146">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-146">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="9c8c5-148">Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9c8c5-149">O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="9c8c5-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-150">Optional.</span></span>|  
|[<span data-ttu-id="9c8c5-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="9c8c5-152">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="9c8c5-153">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="9c8c5-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c8c5-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c8c5-155">Parent Elements</span></span>  
  
|<span data-ttu-id="9c8c5-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c8c5-156">Element</span></span>|<span data-ttu-id="9c8c5-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c8c5-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c8c5-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="9c8c5-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="9c8c5-159">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c8c5-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c8c5-160">Remarks</span></span>  
 <span data-ttu-id="9c8c5-161">Esta seção fornece valores de propriedade para um <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objeto.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="9c8c5-162">As configurações definidas nesta seção substituem aquelas configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="9c8c5-163">Algumas dessas configurações, por sua vez, podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9c8c5-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c8c5-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c8c5-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```