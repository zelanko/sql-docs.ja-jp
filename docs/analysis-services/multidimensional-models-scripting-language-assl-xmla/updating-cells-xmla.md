---
title: セル (XMLA) の更新 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9458e2fb58a3e1fe7806db1bb27147561ef94e5d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="updating-cells-xmla"></a>セルの更新 (XMLA)
  使用することができます、 [UpdateCells](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)キューブの書き戻しを有効になっているキューブ内の 1 つまたは複数のセルの値を変更するコマンド。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 更新するセルを含む各パーティション用の別個の書き戻しテーブルに更新された情報を格納します。  
  
> [!NOTE]  
>  **UpdateCells**コマンドで、キューブ書き戻し時の割り当てがサポートされていません。 書き戻しの割り当てを使用する必要がありますを使用する、[ステートメント](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)多次元式 (MDX) UPDATE ステートメントを送信するコマンド。 詳細については、次を参照してください。 [UPDATE CUBE ステートメント & #40 です。MDX と #41 です。](../../mdx/mdx-data-manipulation-update-cube.md)  
  
## <a name="specifying-cells"></a>セルの指定  
 [セル](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)のプロパティ、 **UpdateCells**コマンドには、更新されるセルが含まれています。 内の各セルを識別する、**セル**そのセルの序数を使用してプロパティです。 概念的には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]場合と同様、キューブのキューブ内のセルに番号、 *p*-次元の配列を*p*軸の数です。 セルは、行優先順で指定されます。 次の図は、セルの序数を計算するための公式を示しています。  
  
 ![セルの序数位置を計算する数式](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/media/cellordinalformula.gif "をセルの序数位置を計算する式")  
  
 セルの序数がわかれば、内のセルの目的の値を指定することができます、[値](../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)のプロパティ、[セル](../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)プロパティです。  
  
## <a name="see-also"></a>参照  
 [Update 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
