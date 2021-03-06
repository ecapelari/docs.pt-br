---
title: '&amp; Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604296"
---
# <a name="amp-operator-visual-basic"></a>&amp; Operador (Visual Basic)
Gera uma concatenação de cadeia de caracteres de duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `String` ou `Object` variável.  
  
 `expression1`  
 Necessário. Qualquer expressão com um tipo de dados que amplia a `String`.  
  
 `expression2`  
 Necessário. Qualquer expressão com um tipo de dados que amplia a `String`.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo de dados `expression1` ou `expression2` não é `String` mas amplia a `String`, ele será convertido em `String`. Se qualquer um dos tipos de dados não se estendem ao `String`, o compilador gerará um erro.  
  
 O tipo de dados `result` é `String`. Se uma ou ambas as expressões são avaliadas como [nada](../../../visual-basic/language-reference/nothing.md) ou tem um valor de <xref:System.DBNull.Value?displayProperty=nameWithType>, eles são tratados como uma cadeia de caracteres com um valor de "".  
  
> [!NOTE]
>  O `&` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  O caractere e comercial (&) também podem ser usados para identificar variáveis como tipo `Long`. Para obter mais informações, consulte [caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres. O resultado é um valor de cadeia de caracteres que representa a concatenação dos operandos de cadeia de caracteres de dois.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador &=](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operadores de concatenação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
