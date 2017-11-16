---
title: "セル (XMLA) の更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57edea50d67fa52de99f92b85b40bcd5caf307fb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  使用することができます、 [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)キューブの書き戻しを有効になっているキューブ内の 1 つまたは複数のセルの値を変更するコマンド。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を更新するセルを含む各パーティション用の別個の書き戻しテーブルに更新された情報を格納します。  
  
> [!NOTE]  
>  **UpdateCells**コマンドで、キューブ書き戻し時の割り当てがサポートされていません。 書き戻しの割り当てを使用する必要がありますを使用する、[ステートメント](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)多次元式 (MDX) UPDATE ステートメントを送信するコマンド。 詳細については、次を参照してください。 [UPDATE CUBE ステートメント & #40 です。MDX と #41 です。](../../mdx/mdx-data-manipulation-update-cube.md).  
  
## <a name="specifying-cells"></a>セルの指定  
 [セル](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)のプロパティ、 **UpdateCells**コマンドには、更新されるセルが含まれています。 内の各セルを識別する、**セル**そのセルの序数を使用してプロパティです。 概念的には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合と同様、キューブのキューブ内のセルに番号、 *p*-次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数位置を計算する数式](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "をセルの序数位置を計算する式")  
  
 セルの序数がわかれば、内のセルの目的の値を指定することができます、[値](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)のプロパティ、[セル](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)プロパティです。  
  
## <a name="see-also"></a>参照  
 [Update 要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

