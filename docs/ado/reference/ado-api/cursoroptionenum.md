---
title: "CursorOptionEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: CursorOptionEnum
helpviewer_keywords: CursorOptionEnum enumeration [ADO]
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0076db0f4d9bcb1c85858bef763795cee1ba6754
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
どのような機能を指定、[サポート](../../../ado/reference/ado-api/supports-method.md)のメソッドをテストする必要があります。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adAddNew**|0x1000400|では、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)を新しいレコードを追加するメソッド。|  
|**adApproxPosition**|0x4000|では、 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)と[と、AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティです。|  
|**adBookmark**|0x2000|では、[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)特定のレコードにアクセスするプロパティです。|  
|**adDelete**|0x1000800|では、[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)レコードを削除するメソッド。|  
|**adFind**|0x80000|サポート、[検索](../../../ado/reference/ado-api/find-method-ado.md)を内の行を探す方法、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)です。|  
|**adHoldRecords**|0x100|複数のレコードを取得または保留中のすべての変更をコミットすることがなく、次の位置を変更します。|  
|**adIndex**|0x100000|では、[インデックス](../../../ado/reference/ado-api/index-property.md)インデックスの名前を付けるプロパティです。|  
|**adMovePrevious**|0x200|サポート、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)と[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッド、および[移動](../../../ado/reference/ado-api/move-method-ado.md)または[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)位置の前に、現在のレコードを移動するメソッドブックマークをせずにします。|  
|**adNotify**|0x40000|基になるデータ プロバイダーが通知をサポートしていることを示します (を決定するかどうか**Recordset**イベントがサポートされます)。|  
|**adResync**|0x20000|サポート、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドを基になるデータベースに表示されているデータでカーソルを更新します。|  
|**adSeek**|0x200000|サポート、[シーク](../../../ado/reference/ado-api/seek-method.md)を内の行を探す方法、 **Recordset**です。|  
|**adUpdate**|0x1008000|では、[更新](../../../ado/reference/ado-api/update-method.md)既存のデータを変更する方法です。|  
|**adUpdateBatch**|0x10000|バッチ更新をサポートしています ([UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)と[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッド)、プロバイダーへの変更のグループを送信します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.CursorOption.ADDNEW|  
|AdoEnums.CursorOption.APPROXPOSITION|  
|AdoEnums.CursorOption.BOOKMARK|  
|AdoEnums.CursorOption.DELETE|  
|AdoEnums.CursorOption.FIND|  
|AdoEnums.CursorOption.HOLDRECORDS|  
|AdoEnums.CursorOption.INDEX|  
|AdoEnums.CursorOption.MOVEPREVIOUS|  
|AdoEnums.CursorOption.NOTIFY|  
|AdoEnums.CursorOption.RESYNC|  
|AdoEnums.CursorOption.SEEK|  
|AdoEnums.CursorOption.UPDATE|  
|AdoEnums.CursorOption.UPDATEBATCH|  
  
## <a name="applies-to"></a>適用対象  
 [Supports メソッド](../../../ado/reference/ado-api/supports-method.md)
