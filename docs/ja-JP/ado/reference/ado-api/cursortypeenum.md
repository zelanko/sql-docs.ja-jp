---
title: CursorTypeEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eabc0f3162645fdf526faff246937312a8a5b775
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="cursortypeenum"></a>CursorTypeEnum
使用するカーソルの種類を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|動的カーソルを使用します。 追加、変更、および他のユーザーによって削除が可視性、および内の移動の型はすべて、**レコード セット**は許可されて、ブックマークを除く場合は、プロバイダーはサポートされていません。|  
|**adOpenForwardOnly**|0|既定値です。 順方向専用カーソルを使用します。 カーソル、静的カーソルと同じすることができますのみ転送レコードをスクロールする点を除いてです。 これは、1 つだけを通過する必要があるときにパフォーマンスが向上する**Recordset**です。|  
|**adOpenKeyset**|1|キーセット カーソルを使用します。 動的カーソルなどの他のユーザーが削除したレコードはからアクセス可能ではないものの、他のユーザーを追加したレコードを参照してくださいできませんする点を除いて、 **Recordset**です。 他のユーザーがデータの変更は、表示されています。|  
|**adOpenStatic**|3|静的カーソルは、一連のデータの検索や、レポートの生成に使用できるレコードの静的コピーを使用します。 追加、変更、または他のユーザーによって削除は表示されません。|  
|**adOpenUnspecified**|-1|カーソルの種類は指定しません。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
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
