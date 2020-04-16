---
title: セルの更新 (XMLA) |マイクロソフトドキュメント
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
ms.openlocfilehash: f0eab50aa7e70aedee93eef2cefee648e6ceb5c9
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387892"
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  [[UpdateCells]](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)コマンドを使用すると、キューブの書き戻しが有効になっているキューブ内の 1 つ以上のセルの値を変更できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]更新されるセルを含むパーティションごとに、更新された情報を個別の書き戻しテーブルに格納[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。  
  
> [!NOTE]  
>  `UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。 割り当てられた書き戻しを使用するには、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)コマンドを使用してマルチディメンション式 (MDX) UPDATE ステートメントを送信する必要があります。 詳細については、「[キューブ ステートメントの更新 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)」を参照してください。  
  
## <a name="specifying-cells"></a>セルの指定  
 コマンドの[Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) `UpdateCells`プロパティには、更新するセルが含まれています。 `Cell` プロパティ内の各セルは、セルの序数を使用して識別します。 概念的[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]には、キューブ内のセルに、まるで*p*次元配列 *(p*軸の数) のように番号を付けます。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数の位置を計算する式](../../analysis-services/dev-guide/media/cellordinalformula.gif "セルの序数の位置を計算する式")  
  
 セルの序数がわかったら[、Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)プロパティの[Value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)プロパティでセルの目的の値を指定できます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;要素の更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
