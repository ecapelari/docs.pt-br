---
title: "Chamando funções em consultas no LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="77465-102">Chamando funções em consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="77465-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="77465-103">Os tópicos nesta seção descrevem como chamar funções em consultas LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="77465-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="77465-104">As classes <xref:System.Data.Objects.EntityFunctions> e <xref:System.Data.Objects.SqlClient.SqlFunctions> fornecem acesso às funções canônicas e de banco de dados como parte do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="77465-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="77465-105">Para obter mais informações, consulte [como: chamar funções canônicas](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) e [como: chamar funções de banco de dados](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="77465-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="77465-106">O processo para chamar uma função personalizada exige três etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="77465-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="77465-107">Defina uma função no modelo conceitual ou declare uma função no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="77465-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="77465-108">Adicione um método ao seu aplicativo e mapeie-o para a função no modelo com um <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77465-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="77465-109">Chame a função em uma consulta LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="77465-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="77465-110">Para obter mais informações, consulte os tópicos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="77465-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77465-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="77465-111">In This Section</span></span>  
 [<span data-ttu-id="77465-112">Como: chamar funções canônicas</span><span class="sxs-lookup"><span data-stu-id="77465-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="77465-113">Como: chamar funções de banco de dados</span><span class="sxs-lookup"><span data-stu-id="77465-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="77465-114">Como: chamar funções de banco de dados personalizado</span><span class="sxs-lookup"><span data-stu-id="77465-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="77465-115">Como: chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="77465-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="77465-116">Como: chamar funções definidas como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="77465-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="77465-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77465-117">See Also</span></span>  
 [<span data-ttu-id="77465-118">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="77465-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 <span data-ttu-id="77465-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) (Funções canônicas)</span><span class="sxs-lookup"><span data-stu-id="77465-119">[Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)</span></span>  
 [<span data-ttu-id="77465-120">Visão geral do arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="77465-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="77465-121">Como: definir funções personalizadas no modelo conceitual</span><span class="sxs-lookup"><span data-stu-id="77465-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)