---
title: "Função StrongNameSignatureVerification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerification
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerification
helpviewer_keywords: StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2c04aba5b774b299e26be8dc532b894b6c6fad5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="26176-102">Função StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="26176-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="26176-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="26176-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="26176-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="26176-104">This function has been deprecated.</span></span> <span data-ttu-id="26176-105">Use o [Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="26176-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26176-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26176-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26176-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26176-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="26176-108">[in] O caminho para o executável (. dll ou .exe) arquivo portátil para o assembly verificar.</span><span class="sxs-lookup"><span data-stu-id="26176-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="26176-109">[in] Sinalizadores para modificar o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="26176-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="26176-110">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="26176-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="26176-111">`SN_INFLAG_FORCE_VER`(0x00000001) - força a verificação mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="26176-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="26176-112">`SN_INFLAG_INSTALL`(0x00000002) - Especifica que esta é a primeira vez que o manifesto é verificado.</span><span class="sxs-lookup"><span data-stu-id="26176-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="26176-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) - Especifica que o cache permite acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="26176-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="26176-114">`SN_INFLAG_USER_ACCESS`(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="26176-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="26176-115">`SN_INFLAG_ALL_ACCESS`(0x00000010) - Especifica que o cache não fornecem nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="26176-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="26176-116">`SN_INFLAG_RUNTIME`(0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="26176-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="26176-117">[out] Sinalizadores que indica se a assinatura de nome forte foi verificada.</span><span class="sxs-lookup"><span data-stu-id="26176-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="26176-118">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="26176-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="26176-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - Este valor é definido como `false` para especificar se a verificação foi bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="26176-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26176-120">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26176-120">Return Value</span></span>  
 <span data-ttu-id="26176-121">`true`Se a verificação for bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="26176-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26176-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26176-122">Requirements</span></span>  
 <span data-ttu-id="26176-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26176-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26176-124">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="26176-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="26176-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="26176-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26176-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26176-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26176-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26176-127">See Also</span></span>  
 [<span data-ttu-id="26176-128">Método StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="26176-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="26176-129">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="26176-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="26176-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="26176-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)