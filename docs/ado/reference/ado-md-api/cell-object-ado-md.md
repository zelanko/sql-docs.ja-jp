---
title: "セルのオブジェクト (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cell
helpviewer_keywords:
- Cell object [ADO MD]
ms.assetid: dcc2f044-b785-4a29-9bc5-b673f66eedf9
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d6ef6e4e3cf888b60050bfd297863568d8112a57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="cell-object-ado-md"></a>セルのオブジェクト (ADO MD)
セル セットに含まれる軸座標の交差部分にデータを表します。  
  
## <a name="remarks"></a>解説  
 A**セル**によってオブジェクトが返される、[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)のプロパティ、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト。  
  
 コレクションのプロパティと、**セル**オブジェクトを次を行うことができます。  
  
-   内のデータを返す、**セル**で、[値](../../../ado/reference/ado-md-api/value-property-ado-md.md)プロパティです。  
  
-   表示の書式設定を表す文字列を返す、**値**を持つプロパティ、 [FormattedValue](../../../ado/reference/ado-md-api/formattedvalue-property-ado-md.md)プロパティです。  
  
-   序数値を返す、**セル**内で、**セルセット**で、[序数](../../../ado/reference/ado-md-api/ordinal-property-ado-md-cell.md)プロパティです。  
  
-   位置を決定、**セル**内で、 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)で、[位置](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)コレクション。  
  
-   に関するその他の情報を取得、**セル**標準 ado[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、利用可能なプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの完全な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|Description|  
|----------|-----------------|  
|背景色|セルを表示するときに使用する背景色です。|  
|FontFlags|フォントの効果を指定するビットマスク。|  
|フォント名|セルの値を表示するために使用するフォントです。|  
|フォントサイズ|セルの値を表示するために使用するフォント サイズ。|  
|前景色|セルを表示するときに使用する前景色。|  
|FormatString|書式設定された文字列の値です。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/cell-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [軸の例 (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [位置コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
