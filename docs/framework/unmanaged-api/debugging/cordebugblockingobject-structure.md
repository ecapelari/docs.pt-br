---
title: Estrutura CorDebugBlockingObject
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingObject Structure
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingObject
helpviewer_keywords: CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c47735565c960c2600f7274d0d59d5a6ec6c178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="ca537-102">Estrutura CorDebugBlockingObject</span><span class="sxs-lookup"><span data-stu-id="ca537-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="ca537-103">Define um objeto que está bloqueando um thread e o motivo específico que o thread está bloqueado.</span><span class="sxs-lookup"><span data-stu-id="ca537-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca537-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca537-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="ca537-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ca537-105">Members</span></span>  
  
|<span data-ttu-id="ca537-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ca537-106">Member</span></span>|<span data-ttu-id="ca537-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca537-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="ca537-108">O objeto no qual o thread está bloqueando.</span><span class="sxs-lookup"><span data-stu-id="ca537-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="ca537-109">Esse objeto é válido apenas para a duração do atual estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="ca537-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="ca537-110">Se dois threads estão bloqueando no mesmo objeto no mesmo estado sincronizado, você pode esperar que o [Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) método para retornar o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="ca537-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="ca537-111">No entanto, as interfaces podem ou não ser equivalente do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="ca537-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="ca537-112">O número de milissegundos antes da operação de bloqueio atingirá o tempo limite ou o valor infinito, o que indica que ele não terá tempo limite. O valor de tempo limite Especifica o comprimento total de tempo para a operação de bloqueio, não o tempo que ainda está pendente.</span><span class="sxs-lookup"><span data-stu-id="ca537-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="ca537-113">O motivo que o thread está bloqueado neste objeto.</span><span class="sxs-lookup"><span data-stu-id="ca537-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca537-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca537-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca537-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca537-115">Requirements</span></span>  
 <span data-ttu-id="ca537-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca537-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca537-117">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ca537-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ca537-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca537-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca537-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca537-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca537-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca537-120">See Also</span></span>  
 [<span data-ttu-id="ca537-121">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="ca537-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ca537-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="ca537-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)