---
title: "Delete メソッド (ADO レコード セット) |Microsoft ドキュメント"
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
f1_keywords:
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords: Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ff78b2827f8bd6aa22ded6429f0468617b7a83d9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="delete-method-ado-recordset"></a>Delete メソッド (ADO レコード セット)
現在のレコードまたはレコードのグループを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 [AffectEnum](../../../ado/reference/ado-api/affectenum.md)レコードの数を決定する値、**削除**メソッドに影響します。 既定値は**adAffectCurrent**です。  
  
> [!NOTE]
>  **adAffectAll**と**呼び出します**に有効な引数ではなく**削除**です。  
  
## <a name="remarks"></a>解説  
 使用して、**削除**メソッドは、現在のレコードまたはレコードのグループを示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトを削除します。 場合、 **Recordset**オブジェクトはレコードの削除を許可しないエラーが発生します。 即時更新モードの場合は、削除はすぐに、データベースで発生します。 呼び出し後に、レコードが編集モードのままは場合 (たとえば、データベース整合性違反) のため、レコードが正常に削除できません、[更新](../../../ado/reference/ado-api/update-method.md)です。 つまりの更新をキャンセルする必要があります[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)現在のレコードから移動する前に (たとえば、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)、[移動](../../../ado/reference/ado-api/move-method-ado.md)、または[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md))。  
  
 バッチ更新モードの場合は、レコードがキャッシュからの削除とマークされてし、実際の削除の動作を呼び出すとき、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドです。 使用して、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを削除したレコードを表示します。  
  
 削除されたレコードからフィールドの値を取得するには、エラーが生成されます。 現在のレコードを削除すると、削除されたレコードのまま別のレコードに移動するまでです。 移動した後、削除されたレコードからアクセスできなくなります。  
  
 トランザクションで、入れ子にする場合は、削除されたレコードを回復することができます、 [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッドです。 バッチ更新モードである場合は、保留中の削除または保留中の削除とのグループを取り消すことができます、 [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドです。  
  
 基になるデータとの競合のためのレコードを削除する試行が失敗した場合 (たとえば、レコードが別のユーザーによって既に削除されている場合)、プロバイダーに警告を返し、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクション プログラムは停止されませんが、実行します。 要求されたすべてのレコードの競合がある場合にのみ、実行時エラーが発生します。  
  
 場合、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)動的プロパティを設定すると、および**レコード セット**は、複数のテーブルに対して結合操作を実行した結果、**削除**メソッドはのみを削除指定したテーブルから行、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)プロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) の削除します。](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [メソッドの例 (VBScript) の削除します。](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [メソッドの例 (vc++) を削除します。](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [Delete メソッド (ADO フィールドのコレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO パラメーターのコレクション)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DeleteRecord メソッド (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
