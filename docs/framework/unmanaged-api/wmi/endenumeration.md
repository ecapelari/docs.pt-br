---
title: "Função EndEnumeration (referência de API não gerenciada)"
description: "A função EndEnumeration encerra uma enumeração."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="e0b2c-103">Função EndEnumeration</span><span class="sxs-lookup"><span data-stu-id="e0b2c-103">EndEnumeration function</span></span>
<span data-ttu-id="e0b2c-104">Encerra uma sequência de enumeração iniciada com uma chamada para o [BeginEnumeration função](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2c-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e0b2c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0b2c-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e0b2c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0b2c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e0b2c-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e0b2c-108">[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="e0b2c-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e0b2c-109">Return value</span></span>

<span data-ttu-id="e0b2c-110">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="e0b2c-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e0b2c-111">Constante</span><span class="sxs-lookup"><span data-stu-id="e0b2c-111">Constant</span></span>  |<span data-ttu-id="e0b2c-112">Valor</span><span class="sxs-lookup"><span data-stu-id="e0b2c-112">Value</span></span>  |<span data-ttu-id="e0b2c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0b2c-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e0b2c-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e0b2c-114">0x80041001</span></span> | <span data-ttu-id="e0b2c-115">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e0b2c-116">0</span><span class="sxs-lookup"><span data-stu-id="e0b2c-116">0</span></span> | <span data-ttu-id="e0b2c-117">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e0b2c-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0b2c-118">Remarks</span></span>

<span data-ttu-id="e0b2c-119">Essa função encapsula uma chamada para o [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) método.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="e0b2c-120">Uma chamada para o `EndEnumeration` função não é necessária, mas é recomendado, pois ele libera os recursos associados com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="e0b2c-121">No entanto, os resoruces são desalocados automaticamente quando a próxima enumeração for iniciada ou o objeto é liberado.</span><span class="sxs-lookup"><span data-stu-id="e0b2c-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0b2c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0b2c-122">Requirements</span></span>  
 <span data-ttu-id="e0b2c-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b2c-124">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e0b2c-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e0b2c-125">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b2c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b2c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0b2c-126">See also</span></span>  
[<span data-ttu-id="e0b2c-127">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="e0b2c-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)