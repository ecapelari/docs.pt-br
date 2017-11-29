---
title: "Método ICorProfilerInfo::SetEnterLeaveFunctionHooks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2bf897ce41e2d9a8b4c7b9eeb4053ea0e9ad951
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="36a29-102">Método ICorProfilerInfo::SetEnterLeaveFunctionHooks</span><span class="sxs-lookup"><span data-stu-id="36a29-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="36a29-103">Especifica as funções implementada pelo criador de perfil a ser chamado no "entrar", "Sair" e "tailcall" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="36a29-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36a29-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36a29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36a29-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="36a29-106">[in] Um ponteiro para a implementação para ser usado como o [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="36a29-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="36a29-107">[in] Um ponteiro para a implementação para ser usado como o [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="36a29-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="36a29-108">[in] Um ponteiro para a implementação para ser usado como o [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="36a29-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36a29-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="36a29-109">Remarks</span></span>  
 <span data-ttu-id="36a29-110">No .NET Framework versão 1.0, cada ponteiro de função pode ser nulo para desabilitar o retorno de chamada correspondente.</span><span class="sxs-lookup"><span data-stu-id="36a29-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="36a29-111">Apenas um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="36a29-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="36a29-112">Portanto, se um criador de perfil chama ambos `SetEnterLeaveFunctionHooks` e [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), em seguida, `SetEnterLeaveFunctionHooks2` terá precedência.</span><span class="sxs-lookup"><span data-stu-id="36a29-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="36a29-113">O `SetEnterLeaveFunctionHooks` método pode ser chamado somente a partir do criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="36a29-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36a29-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36a29-114">Requirements</span></span>  
 <span data-ttu-id="36a29-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36a29-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36a29-116">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36a29-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36a29-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36a29-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36a29-118">**Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36a29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a29-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36a29-119">See Also</span></span>  
 [<span data-ttu-id="36a29-120">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="36a29-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)