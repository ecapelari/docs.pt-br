---
title: Como acessar dispositivos de criptografia de hardware
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
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5156316387f94d434301e2d5286bd325d7e04320
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="61d1e-102">Como acessar dispositivos de criptografia de hardware</span><span class="sxs-lookup"><span data-stu-id="61d1e-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="61d1e-103">Você pode usar o <xref:System.Security.Cryptography.CspParameters> classe acessem dispositivos de criptografia de hardware.</span><span class="sxs-lookup"><span data-stu-id="61d1e-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="61d1e-104">Por exemplo, você pode usar esta classe para integrar seu aplicativo com um cartão inteligente, um gerador de número aleatório de hardware ou uma implementação de um determinado algoritmo de criptografia de hardware.</span><span class="sxs-lookup"><span data-stu-id="61d1e-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="61d1e-105">O <xref:System.Security.Cryptography.CspParameters> classe cria um provedor de serviços de criptografia (CSP) que acessa um dispositivo de criptografia de hardware instalado corretamente.</span><span class="sxs-lookup"><span data-stu-id="61d1e-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="61d1e-106">Você pode verificar a disponibilidade de um CSP inspecionando a seguinte chave do registro usando o Editor do registro (Regedit.exe): HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="61d1e-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="61d1e-107">Para assinar dados usando um cartão de chave</span><span class="sxs-lookup"><span data-stu-id="61d1e-107">To sign data using a key card</span></span>  
  
1.  <span data-ttu-id="61d1e-108">Criar uma nova instância do <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.</span><span class="sxs-lookup"><span data-stu-id="61d1e-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="61d1e-109">Passe os sinalizadores apropriados para o <xref:System.Security.Cryptography.CspParameters.Flags%2A> propriedade recém-criado <xref:System.Security.Cryptography.CspParameters> objeto.</span><span class="sxs-lookup"><span data-stu-id="61d1e-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="61d1e-110">Por exemplo, passar o <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> sinalizador.</span><span class="sxs-lookup"><span data-stu-id="61d1e-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3.  <span data-ttu-id="61d1e-111">Criar uma nova instância de um <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (por exemplo, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe), passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="61d1e-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4.  <span data-ttu-id="61d1e-112">Assinar os dados usando uma da `Sign` métodos e verifique se os dados usando uma da `Verify` métodos.</span><span class="sxs-lookup"><span data-stu-id="61d1e-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="61d1e-113">Para gerar um número aleatório usando um gerador de número aleatório de hardware</span><span class="sxs-lookup"><span data-stu-id="61d1e-113">To generate a random number using a hardware random number generator</span></span>  
  
1.  <span data-ttu-id="61d1e-114">Criar uma nova instância do <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.</span><span class="sxs-lookup"><span data-stu-id="61d1e-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2.  <span data-ttu-id="61d1e-115">Criar uma nova instância do <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="61d1e-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3.  <span data-ttu-id="61d1e-116">Criar um valor aleatório usando o <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> ou <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> método.</span><span class="sxs-lookup"><span data-stu-id="61d1e-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61d1e-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61d1e-117">Example</span></span>  
 <span data-ttu-id="61d1e-118">O exemplo de código a seguir demonstra como assinar dados usando um cartão inteligente.</span><span class="sxs-lookup"><span data-stu-id="61d1e-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="61d1e-119">O exemplo de código cria um <xref:System.Security.Cryptography.CspParameters> objeto que expõe um cartão inteligente e, em seguida, inicia um <xref:System.Security.Cryptography.RSACryptoServiceProvider> usando o CSP do objeto.</span><span class="sxs-lookup"><span data-stu-id="61d1e-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="61d1e-120">O exemplo de código, em seguida, assina e verifica alguns dados.</span><span class="sxs-lookup"><span data-stu-id="61d1e-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61d1e-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="61d1e-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="61d1e-122">Incluir o <xref:System> e <xref:System.Security.Cryptography> namespaces.</span><span class="sxs-lookup"><span data-stu-id="61d1e-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
-   <span data-ttu-id="61d1e-123">Você deve ter um leitor de cartão inteligente e drivers instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="61d1e-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
-   <span data-ttu-id="61d1e-124">Você deve inicializar o <xref:System.Security.Cryptography.CspParameters> objeto usando informações específicas para o leitor de cartão.</span><span class="sxs-lookup"><span data-stu-id="61d1e-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="61d1e-125">Para obter mais informações, consulte a documentação de seu leitor de cartão.</span><span class="sxs-lookup"><span data-stu-id="61d1e-125">For more information, see the documentation of your card reader.</span></span>