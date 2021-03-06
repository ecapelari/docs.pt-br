---
title: Matrizes
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2945ead7c22b759ce88f6585e2254e9bc540a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570380"
---
# <a name="arrays"></a>Matrizes
**FAZER ✓** preferir usar coleções em matrizes em APIs públicas. O [coleções](../../../docs/standard/design-guidelines/guidelines-for-collections.md) seção fornece detalhes sobre como escolher entre coleções e matrizes.  
  
 **X não** usar campos de matriz de somente leitura. O próprio campo é somente leitura e não pode ser alterado, mas os elementos da matriz podem ser alterados.  
  
 **✓ CONSIDERE** usando matrizes denteadas em vez de matrizes multidimensionais.  
  
 Uma matriz denteada é uma matriz com elementos também são matrizes. As matrizes que compõem os elementos podem ser de tamanhos diferentes, resultando em menos perda de espaço para alguns conjuntos de dados (por exemplo, matriz esparsa) em comparação comparada matrizes multidimensionais. Além disso, o CLR otimiza as operações de índice em matrizes denteadas, para que eles podem apresentar melhor desempenho de tempo de execução em alguns cenários.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array>  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
