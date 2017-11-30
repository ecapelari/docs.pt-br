---
title: "Diretrizes de design para exceções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="18865-102">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="18865-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="18865-103">Manipulação de exceção tem muitas vantagens em relação a relatórios de erros com base em valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="18865-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="18865-104">Design de boa estrutura ajuda o desenvolvedor do aplicativo perceber os benefícios de exceções.</span><span class="sxs-lookup"><span data-stu-id="18865-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="18865-105">Esta seção aborda os benefícios de exceções e apresenta diretrizes para usá-las com eficiência.</span><span class="sxs-lookup"><span data-stu-id="18865-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18865-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="18865-106">In This Section</span></span>  
 [<span data-ttu-id="18865-107">Lançando exceções</span><span class="sxs-lookup"><span data-stu-id="18865-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="18865-108">Usando tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="18865-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="18865-109">Desempenho e exceções</span><span class="sxs-lookup"><span data-stu-id="18865-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="18865-110">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="18865-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="18865-111">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="18865-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18865-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18865-112">See Also</span></span>  
 [<span data-ttu-id="18865-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="18865-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)