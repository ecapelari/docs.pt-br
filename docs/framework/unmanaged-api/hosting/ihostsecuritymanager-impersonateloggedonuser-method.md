---
title: "Método IHostSecurityManager::ImpersonateLoggedOnUser"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.ImpersonateLoggedOnUser
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c5956dcad6908f0117de7f5ff0c6632ad3bb925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="22667-102">Método IHostSecurityManager::ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="22667-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="22667-103">Solicitações que código ser executado usando as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="22667-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22667-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22667-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22667-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22667-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="22667-106">[in] Um token que representa as credenciais do usuário para ser representado.</span><span class="sxs-lookup"><span data-stu-id="22667-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22667-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="22667-107">Return Value</span></span>  
  
|<span data-ttu-id="22667-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22667-108">HRESULT</span></span>|<span data-ttu-id="22667-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="22667-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22667-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="22667-110">S_OK</span></span>|<span data-ttu-id="22667-111">`ImpersonateLoggedOnUser`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="22667-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="22667-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22667-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22667-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="22667-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22667-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22667-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22667-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="22667-115">The call timed out.</span></span>|  
|<span data-ttu-id="22667-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22667-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22667-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="22667-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22667-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22667-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22667-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="22667-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22667-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22667-120">E_FAIL</span></span>|<span data-ttu-id="22667-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="22667-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22667-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="22667-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22667-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="22667-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22667-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="22667-124">Remarks</span></span>  
 <span data-ttu-id="22667-125">Chamar `LogonUser` ou uma função relacionada do Win32 para obter um identificador para as credenciais da identidade do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="22667-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="22667-126">O `HANDLE` tipo não é compatível com o COM, ou seja, seu tamanho é específico para um sistema operacional e requer empacotamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="22667-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="22667-127">Portanto, esse token é para uso somente dentro do processo, entre o host e o CLR.</span><span class="sxs-lookup"><span data-stu-id="22667-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22667-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22667-128">Requirements</span></span>  
 <span data-ttu-id="22667-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22667-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22667-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22667-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22667-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="22667-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22667-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22667-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22667-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22667-133">See Also</span></span>  
 [<span data-ttu-id="22667-134">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="22667-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="22667-135">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="22667-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="22667-136">Método RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="22667-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)