---
title: Resolvendo recursos externos durante processamento XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8921321191a68899e114613f8469e1552fff34bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="cfb79-102">Resolvendo recursos externos durante processamento XSLT</span><span class="sxs-lookup"><span data-stu-id="cfb79-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="cfb79-103">Há várias vezes durante uma transformação XSLT quando você precise resolver recursos externos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="cfb79-104">Usando a classe de XmlResolver</span><span class="sxs-lookup"><span data-stu-id="cfb79-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="cfb79-105">A classe de <xref:System.Xml.XmlResolver> é usada para resolver recursos externos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="cfb79-106">A tabela a seguir descreve quando <xref:System.Xml.XmlResolver> se torna envolvido durante processamento XSLT.</span><span class="sxs-lookup"><span data-stu-id="cfb79-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="cfb79-107">Tarefa XSLT</span><span class="sxs-lookup"><span data-stu-id="cfb79-107">XSLT task</span></span>|<span data-ttu-id="cfb79-108">O que o XmlResolver é usado para</span><span class="sxs-lookup"><span data-stu-id="cfb79-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="cfb79-109">Compile a folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-109">Compile the style sheet.</span></span>|<span data-ttu-id="cfb79-110">Resolver o URI de folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="cfb79-111">-e-</span><span class="sxs-lookup"><span data-stu-id="cfb79-111">-and-</span></span><br /><br /> <span data-ttu-id="cfb79-112">Resolver referências de URI em todos os elementos de `xsl:import` ou de `xsl:include` .</span><span class="sxs-lookup"><span data-stu-id="cfb79-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="cfb79-113">Executar a folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-113">Execute the style sheet.</span></span>|<span data-ttu-id="cfb79-114">Resolver o URI de documento de contexto.</span><span class="sxs-lookup"><span data-stu-id="cfb79-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="cfb79-115">-e-</span><span class="sxs-lookup"><span data-stu-id="cfb79-115">-and-</span></span><br /><br /> <span data-ttu-id="cfb79-116">Resolver referências de URI em todas as funções XSLT `document()` .</span><span class="sxs-lookup"><span data-stu-id="cfb79-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="cfb79-117">Os métodos de <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> e de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> incluem as sobrecargas que recebem um objeto de <xref:System.Xml.XmlResolver> como um dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="cfb79-118">Se <xref:System.Xml.XmlResolver> não for especificado, <xref:System.Xml.XmlUrlResolver> padrão sem credenciais é usado.</span><span class="sxs-lookup"><span data-stu-id="cfb79-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="cfb79-119">A lista a seguir descreve quando você pode querer especificar um objeto de <xref:System.Xml.XmlResolver> :</span><span class="sxs-lookup"><span data-stu-id="cfb79-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="cfb79-120">Se o processo XSLT precisa acessar um recurso de rede que requer autenticação, você pode usar <xref:System.Xml.XmlResolver> com as credenciais necessárias.</span><span class="sxs-lookup"><span data-stu-id="cfb79-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="cfb79-121">Se você deseja restringir os recursos que o processo XSLT pode acessar, você pode usar <xref:System.Xml.XmlSecureResolver> com o conjunto de permissões correto.</span><span class="sxs-lookup"><span data-stu-id="cfb79-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="cfb79-122">Use a classe de <xref:System.Xml.XmlSecureResolver> se você precisa abrir um recurso que você não controle, ou que é não confiável.</span><span class="sxs-lookup"><span data-stu-id="cfb79-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="cfb79-123">Se você desejar personalizar o comportamento, você pode implementar sua própria classe de <xref:System.Xml.XmlResolver> e usá-la para resolver recursos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="cfb79-124">Se você quiser garantir que nenhum recurso externo é acessado, você pode especificar `null` para o argumento de <xref:System.Xml.XmlResolver> .</span><span class="sxs-lookup"><span data-stu-id="cfb79-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfb79-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfb79-125">Example</span></span>  
 <span data-ttu-id="cfb79-126">O exemplo a seguir cria uma folha de estilos que é armazenada em um recurso de rede.</span><span class="sxs-lookup"><span data-stu-id="cfb79-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="cfb79-127">Um objeto de <xref:System.Xml.XmlUrlResolver> especifica as credenciais necessárias para acessar a folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="cfb79-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="cfb79-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfb79-128">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [<span data-ttu-id="cfb79-129">Transformações XSLT</span><span class="sxs-lookup"><span data-stu-id="cfb79-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)