---
title: LockType プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f981f14e4eedb9dad3724f91c5ce70f6535ee0a7
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279231"
---
# <a name="locktype-property-ado"></a>LockType プロパティ (ADO)
編集中のレコードに置かれたロックの種類を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)値。 既定値は**adLockReadOnly**です。  
  
## <a name="remarks"></a>コメント  
 設定、 **LockType**プロパティを開く前に、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)を開くときにプロバイダーのロックの種類を使用する必要がありますを指定します。 開いている上で使用されているロックの種類を取得するプロパティを読み取る**Recordset**オブジェクト。  
  
 プロバイダーはすべてのロックの種類をサポートしていません。 プロバイダーをサポートして、要求された場合**LockType**設定すると、別の種類のロックが代用されます。 使用可能な実際のロック機能を決定する、**レコード セット**オブジェクトを使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを**adUpdate**と**adUpdateBatch**.  
  
 **AdLockPessimistic**場合の設定はサポートされていません、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されている**adUseClient**です。 サポートされていない値が設定されている場合、エラーは発生しません。サポートされている最も近い**LockType**が使用されます。  
  
 **LockType**プロパティが読み取り/書き込み時に、 **Recordset**が開いているときに閉じており、読み取り専用です。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**クライアント側で使用すると**レコード セット**オブジェクト、 **LockType**プロパティのみ設定できます**adLockBatchOptimistic**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [カーソル。、LockType、および EditMode のプロパティの例 (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [カーソル。、LockType、および EditMode のプロパティの例 (vc++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
