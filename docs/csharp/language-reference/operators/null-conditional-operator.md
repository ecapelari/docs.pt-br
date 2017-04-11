---
title: "?? Operator (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ??_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: de2abc6830419c368c6a62dfd74fc6f2013db9d4
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>?? Operador (Referência de C#)
O operador `??` é chamado operador de coalescência nula.  Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.  
  
## <a name="remarks"></a>Comentários  
 Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo). Você pode usar a expressividade sintática do operador `??` para retornar um valor apropriado (o operando direito) quando o operando esquerdo possuir um tipo anulável cujo valor seja nulo. Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado. Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.  
  
 Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).  
  
 O resultado de um operador ?? não será considerado constante, mesmo se os dois argumentos forem constantes.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)   
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)   
 [O que exatamente “levantado” significa?](http://go.microsoft.com/fwlink/?LinkID=112382)