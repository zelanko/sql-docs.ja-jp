---
title: UpdateBatch メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::UpdateBatch
- Recordset15::raw_UpdateBatch
helpviewer_keywords:
- UpdateBatch method [ADO]
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e9d74fe938ce486a4cd15573af8166dbed12ba6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937840"
---
# <a name="updatebatch-method"></a>UpdateBatch メソッド
すべての保留中のバッチ更新をディスクに書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.UpdateBatch AffectRecords, PreserveStatus  
```  
  
#### <a name="parameters"></a>パラメーター  
 *影響のあるレコード*  
 省略可能。 **UpdateBatch**メソッドが影響するレコードの数を示す[AffectEnum](../../../ado/reference/ado-api/affectenum.md)値です。  
  
 *PreserveStatus*  
 省略可能。 [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティによって示されるローカルの変更をコミットする必要があるかどうかを指定する**ブール**値です。 この値が**True**に設定されている場合、更新が完了した後も、各レコードの**Status**プロパティは変更されません。  
  
## <a name="remarks"></a>解説  
 バッチ更新モードで**レコードセット**オブジェクトを変更する場合は、 **UpdateBatch**メソッドを使用して、**レコードセット**オブジェクトに加えられたすべての変更を基になるデータベースに転送します。  
  
 **レコードセット**オブジェクトでバッチ更新がサポートされている場合は、 **UpdateBatch**メソッドを呼び出すまで、1つ以上のレコードに対して複数の変更をローカルにキャッシュできます。 現在のレコードを編集している場合、または**UpdateBatch**メソッドを呼び出したときに新しいレコードを追加している場合、ADO は[Update](../../../ado/reference/ado-api/update-method.md)メソッドを自動的に呼び出して、保留中の変更を現在のレコードに保存してから、バッチされた変更をプロバイダーに送信します。 バッチ更新は、キーセットまたは静的カーソルのいずれかでのみ使用してください。  
  
> [!NOTE]
>  **Adを**このパラメーターの値として指定すると、現在の**レコードセット**(レコードが一致しないフィルターなど) に表示されているレコードがない場合にエラーが発生します。  
  
 基になるデータとの競合 (たとえば、レコードが別のユーザーによって既に削除されているなど) が原因で、いずれかのレコードまたはすべてのレコードに対して変更を送信しようとして失敗した場合、プロバイダーは[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションに警告を返し、実行時エラーが発生します。 [フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**AdFilterAffectedRecords**) と[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティを使用して、競合しているレコードを検索します。  
  
 保留中のバッチの更新をすべて取り消すには、 [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドを使用します。  
  
 一意の[テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と更新の再[同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)の動的プロパティが設定されていて、**レコードセット**が複数のテーブルに対して結合操作を実行した結果である場合、更新の再[同期](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)プロパティの設定に応じて、 **UpdateBatch**メソッドの実行には暗黙的に再[同期](../../../ado/reference/ado-api/resync-method.md)メソッドが適用されます。  
  
 バッチの個々の更新がデータソースで実行される順序は、ローカル**レコードセット**で実行された順序と同じである必要はありません。 更新順序はプロバイダに依存します。 Insert または update の foreign key 制約など、相互に関連する更新をコーディングする場合は、このことを考慮してください。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [UpdateBatch および CancelBatch メソッドの例 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch および CancelBatch メソッドの例 (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)
