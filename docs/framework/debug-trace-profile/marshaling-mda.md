---
title: MDA marshaling
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 164c7a6e4411d7ff3e66643c6f012fdba790ef49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386672"
---
# <a name="marshaling-mda"></a>MDA marshaling
O MDA (Assistente de Depuração Gerenciado) de `marshaling` é ativado quando o CLR define informações de marshaling para um parâmetro de método ou um campo de uma estrutura. Esse MDA não funciona para assemblies compilados por JIT.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 O MDA exibe o tipo do parâmetro ou campo nos contextos gerenciado e não gerenciado, bem como a estrutura ou o método que contém o tipo.  A seguir está um exemplo da saída de um campo:  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a>Configuração  
 A configuração de MDA permite que você filtre as informações de marshaling relatadas com base no campo envolvido ou em nomes de método.  O exemplo a seguir mostra o uso dos elementos `methodFilter`, `fieldFilter` e `match` para especificar filtros.  Definir o atributo `name` como um asterisco (*) corresponderá a tudo.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
