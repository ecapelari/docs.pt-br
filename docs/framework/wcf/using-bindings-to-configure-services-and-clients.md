---
title: Usando associações para configurar serviços e clientes
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 8271f51885c0d7800d26018b94942a7d832bf4a5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806065"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Usando associações para configurar serviços e clientes
Associações são objetos que especificam os detalhes de comunicação necessários para conectar a um ponto de extremidade. Mais especificamente, associações contém informações de configuração que são usadas para criar o tempo de execução do cliente ou serviço, definindo as especificações de transportes (codificação de mensagens) para formatos de conexão e protocolos a serem usados para o canal de ponto de extremidade ou cliente respectivo. Para criar um serviço Windows Communication Foundation (WCF) está funcionando, cada ponto de extremidade no serviço requer uma associação. Este tópico explica as associações são, como elas são definidas e como uma associação específica é especificada para um ponto de extremidade.  
  
## <a name="what-a-binding-defines"></a>O que define uma associação  
 As informações em uma associação podem ser muito complexa ou muito básica. A associação mais básica especifica somente o protocolo de transporte (como HTTP) que deve ser usado para se conectar ao ponto de extremidade. Geralmente, as informações que contém uma associação sobre como se conectar a um ponto de extremidade se enquadra em uma das categorias na tabela a seguir.  
  
 Protocolos  
 Determina o mecanismo de segurança que está sendo usado, o recurso de mensagens confiável ou configurações de fluxo do contexto de transação.  
  
 Transporte  
 Determina o protocolo de transporte subjacente para usar (por exemplo, TCP ou HTTP).  
  
 Codificando  
 Determina a codificação de mensagens, por exemplo, texto/XML, binário ou mensagem de transmissão de otimização do mecanismo (MTOM), que determina como as mensagens são representadas como fluxos de bytes na conexão.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 O WCF inclui um conjunto de associações fornecidas pelo sistema que são projetados para cobrir a maioria dos requisitos de aplicativos e cenários. As classes a seguir representam alguns exemplos de associações fornecidas pelo sistema:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: Um protocolo HTTP adequado para se conectar a serviços Web de associação que é compatível com o WS-I Basic Profile 1.1 especificação (por exemplo, [ASMX] de serviços Web do ASP.NET-serviços baseados em).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Protocolos de especificações de serviços um protocolo HTTP associação adequado para se conectar a pontos de extremidade que estão em conformidade com a Web.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Usa a codificação binária do .NET e quadros tecnologias em conjunto com o Windows denominado transporte de pipe para se conectar a outros pontos de extremidade do WCF no mesmo computador.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Usa o binário de .NET codificação e quadros tecnologias em conjunto com o enfileiramento de mensagens (também conhecido como MSMQ) para criar conexões de mensagem na fila com outros pontos de extremidade do WCF.  
  
 Para obter uma lista de associações fornecidas pelo sistema, com descrições, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Se a coleção de associação fornecida pelo sistema não tiver a combinação correta de recursos que requer um aplicativo de serviço, você pode criar um <xref:System.ServiceModel.Channels.CustomBinding> associação. Para obter mais informações sobre os elementos de um <xref:System.ServiceModel.Channels.CustomBinding> de associação, consulte [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e [personalizado associações](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Usando associações  
 Usando associações envolve duas etapas básicas:  
  
1.  Selecione ou definir uma associação. O método mais fácil é escolher uma das associações fornecidas pelo sistema e usar as configurações padrão. Você também pode escolher uma associação fornecida pelo sistema e redefinir seus valores de propriedade para atender às suas necessidades. Como alternativa, você pode criar uma associação personalizada e definir todas as propriedades conforme necessário.  
  
2.  Crie um ponto de extremidade que usa esta associação.  
  
## <a name="code-and-configuration"></a>Código e configuração  
 Você pode definir ou configurar as associações por meio de código ou de configuração. Essas duas abordagens são independentes do tipo de associação usado, por exemplo, se você estiver usando um fornecido pelo sistema ou um <xref:System.ServiceModel.Channels.CustomBinding> associação. Em geral, usando código oferece total controle sobre a definição de uma associação ao compilar. Por outro lado, usando a configuração, permite que um administrador do sistema ou o usuário de um serviço WCF ou o cliente para alterar os parâmetros de associações. Essa flexibilidade geralmente é desejável, porque não há nenhuma maneira de prever os requisitos específicos de máquina e rede condições em que um aplicativo WCF é a ser implantado. Separar as informações de associação (e endereçamento) do código permite que os administradores alterem os detalhes de associação sem precisar recompilar ou reimplantar o aplicativo. Observe que, se a associação é definida no código, ele substitui quaisquer definições de configuração feitas no arquivo de configuração. Para obter exemplos desses procedimentos, consulte os tópicos a seguir:  
  
-   [Como: hospedar um serviço WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) fornece um exemplo de como criar uma associação no código.  
  
-   [Como: configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) fornece um exemplo de criação de um cliente usando a configuração.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Como especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Como especificar uma associação de serviço no código](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [Como especificar uma associação de cliente na configuração](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [Como especificar uma associação de cliente no código](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
