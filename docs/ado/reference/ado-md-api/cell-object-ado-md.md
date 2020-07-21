---
title: Cell オブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
author: rothja
ms.author: jroth
ms.openlocfilehash: d309ba98c1e50d8eb6fbe47fb9452f8ea7df35ba
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761800"
---
# <a name="cell-object-ado-md"></a>Cell オブジェクト (ADO MD)
セルセットに含まれる軸の座標の交差部分にあるデータを表します。  
  
## <a name="remarks"></a>解説  
 セルオブジェクトは、**セル**[セット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトの[Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティによって返されます。  
  
 **Cell**オブジェクトのコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Value](../../../ado/reference/ado-md-api/value-property-ado-md.md)プロパティを持つ**セル**のデータを返します。  
  
-   [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md)プロパティを使用して、 **Value**プロパティの書式設定された表示を表す文字列を返します。  
  
-   [Ordinal](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md)プロパティを持つセル**セット**内の**セル**の序数値を返します。  
  
-   [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)内の**セル**の位置[を、position コレクションと](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)共に決定します。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、**セル**に関する他の情報を取得します。  
  
 **Properties**コレクションには、プロバイダーが提供するプロパティが含まれています。 次の表に、使用可能なプロパティを示します。 実際のプロパティリストは、プロバイダーの実装によって異なる場合があります。 使用できるプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|色|セルを表示するときに使用する背景色。|  
|FontFlags|フォントに対する影響の詳細を示すビットマスク。|  
|FontName|セル値を表示するために使用されるフォントです。|  
|フォントサイズ|セル値を表示するために使用されるフォントサイズ。|  
|前景色|セルを表示するときに使用する前景色。|  
|FormatString|書式設定された文字列の値。|  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Axis の例 (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [位置コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
