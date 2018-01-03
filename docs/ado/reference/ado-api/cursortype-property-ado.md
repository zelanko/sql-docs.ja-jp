---
title: "カーソル プロパティ (ADO) |。Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset15::CursorType
helpviewer_keywords: CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 605fd338c9a5f41a893eccc885a610770c4e37bc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="cursortype-property-ado"></a>カーソル。 プロパティ (ADO)
使用されているカーソルの種類を示す、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)値。 既定値は**adOpenForwardOnly**です。  
  
## <a name="remarks"></a>解説  
 使用して、**カーソル。**プロパティを開くときに使用するカーソルの種類を指定する、 **Recordset**オブジェクト。  
  
 設定のみ**adOpenStatic**がサポートされる場合、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されている**adUseClient**です。 サポートされていない値が設定されている場合、エラーは発生しません。サポートされている最も近い**カーソル。**が使用されます。  
  
 プロバイダーが、要求されたカーソルの種類をサポートしていない場合は、別のカーソルの種類を返すこと可能性があります。 **カーソル。**実際のカーソルの種類に一致するプロパティが変更に使用する場合、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトが開いています。 返されるカーソルの特定の機能を確認するため、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドです。 閉じた後、 **Recordset**、**カーソル。**プロパティは元の設定に戻ります。  
  
 次の表は、プロバイダーの機能を示します (で識別される**サポート**メソッド定数) 各カーソルの種類に必要なです。  
  
|このカーソル。 のレコード セット|サポートするメソッドは、すべてこれらの定数の True 返す必要があります。|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|なし|  
|**adOpenKeyset**|**adBookmark**、 **adHoldRecords**、 **adMovePrevious**、 **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**、 **adHoldRecords**、 **adMovePrevious**、 **adResync**|  
  
> [!NOTE]
>  **サポート**(**adUpdateBatch**) バッチを更新するのに、動的かつ順方向専用カーソルの場合は true。 可能性があります、keyset または static カーソルを使用する必要があります。 設定、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)プロパティを**adLockBatchOptimistic**と**CursorLocation**プロパティを**adUseClient**カーソルを有効にするにはOLE DB では、バッチ更新に必要なサービス。  
  
 **カーソル。**プロパティが読み取り/書き込み時に、 **Recordset**が開いているときにが閉じており、読み取り専用です。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**レコード セット**オブジェクト、**カーソル。**プロパティはにのみ設定できます**adOpenStatic**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [カーソル。、LockType、および EditMode のプロパティの例 (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [カーソル。、LockType、および EditMode のプロパティの例 (vc++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports メソッド](../../../ado/reference/ado-api/supports-method.md)
