---
title: Executando um comando
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e09685c92652e1fcac2486031ecb49bf8399be59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="executing-a-command"></a><span data-ttu-id="4d403-102">Executando um comando</span><span class="sxs-lookup"><span data-stu-id="4d403-102">Executing a Command</span></span>
<span data-ttu-id="4d403-103">Cada provedor de dados do .NET Framework incluído com o .NET Framework tem seu próprio objeto de comando que herda de <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="4d403-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="4d403-104">O Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbCommand>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlCommand>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcCommand> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="4d403-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="4d403-105">Cada um desses objetos expõe métodos para executar comandos com base no tipo de comando e do valor de retorno desejado, como descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d403-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="4d403-106">Comando</span><span class="sxs-lookup"><span data-stu-id="4d403-106">Command</span></span>|<span data-ttu-id="4d403-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4d403-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="4d403-108">Retorna um objeto `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="4d403-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="4d403-109">Retorna um único valor escalar.</span><span class="sxs-lookup"><span data-stu-id="4d403-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="4d403-110">Executa um comando que não retorna nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="4d403-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="4d403-111">Retorna um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4d403-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4d403-112">Disponível somente para um objeto do `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="4d403-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="4d403-113">Cada objeto de comando fortemente tipado também dá suporte a uma enumeração de <xref:System.Data.CommandType> que especifica como uma cadeia de caracteres de comando é interpretada, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d403-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="4d403-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="4d403-114">CommandType</span></span>|<span data-ttu-id="4d403-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d403-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="4d403-116">Um comando SQL que define as instruções a serem executado na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4d403-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="4d403-117">O nome do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="4d403-117">The name of the stored procedure.</span></span> <span data-ttu-id="4d403-118">Você pode usar a propriedade `Parameters` de um comando para acessar os parâmetros de entrada e saída e os valores de retorno, independentemente do método `Execute` chamado.</span><span class="sxs-lookup"><span data-stu-id="4d403-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="4d403-119">Ao usar `ExecuteReader`, os valores de retorno e os parâmetros de saída não estarão acessíveis até que o `DataReader` seja fechado.</span><span class="sxs-lookup"><span data-stu-id="4d403-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="4d403-120">O nome de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="4d403-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d403-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d403-121">Example</span></span>  
 <span data-ttu-id="4d403-122">O código de exemplo a seguir demonstra como criar um objeto <xref:System.Data.SqlClient.SqlCommand> para executar um procedimento armazenado definindo suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="4d403-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="4d403-123">Um objeto <xref:System.Data.SqlClient.SqlParameter> é usado para especificar o parâmetro de entrada para o procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="4d403-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="4d403-124">O comando é executado usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> e a saída do <xref:System.Data.SqlClient.SqlDataReader> é exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4d403-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="4d403-125">Comandos de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="4d403-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="4d403-126">O provedor de dados .NET Framework para SQL Server adiciona contadores de desempenho para permitir que você detecte os problemas intermitentes relacionados às execuções de comando com falha.</span><span class="sxs-lookup"><span data-stu-id="4d403-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="4d403-127">Para obter mais informações, consulte [contadores de desempenho](../../../../docs/framework/data/adonet/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="4d403-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d403-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d403-128">See Also</span></span>  
 [<span data-ttu-id="4d403-129">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d403-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="4d403-130">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="4d403-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="4d403-131">Trabalhando com DataReaders</span><span class="sxs-lookup"><span data-stu-id="4d403-131">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 <span data-ttu-id="4d403-132">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4d403-132">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>