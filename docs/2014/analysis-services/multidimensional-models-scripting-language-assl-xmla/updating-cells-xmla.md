---
title: セルの更新 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71279981c5fd3879d633e0fdd8cdec74bed6deac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887709"
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)コマンドを使用すると、キューブの書き戻しが有効になっているキューブ内の1つ以上のセルの値を変更できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]更新されるセルを含むパーティションごとに、更新された情報を個別の書き戻しテーブルに格納し[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ます。  
  
> [!NOTE]  
>  
  `UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。 割り当てられた書き戻しを使用するには、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用して多次元式 (MDX) の UPDATE ステートメントを送信する必要があります。 詳細については、「 [UPDATE CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)」を参照してください。  
  
## <a name="specifying-cells"></a>セルの指定  
 コマンドの Cell プロパティには、更新するセルが含まれています。 [](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) `UpdateCells` 
  `Cell` プロパティ内の各セルは、セルの序数を使用して識別します。 概念的に[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、キューブが*p*次元配列であるかのように、キューブ内のセルに数値が付けられます。ここで、 *p*は軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数の位置を計算する式](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/cellordinalformula.gif "セルの序数の位置を計算する式")  
  
 セルの序数がわかれば、そのセルの目的の値を[セルプロパティの](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)プロパティで示すことができます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;の要素の更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
