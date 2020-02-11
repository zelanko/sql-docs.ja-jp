---
title: CancelBatch メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f1c6a9f57d30b47641b9280e25a97336c28b0496
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920169"
---
# <a name="cancelbatch-method-ado"></a>CancelBatch メソッド (ADO)
保留中のバッチ更新をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>パラメーター  
 *影響のあるレコード*  
 省略可能。 **CancelBatch**メソッドが影響するレコードの数を示す[AffectEnum](../../../ado/reference/ado-api/affectenum.md)値。  
  
## <a name="remarks"></a>解説  
 バッチ更新モードで[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)内の保留中の更新を取り消すには、 **CancelBatch**メソッドを使用します。 **レコードセット**が即時更新モードである場合、 **AdCancelBatch**が**current**を指定せずにを呼び出すと、エラーが生成されます。  
  
 現在のレコードを編集している場合、または**CancelBatch**を呼び出したときに新しいレコードを追加している場合、ADO は最初に[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッドを呼び出して、キャッシュされた変更を取り消します。 その後、**レコードセット**内のすべての保留中の変更が取り消されます。  
  
 **CancelBatch**呼び出しの後に現在のレコードがわからないされている可能性があります。特に、新しいレコードを追加するプロセスを実行していた場合に発生します。 このため、 **CancelBatch**の呼び出し後に、レコード**セット**内の既知の場所に現在のレコードの位置を設定することは賢明です。 たとえば、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドを呼び出します。  
  
 基になるデータと競合しているために保留中の更新をキャンセルしようとした場合 (たとえば、別のユーザーによってレコードが削除された場合)、プロバイダは[Errors](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションに警告を返しますが、プログラムの実行を停止することはありません。 実行時エラーは、要求されたすべてのレコードに競合がある場合にのみ発生します。 [フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**AdFilterAffectedRecords**) と[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティを使用して、競合しているレコードを検索します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [UpdateBatch および CancelBatch メソッドの例 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch および CancelBatch メソッドの例 (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelUpdate メソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate メソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
