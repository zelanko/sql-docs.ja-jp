---
title: CursorTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 059d6bb8e621839ccf21bb4eb4251db08f427523
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761400"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
使用するカーソルの種類を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|動的カーソルを使用します。 追加、変更、および他のユーザーによって削除が表示されて、すべての種類内の移動の**レコード セット**は許可されて、ブックマーク、を除き、プロバイダーをサポートしていない場合。|  
|**adOpenForwardOnly**|0|既定値です。 順方向専用カーソルを使用します。 静的カーソルと同じですが、レコードを前方スクロールできますのみ。 これは、1 つだけを通過する必要があるときにパフォーマンスが向上する**Recordset**します。|  
|**adOpenKeyset**|1|キーセット カーソルを使用します。 など、動的カーソルの点が異なりますが、他のユーザーを削除するレコードはからアクセスできる他のユーザーを追加するレコードを参照してくださいことはできません、 **Recordset**します。 他のユーザーによるデータの変更は、表示されています。|  
|**adOpenStatic**|3|静的カーソルは、一連のデータの検索やレポートの生成に使用できるレコードの静的コピーを使用します。 追加、変更、または他のユーザーによって削除には表示されません。|  
|**adOpenUnspecified**|-1|カーソルの種類を指定しません。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
 [CursorType プロパティ (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
