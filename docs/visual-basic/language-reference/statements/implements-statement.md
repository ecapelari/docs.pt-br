---
title: Instrução Implements
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 5afc7e4e3a03dfab1288e50e65e5076bdd438f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604205"
---
# <a name="implements-statement"></a>Instrução Implements
Especifica um ou mais interfaces, ou membros de interface, que devem ser implementados na classe ou definição de estrutura na qual ele aparece.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Partes  
 `interfacename`  
 Necessário. Uma interface cujas propriedades, procedimentos e eventos devem ser implementados por membros correspondentes na classe ou estrutura.  
  
 `interfacemember`  
 Necessário. O membro de uma interface que está sendo implementado.  
  
## <a name="remarks"></a>Comentários  
 Uma interface é uma coleção de protótipos que representa os membros (propriedades, procedimentos e eventos) encapsula a interface. Interfaces contêm apenas as declarações de membros; classes e estruturas implementam esses membros. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 O `Implements` instrução deve seguir imediatamente a `Class` ou `Structure` instrução.  
  
 Quando você implementa uma interface, você deve implementar todos os membros declarados na interface. Omitir qualquer membro é considerado um erro de sintaxe. Para implementar um membro individual, você deve especificar o [implementa](../../../visual-basic/language-reference/statements/implements-clause.md) palavra-chave (que é separada do `Implements` instrução) quando você declara o membro na classe ou estrutura. Para obter mais informações, consulte [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Classes podem usar [privada](../../../visual-basic/language-reference/modifiers/private.md) implementações de propriedades e procedimentos, mas esses membros são acessíveis somente chamando uma instância da classe implementada em uma variável declarada com o tipo da interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `Implements` instrução para implementar membros de uma interface. Define uma interface denominada `ICustomerInfo` com um evento, uma propriedade e um procedimento. A classe `customerInfo` implementa todos os membros definidos na interface.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Observe que a classe `customerInfo` usa o `Implements` instrução em uma linha de código fonte separado para indicar que a classe implementa todos os membros de `ICustomerInfo` interface. Em seguida, cada membro na classe usa a `Implements` palavra-chave como parte de sua declaração de membro para indicar que implementa o membro da interface.  
  
## <a name="example"></a>Exemplo  
 Os dois procedimentos a seguir mostram como você poderia usar a interface implementada no exemplo anterior. Para testar a implementação, adicione esses procedimentos no seu projeto e chame o `testImplements` procedimento.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
