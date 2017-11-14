---
title: "UpdateBatch メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57c85b6ed83792e2e489eb91dab59bd0da598939
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatebatch-method"></a>UpdateBatch メソッド
すべての保留中のバッチ更新プログラムをディスクに書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 省略可。 [AffectEnum](../../../ado/reference/ado-api/affectenum.md)レコードの数を示す値、 **UpdateBatch**メソッドに影響します。  
  
 *PreserveStatus*  
 省略可。 A**ブール**によって示されるローカルが変更されたかどうかを指定する値、[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティをコミットする必要があります。 この値が設定されている場合**True**、**ステータス**更新が完了したら、各レコードのプロパティは変更されません。  
  
## <a name="remarks"></a>解説  
 使用して、 **UpdateBatch**メソッドを変更する場合、**レコード セット**で行われたすべての変更を送信するバッチ更新モードでのオブジェクト、**レコード セット**を基になるデータベース オブジェクトです。  
  
 場合、 **Recordset**オブジェクトは、バッチ更新をサポートしている、1 つまたは複数のレコードを複数の変更をキャッシュするには、ローカルで呼び出されるまで、 **UpdateBatch**メソッドです。 現在のレコードを編集または呼び出すときに、新しいレコードを追加する場合、 **UpdateBatch**メソッド、ADO の呼び出しは自動的に、[更新](../../../ado/reference/ado-api/update-method.md)する前に現在のレコードに保留中の変更を保存する方法プロバイダーにバッチ処理された変更を送信します。 バッチ更新を keyset または static カーソルのみを使用する必要があります。  
  
> [!NOTE]
>  指定する**adAffectGroup**現在表示されているレコードがない場合にこのパラメーターの値が、エラー発生は**Recordset** (レコードが一致しないフィルター) などです。  
  
 基になるデータとの競合が原因またはすべてのレコードの変更の転送に失敗した場合 (たとえば、レコードが別のユーザーによって既に削除されている場合)、プロバイダーに警告を返し、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションおよび実行時エラーが発生します。 使用して、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**adFilterAffectedRecords**) および[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)競合しているレコードを検索するプロパティです。  
  
 保留中のすべてのバッチ更新をキャンセルするには、使用、 [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドです。  
  
 場合、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と[更新プログラムが再同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)動的なプロパティを設定すると、および**レコード セット**は、複数のテーブルに対して結合操作を実行した結果、実行、 **UpdateBatch**メソッドが暗黙的に続けて、[再同期](../../../ado/reference/ado-api/resync-method.md)の設定によって、メソッド、[更新プログラムが再同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)プロパティです。  
  
 バッチ内の個々 の更新プログラムが、データ ソースで実行される順序は必ずしもそれらがローカルに実行された順序と同じ**Recordset**です。 更新プログラムの順序は、プロバイダーによって異なります。 この点を考慮、insert または update に対する外部キー制約など、互いに関連する更新プログラムをコーディングするとき。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [UpdateBatch と CancelBatch メソッドの例 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch と CancelBatch メソッドの例 (vc++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)

