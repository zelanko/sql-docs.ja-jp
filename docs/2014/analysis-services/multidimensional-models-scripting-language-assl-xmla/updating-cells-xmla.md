---
title: セルの更新 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
ms.openlocfilehash: 6237bb773709aa7f5eb8bc29fa2436bf69b08030
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146037"
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  使用することができます、 [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)キューブの書き戻しを有効になっているキューブ内の 1 つまたは複数のセルの値を変更するコマンド。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 更新対象のセルを含む各パーティション用の別個の書き戻しテーブルには、更新された情報を格納します。  
  
> [!NOTE]  
>  `UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。 書き戻しの割り当てを使用する必要がありますを使用する、[ステートメント](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)多次元式 (MDX) UPDATE ステートメントを送信するコマンド。 詳細については、[UPDATE CUBE ステートメント&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)を参照してください。  
  
## <a name="specifying-cells"></a>セルの指定  
 [セル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)のプロパティ、`UpdateCells`コマンドには、更新するセルが含まれています。 `Cell` プロパティ内の各セルは、セルの序数を使用して識別します。 概念的には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合と同様、キューブ、キューブ内のセルの番号、 *p*-次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数位置を計算する式を](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "セルの序数位置を計算する式")  
  
 セルの序数がわかれば、内のセルの目的の値を指定することができます、[値](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)のプロパティ、[セル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)プロパティ。  
  
## <a name="see-also"></a>参照  
 [Update 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
