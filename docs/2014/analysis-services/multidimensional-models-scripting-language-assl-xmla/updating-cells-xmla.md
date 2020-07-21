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
ms.openlocfilehash: 2c3d9a7c27533666c75102d9eac3b8311bfe4af6
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544916"
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)コマンドを使用すると、キューブの書き戻しが有効になっているキューブ内の1つ以上のセルの値を変更できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] されるセルを含むパーティションごとに、更新された情報を個別の書き戻しテーブルに格納します。  
  
> [!NOTE]  
>  `UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。 割り当てられた書き戻しを使用するには、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用して多次元式 (MDX) の UPDATE ステートメントを送信する必要があります。 詳細については、「 [UPDATE CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)」を参照してください。  
  
## <a name="specifying-cells"></a>セルの指定  
 コマンドの[Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)プロパティには `UpdateCells` 、更新するセルが含まれています。 `Cell` プロパティ内の各セルは、セルの序数を使用して識別します。 概念的には、キューブが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *p*次元配列であるかのように、キューブ内のセルに数値が付けられます。ここで、 *p*は軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数の位置を計算する式](../../analysis-services/dev-guide/media/cellordinalformula.gif "セルの序数の位置を計算する式")  
  
 セルの序数がわかれば、そのセルの目的の値を[セルプロパティの](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)プロパティで示すことができます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;の要素の更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
