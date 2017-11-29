---
title: "Segurança 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d7288eeffeb642d1e897e11153802633d71747bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-overview"></a><span data-ttu-id="b358a-102">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="b358a-102">Security Overview</span></span>
<span data-ttu-id="b358a-103">Proteger um aplicativo é um processo contínuo.</span><span class="sxs-lookup"><span data-stu-id="b358a-103">Securing an application is an ongoing process.</span></span> <span data-ttu-id="b358a-104">Nunca será um ponto em que um desenvolvedor pode garantir que um aplicativo é seguro de todos os ataques, porque é impossível prever quais tipos de novas tecnologias de ataques futuros causará.</span><span class="sxs-lookup"><span data-stu-id="b358a-104">There will never be a point where a developer can guarantee that an application is safe from all attacks, because it is impossible to predict what kinds of future attacks new technologies will bring about.</span></span> <span data-ttu-id="b358a-105">Por outro lado, só porque ninguém tem falhas de segurança ainda descobertos (ou publicado) em um sistema não significa que nenhum existem ou podem existir.</span><span class="sxs-lookup"><span data-stu-id="b358a-105">Conversely, just because nobody has yet discovered (or published) security flaws in a system does not mean that none exist or could exist.</span></span> <span data-ttu-id="b358a-106">Você precisa planejar a segurança durante a fase de design do projeto, bem como para planejar como segurança será mantida durante o tempo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b358a-106">You need to plan for security during the design phase of the project, as well as plan how security will be maintained over the lifetime of the application.</span></span>  
  
## <a name="design-for-security"></a><span data-ttu-id="b358a-107">Design de segurança</span><span class="sxs-lookup"><span data-stu-id="b358a-107">Design for Security</span></span>  
 <span data-ttu-id="b358a-108">Um dos maiores problemas no desenvolvimento de aplicativos seguros é que a segurança é geralmente prioridade, algo implemente depois de um projeto é a conclusão de código.</span><span class="sxs-lookup"><span data-stu-id="b358a-108">One of the biggest problems in developing secure applications is that security is often an afterthought, something to implement after a project is code-complete.</span></span> <span data-ttu-id="b358a-109">Não criar segurança em um aplicativo desde o início leva a aplicativos não seguros porque tem pouco a que torna um aplicativo seguro.</span><span class="sxs-lookup"><span data-stu-id="b358a-109">Not building security into an application at the outset leads to insecure applications because little thought has been given to what makes an application secure.</span></span>  
  
 <span data-ttu-id="b358a-110">Implementação de segurança do último minuto leva a mais bugs, como quebras de software em novas restrições ou precisa ser reescrito para acomodar a funcionalidade inesperada.</span><span class="sxs-lookup"><span data-stu-id="b358a-110">Last minute security implementation leads to more bugs, as software breaks under the new restrictions or has to be rewritten to accommodate unanticipated functionality.</span></span> <span data-ttu-id="b358a-111">Cada linha de código revisado contém a possibilidade de introduzir um novo bug.</span><span class="sxs-lookup"><span data-stu-id="b358a-111">Every line of revised code contains the possibility of introducing a new bug.</span></span> <span data-ttu-id="b358a-112">Por esse motivo, você deve considerar a segurança no início do processo de desenvolvimento, para que ele possa continuar em conjunto com o desenvolvimento de novos recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-112">For this reason, you should consider security early in the development process so that it can proceed in tandem with the development of new features.</span></span>  
  
### <a name="threat-modeling"></a><span data-ttu-id="b358a-113">Modelagem de ameaças</span><span class="sxs-lookup"><span data-stu-id="b358a-113">Threat Modeling</span></span>  
 <span data-ttu-id="b358a-114">Você não pode proteger o sistema contra ataques a menos que você compreenda todos os ataques potenciais que está exposta a.</span><span class="sxs-lookup"><span data-stu-id="b358a-114">You cannot protect a system against attack unless you understand all the potential attacks that it is exposed to.</span></span> <span data-ttu-id="b358a-115">O processo de avaliação de ameaças de segurança, denominado *a modelagem de ameaças*, é necessário para determinar a probabilidade e ramificações de violações de segurança em seu aplicativo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b358a-115">The process of evaluating security threats, called *threat modeling*, is necessary to determine the likelihood and ramifications of security breaches in your ADO.NET application.</span></span>  
  
 <span data-ttu-id="b358a-116">Modelagem de ameaças é composta de três etapas de alto nível: Noções básicas sobre o modo de exibição do adversário, que caracterizam a segurança do sistema e determinar as ameaças.</span><span class="sxs-lookup"><span data-stu-id="b358a-116">Threat modeling is composed of three high-level steps: understanding the adversary’s view, characterizing the security of the system, and determining threats.</span></span>  
  
 <span data-ttu-id="b358a-117">Modelagem de ameaças é uma abordagem iterativa para avaliação de vulnerabilidades em seu aplicativo encontrar aquelas que são mais perigoso, pois expõem os dados mais confidenciais.</span><span class="sxs-lookup"><span data-stu-id="b358a-117">Threat modeling is an iterative approach to assessing vulnerabilities in your application to find those that are the most dangerous because they expose the most sensitive data.</span></span> <span data-ttu-id="b358a-118">Depois que você identificar as vulnerabilidades, você classificá-las em ordem de gravidade e cria um conjunto de prioridade de contramedidas para as ameaças do contador.</span><span class="sxs-lookup"><span data-stu-id="b358a-118">Once you identify the vulnerabilities, you rank them in order of severity and create a prioritized set of countermeasures to counter the threats.</span></span>  
  
 <span data-ttu-id="b358a-119">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-119">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b358a-120">Recurso</span><span class="sxs-lookup"><span data-stu-id="b358a-120">Resource</span></span>|<span data-ttu-id="b358a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b358a-121">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b358a-122">O [modelagem de ameaça](http://go.microsoft.com/fwlink/?LinkId=98353) site MSDN Security Developer Center</span><span class="sxs-lookup"><span data-stu-id="b358a-122">The [Threat Modeling](http://go.microsoft.com/fwlink/?LinkId=98353) site on the MSDN Security Developer Center</span></span>|<span data-ttu-id="b358a-123">Os recursos nesta página ajudarão você a entender a processo de modelagem de ameaças e criar modelos de ameaças que você pode usar para proteger seus aplicativos</span><span class="sxs-lookup"><span data-stu-id="b358a-123">The resources on this page will help you understand the threat modeling process and build threat models that you can use to secure your own applications</span></span>|  
  
## <a name="the-principle-of-least-privilege"></a><span data-ttu-id="b358a-124">O princípio de privilégios mínimos</span><span class="sxs-lookup"><span data-stu-id="b358a-124">The Principle of Least Privilege</span></span>  
 <span data-ttu-id="b358a-125">Quando você projeta, cria e implanta seu aplicativo, você deve supor que seu aplicativo será atacado.</span><span class="sxs-lookup"><span data-stu-id="b358a-125">When you design, build, and deploy your application, you must assume that your application will be attacked.</span></span> <span data-ttu-id="b358a-126">Geralmente, esses ataques provenientes código mal-intencionado que é executado com as permissões do usuário que executa o código.</span><span class="sxs-lookup"><span data-stu-id="b358a-126">Often these attacks come from malicious code that executes with the permissions of the user running the code.</span></span> <span data-ttu-id="b358a-127">Outros podem ser obtidos com o código bem intencionado que tenha sido explorado por um invasor.</span><span class="sxs-lookup"><span data-stu-id="b358a-127">Others can originate with well-intentioned code that has been exploited by an attacker.</span></span> <span data-ttu-id="b358a-128">Ao planejar a segurança, sempre assuma o que pior cenário ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="b358a-128">When planning security, always assume the worst-case scenario will occur.</span></span>  
  
 <span data-ttu-id="b358a-129">É uma medida de contador, que você pode usar tentar colocar tantas proteções ao seu código possível executando com privilégios mínimos.</span><span class="sxs-lookup"><span data-stu-id="b358a-129">One counter-measure you can employ is to try to erect as many walls around your code as possible by running with least privilege.</span></span> <span data-ttu-id="b358a-130">O princípio de menos privilégios diz que qualquer privilégio deve ser concedido para a quantidade mínima de código necessário para a duração mais curta de tempo que é necessário para realizar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="b358a-130">The principle of least privilege says that any given privilege should be granted to the least amount of code necessary for the shortest duration of time that is required to get the job done.</span></span>  
  
 <span data-ttu-id="b358a-131">A prática recomendada para a criação de aplicativos seguros é iniciar com nenhuma permissão e, em seguida, adicionar as permissões mais restrito para a tarefa específica que está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="b358a-131">The best practice for creating secure applications is to start with no permissions at all and then add the narrowest permissions for the particular task being performed.</span></span> <span data-ttu-id="b358a-132">Por outro lado, começando com todas as permissões e, em seguida, negando individuais que leva a aplicativos não seguros que são difíceis de testar e manter como falhas de segurança podem existir acidentalmente conceda mais permissões do que o necessário.</span><span class="sxs-lookup"><span data-stu-id="b358a-132">By contrast, starting with all permissions and then denying individual ones leads to insecure applications that are difficult to test and maintain because security holes may exist from unintentionally granting more permissions than required.</span></span>  
  
 <span data-ttu-id="b358a-133">Para obter mais informações sobre como proteger seus aplicativos, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-133">For more information on securing your applications, see the following resources.</span></span>  
  
|<span data-ttu-id="b358a-134">Recurso</span><span class="sxs-lookup"><span data-stu-id="b358a-134">Resource</span></span>|<span data-ttu-id="b358a-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="b358a-135">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="b358a-136">Protegendo aplicativos</span><span class="sxs-lookup"><span data-stu-id="b358a-136">Securing Applications</span></span>](/visualstudio/ide/securing-applications)|<span data-ttu-id="b358a-137">Contém links para tópicos gerais de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-137">Contains links to general security topics.</span></span> <span data-ttu-id="b358a-138">Também contém links para tópicos para proteger aplicativos distribuídos, aplicativos Web, aplicativos móveis e aplicativos de desktop.</span><span class="sxs-lookup"><span data-stu-id="b358a-138">Also contains links to topics for securing distributed applications, Web applications, mobile applications, and desktop applications.</span></span>|  
  
## <a name="code-access-security-cas"></a><span data-ttu-id="b358a-139">CAS (Segurança de Acesso do Código)</span><span class="sxs-lookup"><span data-stu-id="b358a-139">Code Access Security (CAS)</span></span>  
 <span data-ttu-id="b358a-140">Segurança de acesso ao código (CAS) é um mecanismo que ajuda a limitar o acesso ao código tem a recursos protegidos e operações.</span><span class="sxs-lookup"><span data-stu-id="b358a-140">Code access security (CAS) is a mechanism that helps limit the access that code has to protected resources and operations.</span></span> <span data-ttu-id="b358a-141">No .NET Framework, o ACS executa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="b358a-141">In the .NET Framework, CAS performs the following functions:</span></span>  
  
-   <span data-ttu-id="b358a-142">Define as permissões e os conjuntos de permissões que representam o direito de acesso a vários recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="b358a-142">Defines permissions and permission sets that represent the right to access various system resources.</span></span>  
  
-   <span data-ttu-id="b358a-143">Permite aos administradores configurar política de segurança, associando os conjuntos de permissões a grupos de código (grupos de código).</span><span class="sxs-lookup"><span data-stu-id="b358a-143">Enables administrators to configure security policy by associating sets of permissions with groups of code (code groups).</span></span>  
  
-   <span data-ttu-id="b358a-144">Permite que o código solicitar as permissões requeridas para executar, bem como as permissões que seriam úteis para ter e especifica que o código nunca deve ter as permissões.</span><span class="sxs-lookup"><span data-stu-id="b358a-144">Enables code to request the permissions it requires in order to run, as well as the permissions that would be useful to have, and specifies which permissions the code must never have.</span></span>  
  
-   <span data-ttu-id="b358a-145">Concede permissões para cada assembly carregado, com base nas permissões solicitadas pelo código e as operações permitidas pela política de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-145">Grants permissions to each assembly that is loaded, based on the permissions requested by the code and on the operations permitted by security policy.</span></span>  
  
-   <span data-ttu-id="b358a-146">Permite que o código que os chamadores têm permissões específicas de demanda.</span><span class="sxs-lookup"><span data-stu-id="b358a-146">Enables code to demand that its callers have specific permissions.</span></span>  
  
-   <span data-ttu-id="b358a-147">Permite que o código que os chamadores tenha uma assinatura digital, permitindo que somente os chamadores de uma determinada organização ou um site chamar o código protegido de demanda.</span><span class="sxs-lookup"><span data-stu-id="b358a-147">Enables code to demand that its callers possess a digital signature, thus allowing only callers from a particular organization or site to call the protected code.</span></span>  
  
-   <span data-ttu-id="b358a-148">Impõe restrições no código em tempo de execução, comparando as permissões concedidas de todos os chamadores na pilha de chamadas para as permissões que os chamadores devem ter.</span><span class="sxs-lookup"><span data-stu-id="b358a-148">Enforces restrictions on code at run time by comparing the granted permissions of every caller on the call stack to the permissions that callers must have.</span></span>  
  
 <span data-ttu-id="b358a-149">Para minimizar a quantidade de danos que podem ocorrer se um ataque tiver êxito, escolha um contexto de segurança de seu código que concede acesso apenas os recursos necessários para executar seu trabalho concluído e não mais.</span><span class="sxs-lookup"><span data-stu-id="b358a-149">To minimize the amount of damage that can occur if an attack succeeds, choose a security context for your code that grants access only to the resources it needs to get its work done and no more.</span></span>  
  
 <span data-ttu-id="b358a-150">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-150">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b358a-151">Recurso</span><span class="sxs-lookup"><span data-stu-id="b358a-151">Resource</span></span>|<span data-ttu-id="b358a-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="b358a-152">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="b358a-153">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b358a-153">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)|<span data-ttu-id="b358a-154">Descreve as interações entre ambientes parcialmente confiáveis da perspectiva de um aplicativo ADO.NET, segurança baseada em função e segurança de acesso ao código.</span><span class="sxs-lookup"><span data-stu-id="b358a-154">Describes the interactions between code access security, role-based security, and partially trusted environments from the perspective of an ADO.NET application.</span></span>|  
|[<span data-ttu-id="b358a-155">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="b358a-155">Code Access Security</span></span>](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|<span data-ttu-id="b358a-156">Contém links para tópicos adicionais que descrevem o CAS no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b358a-156">Contains links to additional topics describing CAS in the .NET Framework.</span></span>|  
  
## <a name="database-security"></a><span data-ttu-id="b358a-157">Segurança de banco de dados</span><span class="sxs-lookup"><span data-stu-id="b358a-157">Database Security</span></span>  
 <span data-ttu-id="b358a-158">O princípio de menos privilégios também se aplica à fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b358a-158">The principle of least privilege also applies to your data source.</span></span> <span data-ttu-id="b358a-159">Algumas diretrizes gerais para segurança de banco de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="b358a-159">Some general guidelines for database security include:</span></span>  
  
-   <span data-ttu-id="b358a-160">Crie contas com os privilégios mais baixos possíveis.</span><span class="sxs-lookup"><span data-stu-id="b358a-160">Create accounts with the lowest possible privileges.</span></span>  
  
-   <span data-ttu-id="b358a-161">Não permitir que usuários acessem contas administrativas para obter o código em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="b358a-161">Do not allow users access to administrative accounts just to get code working.</span></span>  
  
-   <span data-ttu-id="b358a-162">Não retornam mensagens de erro do lado do servidor para aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="b358a-162">Do not return server-side error messages to client applications.</span></span>  
  
-   <span data-ttu-id="b358a-163">Valide todas as entradas no cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="b358a-163">Validate all input at both the client and the server.</span></span>  
  
-   <span data-ttu-id="b358a-164">Use comandos parametrizados e evitar instruções SQL dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="b358a-164">Use parameterized commands and avoid dynamic SQL statements.</span></span>  
  
-   <span data-ttu-id="b358a-165">Habilite a segurança de auditoria e log do banco de dados que você está usando para que você será alertado de quaisquer violações de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-165">Enable security auditing and logging for the database you are using so that you are alerted to any security breaches.</span></span>  
  
 <span data-ttu-id="b358a-166">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-166">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b358a-167">Recurso</span><span class="sxs-lookup"><span data-stu-id="b358a-167">Resource</span></span>|<span data-ttu-id="b358a-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="b358a-168">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b358a-169">[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b358a-169">[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md)</span></span>|<span data-ttu-id="b358a-170">Fornece uma visão geral de segurança do SQL Server com cenários de aplicativos que fornecem orientação para a criação de aplicativos seguros do ADO.NET destino do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b358a-170">Provides an overview of SQL Server security with application scenarios that provide guidance for creating secure ADO.NET applications that target SQL Server.</span></span>|  
|[<span data-ttu-id="b358a-171">Recomendações para estratégias de acesso de dados</span><span class="sxs-lookup"><span data-stu-id="b358a-171">Recommendations for Data Access Strategies</span></span>](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|<span data-ttu-id="b358a-172">Fornece recomendações para acessar dados e executar operações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b358a-172">Provides recommendations for accessing data and performing database operations.</span></span>|  
  
## <a name="security-policy-and-administration"></a><span data-ttu-id="b358a-173">Diretiva de segurança e administração</span><span class="sxs-lookup"><span data-stu-id="b358a-173">Security Policy and Administration</span></span>  
 <span data-ttu-id="b358a-174">Administrar incorretamente a política de CAS (segurança) de acesso do código pode criar vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-174">Improperly administering code access security (CAS) policy can potentially create security weaknesses.</span></span> <span data-ttu-id="b358a-175">Quando um aplicativo é implantado, técnicas para monitorar a segurança devem ser usadas e riscos avaliados como novas ameaças surgem.</span><span class="sxs-lookup"><span data-stu-id="b358a-175">Once an application is deployed, techniques for monitoring security should be used and risks evaluated as new threats emerge.</span></span>  
  
 <span data-ttu-id="b358a-176">Para obter mais informações, consulte os seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b358a-176">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b358a-177">Recurso</span><span class="sxs-lookup"><span data-stu-id="b358a-177">Resource</span></span>|<span data-ttu-id="b358a-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="b358a-178">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="b358a-179">PONTA: Gerenciamento de política de segurança</span><span class="sxs-lookup"><span data-stu-id="b358a-179">NIB: Security Policy Management</span></span>](http://msdn.microsoft.com/en-us/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|<span data-ttu-id="b358a-180">Fornece informações sobre como criar e administrar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-180">Provides information on creating and administering security policy.</span></span>|  
|[<span data-ttu-id="b358a-181">PONTA: Práticas recomendadas de política de segurança</span><span class="sxs-lookup"><span data-stu-id="b358a-181">NIB: Security Policy Best Practices</span></span>](http://msdn.microsoft.com/en-us/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|<span data-ttu-id="b358a-182">Fornece links que descrevem como administrar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="b358a-182">Provides links describing how to administer security policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b358a-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b358a-183">See Also</span></span>  
 <span data-ttu-id="b358a-184">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b358a-184">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="b358a-185">[PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784) (PAVE Segurança no código nativo e do .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="b358a-185">[PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)</span></span>  
 <span data-ttu-id="b358a-186">[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b358a-186">[SQL Server Security](../../../../docs/framework/data/adonet/sql/sql-server-security.md)</span></span>  
 <span data-ttu-id="b358a-187">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b358a-187">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>