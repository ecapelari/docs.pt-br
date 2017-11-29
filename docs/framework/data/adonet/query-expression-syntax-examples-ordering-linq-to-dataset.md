---
title: "Exemplos de sintaxe da expressão de consulta: Ordenação (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 179d9936f08e8587ef159a232292ff73ea86cd4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="cfa76-102">Exemplos de sintaxe da expressão de consulta: Ordenação (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="cfa76-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="cfa76-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, e métodos de <xref:System.Linq.Enumerable.ThenByDescending%2A> para ver <xref:System.Data.DataSet> e para ordenar os resultados usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="cfa76-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="cfa76-104">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="cfa76-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="cfa76-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cfa76-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="cfa76-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="cfa76-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="cfa76-107">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="cfa76-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="cfa76-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="cfa76-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="cfa76-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfa76-109">Example</span></span>  
 <span data-ttu-id="cfa76-110">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> para retornar uma lista de contatos ordenados por sobrenome.</span><span class="sxs-lookup"><span data-stu-id="cfa76-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="cfa76-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfa76-111">Example</span></span>  
 <span data-ttu-id="cfa76-112">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> para classificar uma lista de contatos pelo comprimento do sobrenome.</span><span class="sxs-lookup"><span data-stu-id="cfa76-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="cfa76-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="cfa76-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="cfa76-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfa76-114">Example</span></span>  
 <span data-ttu-id="cfa76-115">Este exemplo usa `orderby… descending` (`Order By … Descending`), que é equivalente ao método de <xref:System.Linq.Enumerable.OrderByDescending%2A> , para classificar a tabela de preços de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="cfa76-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="cfa76-116">Inverso</span><span class="sxs-lookup"><span data-stu-id="cfa76-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="cfa76-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfa76-117">Example</span></span>  
 <span data-ttu-id="cfa76-118">Este exemplo usa <xref:System.Linq.Enumerable.Reverse%2A> para criar uma lista de pedidos onde `OrderDate` for anterior do 20 de fevereiro de 2002.</span><span class="sxs-lookup"><span data-stu-id="cfa76-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="cfa76-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="cfa76-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="cfa76-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfa76-120">Example</span></span>  
 <span data-ttu-id="cfa76-121">Este exemplo usa `OrderBy… Descending` , que é equivalente ao método de <xref:System.Linq.Enumerable.ThenByDescending%2A> , para classificar uma lista de produtos, principalmente por nome e em seguida pelo custo da tabela, o mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="cfa76-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="cfa76-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfa76-122">See Also</span></span>  
 [<span data-ttu-id="cfa76-123">Carregar dados em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="cfa76-123">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="cfa76-124">LINQ para exemplos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="cfa76-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="cfa76-125">Visão Geral de Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="cfa76-125">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)