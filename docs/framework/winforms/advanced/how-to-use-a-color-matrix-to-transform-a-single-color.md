---
title: "Como usar uma matriz de cores para transformar uma única cor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60da29b60d2b9b5b98c76a0a9c3ae73ac9142bbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="ab132-102">Como usar uma matriz de cores para transformar uma única cor</span><span class="sxs-lookup"><span data-stu-id="ab132-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ab132-103">fornece o <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> classes para armazenar e manipular imagens.</span><span class="sxs-lookup"><span data-stu-id="ab132-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="ab132-104"><xref:System.Drawing.Image>e <xref:System.Drawing.Bitmap> objetos armazenam a cor de cada pixel como um número de 32 bits: 8 bits para vermelho, verde, azul e alfa.</span><span class="sxs-lookup"><span data-stu-id="ab132-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="ab132-105">Cada um dos quatro componentes é um número de 0 a 255, sendo que 0 representa nenhuma intensidade e 255 representa intensidade total.</span><span class="sxs-lookup"><span data-stu-id="ab132-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="ab132-106">O componente alfa especifica a transparência da cor: 0 é completamente transparente e 255 é totalmente opaca.</span><span class="sxs-lookup"><span data-stu-id="ab132-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="ab132-107">Um vetor de cor é uma tupla de 4 do formulário (vermelho, verde, azul, alfa).</span><span class="sxs-lookup"><span data-stu-id="ab132-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="ab132-108">Por exemplo, o vetor de cor (0, 255, 0, 255) representa uma cor opaca que não tem nenhum vermelho nem azul, mas tem verde na intensidade total.</span><span class="sxs-lookup"><span data-stu-id="ab132-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="ab132-109">Outra convenção para representar cores usa o número 1 para intensidade total.</span><span class="sxs-lookup"><span data-stu-id="ab132-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="ab132-110">Usando essa convenção, a cor descrita no parágrafo anterior seria representada pelo vetor (0, 1, 0, 1).</span><span class="sxs-lookup"><span data-stu-id="ab132-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> <span data-ttu-id="ab132-111">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] usa a convenção de 1 como intensidade total quando executa transformações de cor.</span><span class="sxs-lookup"><span data-stu-id="ab132-111">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="ab132-112">Você pode aplicar transformações lineares (rotação, colocação em escala e assim por diante) em vetores de cor multiplicando os vetores de cor por uma matriz de 4 x 4.</span><span class="sxs-lookup"><span data-stu-id="ab132-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="ab132-113">No entanto, você não pode usar uma matriz de 4 x 4 para realizar uma translação (não linear).</span><span class="sxs-lookup"><span data-stu-id="ab132-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="ab132-114">Se você adicionar uma quinta coordenada fictícia (por exemplo, o número 1) a cada um dos vetores de cor, poderá usar uma matriz de 5 × 5 para aplicar qualquer combinação de transformações lineares e translações.</span><span class="sxs-lookup"><span data-stu-id="ab132-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="ab132-115">Uma transformação que consiste em uma transformação linear seguida por uma translação é chamada de transformação afim.</span><span class="sxs-lookup"><span data-stu-id="ab132-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="ab132-116">Por exemplo, suponha que você queira começar com a cor (0,2, 0,0, 0,4, 1,0) e aplicar as seguintes transformações:</span><span class="sxs-lookup"><span data-stu-id="ab132-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="ab132-117">Duplicar o componente vermelho</span><span class="sxs-lookup"><span data-stu-id="ab132-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="ab132-118">Adicionar 0,2 aos componentes vermelhos, verdes e azuis</span><span class="sxs-lookup"><span data-stu-id="ab132-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="ab132-119">A multiplicação de matriz a seguir executará o par de transformações na ordem listada.</span><span class="sxs-lookup"><span data-stu-id="ab132-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="ab132-120">![Recolorindo](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="ab132-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="ab132-121">Os elementos de uma matriz de cores são indexados (baseados em zero) por linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="ab132-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="ab132-122">Por exemplo, a entrada na quinta linha e na terceira coluna da matriz M é indicada por M[4][2].</span><span class="sxs-lookup"><span data-stu-id="ab132-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="ab132-123">A matriz de identidade 5 × 5 (mostrada na ilustração a seguir) tem 1s na diagonal e 0s em todos os outros lugares.</span><span class="sxs-lookup"><span data-stu-id="ab132-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="ab132-124">Se você multiplicar um vetor de cor pela matriz de identidade, o vetor de cor não mudará.</span><span class="sxs-lookup"><span data-stu-id="ab132-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="ab132-125">Uma maneira conveniente de formar a matriz de uma transformação de cor é começar com a matriz de identidade e fazer uma pequena alteração que produza a transformação desejada.</span><span class="sxs-lookup"><span data-stu-id="ab132-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="ab132-126">![Recolorindo](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="ab132-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="ab132-127">Para uma discussão mais detalhada de matrizes e transformações, consulte [Sistemas de coordenadas e transformações](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="ab132-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab132-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab132-128">Example</span></span>  
 <span data-ttu-id="ab132-129">O exemplo a seguir usa uma imagem toda de uma cor (0,2, 0,0, 0,4, 1,0) e aplica a transformação descrita nos parágrafos anteriores.</span><span class="sxs-lookup"><span data-stu-id="ab132-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="ab132-130">A ilustração a seguir mostra a imagem original à esquerda e a imagem transformada à direita.</span><span class="sxs-lookup"><span data-stu-id="ab132-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="ab132-131">![Cores](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="ab132-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="ab132-132">O código no exemplo a seguir usa as seguintes etapas para recolorir:</span><span class="sxs-lookup"><span data-stu-id="ab132-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="ab132-133">Inicializar um <xref:System.Drawing.Imaging.ColorMatrix> objeto.</span><span class="sxs-lookup"><span data-stu-id="ab132-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="ab132-134">Criar um <xref:System.Drawing.Imaging.ImageAttributes> do objeto e passar o <xref:System.Drawing.Imaging.ColorMatrix> do objeto para o <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> método o <xref:System.Drawing.Imaging.ImageAttributes> objeto.</span><span class="sxs-lookup"><span data-stu-id="ab132-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="ab132-135">Passar o <xref:System.Drawing.Imaging.ImageAttributes> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="ab132-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab132-136">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ab132-136">Compiling the Code</span></span>  
 <span data-ttu-id="ab132-137">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ab132-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab132-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab132-138">See Also</span></span>  
 [<span data-ttu-id="ab132-139">Recolorindo Imagens</span><span class="sxs-lookup"><span data-stu-id="ab132-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="ab132-140">Sistemas de Coordenadas e Transformações</span><span class="sxs-lookup"><span data-stu-id="ab132-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)