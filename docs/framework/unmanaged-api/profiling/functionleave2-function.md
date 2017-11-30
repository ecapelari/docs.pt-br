---
title: "Função FunctionLeave2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave2
helpviewer_keywords: FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c2dd85e23a54a20920e30e22bc91f88a813be39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave2-function"></a><span data-ttu-id="8317f-102">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="8317f-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="8317f-103">Notifica o criador de perfil que uma função está prestes a retornar ao chamador e fornece informações sobre a pilha quadro e função de valor retornado.</span><span class="sxs-lookup"><span data-stu-id="8317f-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8317f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8317f-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8317f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8317f-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="8317f-106">[in] O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="8317f-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="8317f-107">[in] O identificador de função remapeados, o criador de perfil especificado anteriormente por meio de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="8317f-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="8317f-108">[in] Um `COR_PRF_FRAME_INFO` valor que aponta para obter informações sobre o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="8317f-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="8317f-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8317f-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="8317f-110">[in] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estrutura que especifica o local de memória do valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="8317f-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="8317f-111">Para acessar informações do valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="8317f-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="8317f-112">O criador de perfil pode usar o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="8317f-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8317f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8317f-113">Remarks</span></span>  
 <span data-ttu-id="8317f-114">Os valores da `func` e `retvalRange` parâmetros não são válidos após o `FunctionLeave2` função retorna porque os valores podem ser alterados ou ser destruídos.</span><span class="sxs-lookup"><span data-stu-id="8317f-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="8317f-115">O `FunctionLeave2` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="8317f-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="8317f-116">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8317f-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8317f-117">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="8317f-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="8317f-118">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="8317f-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="8317f-119">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="8317f-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8317f-120">A implementação de `FunctionLeave2` não devem bloquear porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8317f-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8317f-121">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8317f-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8317f-122">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionLeave2` retorna.</span><span class="sxs-lookup"><span data-stu-id="8317f-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="8317f-123">Além disso, o `FunctionLeave2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8317f-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8317f-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8317f-124">Requirements</span></span>  
 <span data-ttu-id="8317f-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8317f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8317f-126">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="8317f-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8317f-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8317f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8317f-128">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8317f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8317f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8317f-129">See Also</span></span>  
 [<span data-ttu-id="8317f-130">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="8317f-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="8317f-131">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="8317f-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="8317f-132">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="8317f-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="8317f-133">Funções estáticas globais de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8317f-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)