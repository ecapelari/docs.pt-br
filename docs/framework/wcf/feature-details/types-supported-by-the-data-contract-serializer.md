---
title: Tipos com suporte fornecido pelo serializador de contrato de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 492a82de21c95fe08c361274af2d49e2531535b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="types-supported-by-the-data-contract-serializer"></a><span data-ttu-id="48839-102">Tipos com suporte fornecido pelo serializador de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="48839-102">Types Supported by the Data Contract Serializer</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="48839-103">usa o <xref:System.Runtime.Serialization.DataContractSerializer> como seu mecanismo de serialização padrão para converter dados em XML e converter XML novamente nos dados.</span><span class="sxs-lookup"><span data-stu-id="48839-103"> uses the <xref:System.Runtime.Serialization.DataContractSerializer> as its default serialization engine to convert data into XML and to convert XML back into data.</span></span> <span data-ttu-id="48839-104">O <xref:System.Runtime.Serialization.DataContractSerializer> foi projetado para serializar *contrato de dados* tipos.</span><span class="sxs-lookup"><span data-stu-id="48839-104">The <xref:System.Runtime.Serialization.DataContractSerializer> is designed to serialize *data contract* types.</span></span> <span data-ttu-id="48839-105">No entanto, ele oferece suporte a muitos outros tipos, o que podem ser considerados como tendo um contrato de dados implícita.</span><span class="sxs-lookup"><span data-stu-id="48839-105">However, it supports many other types, which can be thought of as having an implicit data contract.</span></span> <span data-ttu-id="48839-106">O exemplo a seguir é uma lista completa de tipos que pode ser serializado:</span><span class="sxs-lookup"><span data-stu-id="48839-106">The following is a complete list of types that can be serialized:</span></span>  
  
-   <span data-ttu-id="48839-107">Todos os tipos visíveis publicamente que tem um construtor que não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="48839-107">All publicly visible types that have a constructor that does not have parameters.</span></span>  
  
-   <span data-ttu-id="48839-108">Tipos de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="48839-108">Data contract types.</span></span> <span data-ttu-id="48839-109">Estes são os tipos para os quais o <xref:System.Runtime.Serialization.DataContractAttribute> atributo foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="48839-109">These are types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has been applied.</span></span> <span data-ttu-id="48839-110">Novos tipos personalizados que representam objetos de negócios devem normalmente ser criados como dados de tipos de contrato.</span><span class="sxs-lookup"><span data-stu-id="48839-110">New custom types that represent business objects should normally be created as data contract types.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="48839-111">[Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) e [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="48839-111"> [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) and [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
-   <span data-ttu-id="48839-112">Tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="48839-112">Collection types.</span></span> <span data-ttu-id="48839-113">Estes são os tipos que representam as listas de dados.</span><span class="sxs-lookup"><span data-stu-id="48839-113">These are types that represent lists of data.</span></span> <span data-ttu-id="48839-114">Eles podem ser matrizes regulares de tipos ou tipos de coleção, como <xref:System.Collections.ArrayList> e <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="48839-114">These can be regular arrays of types, or collection types, such as <xref:System.Collections.ArrayList> and <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="48839-115">O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo pode ser usado para personalizar a serialização desses tipos, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="48839-115">The <xref:System.Runtime.Serialization.CollectionDataContractAttribute> attribute can be used to customize the serialization of these types, but is not required.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="48839-116">[Tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="48839-116"> [Collection Types in Data Contracts](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).</span></span>  
  
-   <span data-ttu-id="48839-117">Tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="48839-117">Enumeration types.</span></span> <span data-ttu-id="48839-118">Enumerações, incluindo enumerações de sinalizador são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="48839-118">Enumerations, including flag enumerations, are serializable.</span></span> <span data-ttu-id="48839-119">Opcionalmente, os tipos de enumeração podem ser marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> de atributo, caso em que cada membro que participa de serialização deve ser marcado com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="48839-119">Optionally, enumeration types can be marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, in which case every member that participates in serialization must be marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="48839-120">Membros que não são marcados como não são serializados.</span><span class="sxs-lookup"><span data-stu-id="48839-120">Members that are not marked are not serialized.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="48839-121">[Tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="48839-121"> [Enumeration Types in Data Contracts](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).</span></span>  
  
-   <span data-ttu-id="48839-122">Tipos primitivos do .NET framework.</span><span class="sxs-lookup"><span data-stu-id="48839-122">.NET Framework primitive types.</span></span> <span data-ttu-id="48839-123">Os seguintes tipos criados no .NET Framework podem todos ser serializados e são considerados tipos primitivos: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, e <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="48839-123">The following types built into the .NET Framework can all be serialized and are considered to be primitive types: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, and <xref:System.String>.</span></span>  
  
-   <span data-ttu-id="48839-124">Outros tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="48839-124">Other primitive types.</span></span> <span data-ttu-id="48839-125">Esses tipos não são tipos primitivos do .NET Framework, mas são tratados como primitivos no formato XML serializado.</span><span class="sxs-lookup"><span data-stu-id="48839-125">These types are not primitives in the .NET Framework but are treated as primitives in the serialized XML form.</span></span> <span data-ttu-id="48839-126">Esses tipos são <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>e matrizes de <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="48839-126">These types are <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>, and arrays of <xref:System.Byte>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48839-127">Ao contrário de outros tipos primitivos, <xref:System.DateTimeOffset> não é um tipo conhecido por padrão.</span><span class="sxs-lookup"><span data-stu-id="48839-127">Unlike other primitive types, <xref:System.DateTimeOffset> is not a known type by default.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="48839-128">[Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).</span><span class="sxs-lookup"><span data-stu-id="48839-128"> [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).</span></span>  
  
-   <span data-ttu-id="48839-129">Tipos marcados com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="48839-129">Types marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="48839-130">Muitos tipos incluídos no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] primavera de biblioteca de classe base nessa categoria.</span><span class="sxs-lookup"><span data-stu-id="48839-130">Many types included in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] base class library fall into this category.</span></span> <span data-ttu-id="48839-131">O <xref:System.Runtime.Serialization.DataContractSerializer> totalmente dá suporte a este modelo de programação de serialização que foi usado pela comunicação remota do .NET Framework, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, incluindo suporte para o <xref:System.Runtime.Serialization.ISerializable> interface.</span><span class="sxs-lookup"><span data-stu-id="48839-131">The <xref:System.Runtime.Serialization.DataContractSerializer> fully supports this serialization programming model that was used by .NET Framework remoting, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, including support for the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
-   <span data-ttu-id="48839-132">Tipos que representam bruto XML ou tipos que representam [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="48839-132">Types that represent raw XML or types that represent [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] relational data.</span></span> <span data-ttu-id="48839-133">O <xref:System.Xml.XmlElement> e matriz de <xref:System.Xml.XmlNode> tipos têm suporte como uma forma de representar o XML diretamente.</span><span class="sxs-lookup"><span data-stu-id="48839-133">The <xref:System.Xml.XmlElement> and array of <xref:System.Xml.XmlNode> types are supported as a way of representing XML directly.</span></span> <span data-ttu-id="48839-134">Além disso, tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface têm suporte, incluindo as relacionadas <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo e o <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement> tipos.</span><span class="sxs-lookup"><span data-stu-id="48839-134">Additionally, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface are supported, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types.</span></span> <span data-ttu-id="48839-135">O [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> tipo e o <xref:System.Data.DataSet> tipo (bem como suas classes derivadas tipados) todos implementam o <xref:System.Xml.Serialization.IXmlSerializable> de interface e, portanto, se encaixam nesta categoria.</span><span class="sxs-lookup"><span data-stu-id="48839-135">The [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<xref:System.Data.DataTable> type and the <xref:System.Data.DataSet> type (as well as its typed derived classes) all implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, and therefore fit into this category.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="48839-136">[XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="48839-136"> [XML and ADO.NET Types in Data Contracts](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).</span></span>  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a><span data-ttu-id="48839-137">Modo de confiança de limitações de uso de certos tipos parcial</span><span class="sxs-lookup"><span data-stu-id="48839-137">Limitations of Using Certain Types in Partial Trust Mode</span></span>  
 <span data-ttu-id="48839-138">A seguir está uma lista de limitações ao usar determinados tipos de cenários de modo de confiança parcial:</span><span class="sxs-lookup"><span data-stu-id="48839-138">The following is a list of limitations when using certain types in partial trust mode scenarios:</span></span>  
  
-   <span data-ttu-id="48839-139">Para serializar ou desserializar um tipo que implementa <xref:System.Runtime.Serialization.ISerializable> código parcialmente confiável usando o <xref:System.Runtime.Serialization.DataContractSerializer> requer o <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> e <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> permissões.</span><span class="sxs-lookup"><span data-stu-id="48839-139">To serialize or deserialize a type that implements <xref:System.Runtime.Serialization.ISerializable> in partially-trusted code using the <xref:System.Runtime.Serialization.DataContractSerializer> requires the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> and <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> permissions.</span></span>  
  
-   <span data-ttu-id="48839-140">Ao executar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de código em [confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md) modo, a serialização e desserialização de `readonly` campos (ambos `public` e `private`) não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="48839-140">When running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] code in [Partial Trust](../../../../docs/framework/wcf/feature-details/partial-trust.md) mode, the serialization and deserialization of `readonly` fields (both `public` and `private`) is not supported.</span></span> <span data-ttu-id="48839-141">Isso ocorre porque o IL gerado não é verificável e, portanto, requer permissões elevadas.</span><span class="sxs-lookup"><span data-stu-id="48839-141">This is because the generated IL is unverifiable and therefore requires elevated permissions.</span></span>  
  
-   <span data-ttu-id="48839-142">Tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> têm suporte em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="48839-142">Both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported in a partial trust environment.</span></span> <span data-ttu-id="48839-143">No entanto, usar o <xref:System.Runtime.Serialization.DataContractSerializer> está sujeita às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="48839-143">However, use of the <xref:System.Runtime.Serialization.DataContractSerializer> is subject to the following conditions:</span></span>  
  
    -   <span data-ttu-id="48839-144">Todos os serializável `[DataContract]` tipos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="48839-144">All serializable `[DataContract]` types must be public.</span></span>  
  
    -   <span data-ttu-id="48839-145">Todos os serializável `[DataMember]` campos ou propriedades em um `[DataContract]` tipo deve ser público e leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="48839-145">All serializable `[DataMember]` fields or properties in a `[DataContract]` type must be public and read/write.</span></span> <span data-ttu-id="48839-146">A serialização e desserialização de `readonly` campos não é suportado quando executando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em um aplicativo parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="48839-146">The serialization and deserialization of `readonly` fields is not supported when running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in a partially-trusted application.</span></span>  
  
    -   <span data-ttu-id="48839-147">O `[Serializable]` / `ISerializable]` não há suporte para o modelo de programação em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="48839-147">The `[Serializable]`/`ISerializable]` programming model is not supported in a partial trust environment.</span></span>  
  
    -   <span data-ttu-id="48839-148">Conhecido tipos devem ser especificados no código ou configuração de nível de máquina (`Machine.config`).</span><span class="sxs-lookup"><span data-stu-id="48839-148">Known types must be specified in code or machine-level configuration (`Machine.config`).</span></span> <span data-ttu-id="48839-149">Tipos conhecidos não podem ser especificados na configuração de nível de aplicativo por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="48839-149">Known types cannot be specified in application-level configuration for security reasons.</span></span>  
  
-   <span data-ttu-id="48839-150">Tipos que implementam <xref:System.Runtime.Serialization.IObjectReference> lançar uma exceção em um ambiente parcialmente confiável, porque o <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> método requer a permissão de segurança `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.</span><span class="sxs-lookup"><span data-stu-id="48839-150">Types that implement <xref:System.Runtime.Serialization.IObjectReference> throw an exception in a partially-trusted environment because the <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> method requires the security permission `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.</span></span>  
  
## <a name="additional-notes-on-serialization"></a><span data-ttu-id="48839-151">Observações adicionais sobre serialização</span><span class="sxs-lookup"><span data-stu-id="48839-151">Additional Notes on Serialization</span></span>  
 <span data-ttu-id="48839-152">As seguintes regras também se aplicam a tipos com suporte pelo serializador de contrato de dados:</span><span class="sxs-lookup"><span data-stu-id="48839-152">The following rules also apply to types supported by the Data Contract Serializer:</span></span>  
  
-   <span data-ttu-id="48839-153">Tipos genéricos são totalmente suportados pelo serializador de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="48839-153">Generic types are fully supported by the data contract serializer.</span></span>  
  
-   <span data-ttu-id="48839-154">Tipos anuláveis são totalmente suportados pelo serializador de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="48839-154">Nullable types are fully supported by the data contract serializer.</span></span>  
  
-   <span data-ttu-id="48839-155">Tipos de interface são tratados como <xref:System.Object> ou, no caso de interfaces de coleção, como tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="48839-155">Interface types are treated either as <xref:System.Object> or, in the case of collection interfaces, as collection types.</span></span>  
  
-   <span data-ttu-id="48839-156">Há suporte para estruturas e classes.</span><span class="sxs-lookup"><span data-stu-id="48839-156">Both structures and classes are supported.</span></span>  
  
-   <span data-ttu-id="48839-157">O <xref:System.Runtime.Serialization.DataContractSerializer> não oferece suporte para o modelo de programação usado pelo <xref:System.Xml.Serialization.XmlSerializer> e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web.</span><span class="sxs-lookup"><span data-stu-id="48839-157">The <xref:System.Runtime.Serialization.DataContractSerializer> does not support the programming model used by the <xref:System.Xml.Serialization.XmlSerializer> and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services.</span></span> <span data-ttu-id="48839-158">Em particular, não dá suporte a atributos como <xref:System.Xml.Serialization.XmlElementAttribute> e <xref:System.Xml.Serialization.XmlAttributeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="48839-158">In particular, it does not support attributes like <xref:System.Xml.Serialization.XmlElementAttribute> and <xref:System.Xml.Serialization.XmlAttributeAttribute>.</span></span> <span data-ttu-id="48839-159">Para habilitar o suporte para este modelo de programação, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deve ser ativada para usar o <xref:System.Xml.Serialization.XmlSerializer> em vez do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="48839-159">To enable support for this programming model, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must be switched to use the <xref:System.Xml.Serialization.XmlSerializer> instead of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="48839-160">O <xref:System.DBNull> tipo é tratado de maneira especial.</span><span class="sxs-lookup"><span data-stu-id="48839-160">The <xref:System.DBNull> type is treated in a special way.</span></span> <span data-ttu-id="48839-161">Ele é um tipo singleton e após a desserialização o desserializador respeita a restrição de singleton e todos os pontos `DBNull` referências para a instância singleton.</span><span class="sxs-lookup"><span data-stu-id="48839-161">It is a singleton type, and upon deserialization the deserializer respects the singleton constraint and points all `DBNull` references to the singleton instance.</span></span> <span data-ttu-id="48839-162">Porque `DBNull` é um tipo serializável, ele exige <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> permissão.</span><span class="sxs-lookup"><span data-stu-id="48839-162">Because `DBNull` is a serializable type, it demands <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48839-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48839-163">See Also</span></span>  
 [<span data-ttu-id="48839-164">XML e tipos ADO.NET em contratos de dados</span><span class="sxs-lookup"><span data-stu-id="48839-164">XML and ADO.NET Types in Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)  
 [<span data-ttu-id="48839-165">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="48839-165">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="48839-166">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="48839-166">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [<span data-ttu-id="48839-167">Tipos de coleção em contratos de dados</span><span class="sxs-lookup"><span data-stu-id="48839-167">Collection Types in Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)  
 [<span data-ttu-id="48839-168">Tipos de enumeração em contratos de dados</span><span class="sxs-lookup"><span data-stu-id="48839-168">Enumeration Types in Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)