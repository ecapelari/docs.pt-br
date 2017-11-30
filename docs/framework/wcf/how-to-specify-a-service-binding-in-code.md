---
title: "Como especificar uma associação de serviço em código"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 64d33b268c736b3dba333b767bee7fedb487397b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Como especificar uma associação de serviço em código
Neste exemplo, um `ICalculator` contrato é definido para um serviço de cálculo, o serviço é implementado no `CalculatorService` classe e seu ponto de extremidade é definido no código, onde ele é especificado que o serviço deve usar o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Geralmente é a prática recomendada para especificar declarativamente a associação e as informações de endereço na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.  
  
 Para obter uma descrição de como configurar este serviço usando os elementos de configuração em vez de código, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Para especificar em código para usar o BasicHttpBinding para o serviço  
  
1.  Defina um contrato de serviço para o tipo de serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  Implemente o contrato de serviço em uma classe de serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  No aplicativo de hospedagem, crie o endereço base para o serviço e a associação para usar com o serviço.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  Crie o host para o serviço, adicionar o ponto de extremidade e, em seguida, abrir o host.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar os valores padrão das propriedades de associação  
  
1.  Para modificar um dos valores de propriedade padrão da <xref:System.ServiceModel.BasicHttpBinding> classe, defina o valor da propriedade na associação para o novo valor antes de criar o host. Por exemplo, para alterar os valores de tempo limite de abertura e fechamento do padrão de 1 minuto para 2 minutos, use o seguinte.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md) (Usando associações para configurar serviços e clientes)  
 [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md) (Especificando um endereço do ponto de extremidade)