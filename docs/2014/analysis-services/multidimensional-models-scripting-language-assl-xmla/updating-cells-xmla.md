---
title: セル (XMLA) の更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f2a4a8976602080f28f736814783397bc6611e64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175038"
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  使用することができます、 [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md)キューブの書き戻しを有効になっているキューブ内の 1 つまたは複数のセルの値を変更するコマンド。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 更新するセルを含む各パーティション用の別個の書き戻しテーブルに更新された情報を格納します。  
  
> [!NOTE]  
>  `UpdateCells` コマンドは、キューブ書き戻し時の割り当てをサポートしません。 書き戻しの割り当てを使用する必要がありますを使用する、[ステートメント](../xmla/xml-elements-commands/statement-element-xmla.md)多次元式 (MDX) UPDATE ステートメントを送信するコマンド。 詳細については、次を参照してください。 [UPDATE CUBE ステートメント&#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)です。  
  
## <a name="specifying-cells"></a>セルの指定  
 [セル](../xmla/xml-elements-properties/cell-element-xmla.md)のプロパティ、`UpdateCells`コマンドには、更新されるセルが含まれています。 `Cell` プロパティ内の各セルは、セルの序数を使用して識別します。 概念的には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合と同様、キューブのキューブ内のセルに番号、 *p*-次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数位置を計算する数式](../../../2014/analysis-services/dev-guide/media/cellordinalformula.gif "をセルの序数位置を計算する式")  
  
 セルの序数がわかれば、内のセルの目的の値を指定することができます、[値](../xmla/xml-elements-properties/value-element-xmla.md)のプロパティ、[セル](../xmla/xml-elements-properties/cell-element-xmla.md)プロパティです。  
  
## <a name="see-also"></a>参照  
 [Update 要素&#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
