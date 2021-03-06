---
title: Espaço em branco em literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649744"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>Espaço em branco em literais XML (Visual Basic)
O compilador do Visual Basic incorpora somente os caracteres de espaço em branco significativo de um literal XML quando ele cria uma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto. Os caracteres de espaço em branco insignificante não são incorporados.  
  
## <a name="significant-and-insignificant-white-space"></a>Espaço em branco significativo e insignificante  
 Caracteres de espaço em branco em literais XML são significativos em apenas três áreas:  
  
-   Quando eles estão em um valor de atributo.  
  
-   Quando eles fazem parte de conteúdo de texto um elemento do e o texto também contém outros caracteres.  
  
-   Quando eles estão em uma expressão inserida para o conteúdo de texto de um elemento.  
  
 Caso contrário, o compilador trata os caracteres de espaço em branco como insignificante e não inclui, em seguida, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objeto para o literal.  
  
 Para incluir o espaço em branco insignificante em um literal XML, use uma expressão inserida que contém uma cadeia de caracteres literal com o espaço em branco.  
  
> [!NOTE]
>  Se o `xml:space` atributo aparece em um elemento XML, o compilador do Visual Basic inclui o atributo de <xref:System.Xml.Linq.XElement> objeto, mas adicionar esse atributo não alterar como o compilador trata os espaços em branco.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir contém dois elementos XML, externos e internos. Os dois elementos contenham espaço em branco em seu conteúdo de texto. O espaço em branco no elemento externo é insignificante, porque ele contém somente espaços em branco e um elemento XML. O espaço em branco no elemento interno é significativo porque ele contém espaço em branco e texto.  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Quando executado, esse código exibe o texto a seguir.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
