---
title: "メソッドを再同期 |Microsoft ドキュメント"
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
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 392dd82f2b6412c537a86cc68331cffc852069b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="resync-method"></a>メソッドを再同期します。
現在のデータを更新[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、または[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)基になるデータベースからのオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 省略可。 [AffectEnum](../../../ado/reference/ado-api/affectenum.md)レコードの数を決定する値、**再同期**メソッドに影響します。 既定値は**adAffectAll**です。 この値では使用できない、**再同期**のメソッド、**フィールド**のコレクション、**レコード**オブジェクト。  
  
 *ResyncValues*  
 省略可。 A [ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)基になる値が上書きされるかどうかを指定する値。 既定値は**adResyncAllValues**です。  
  
## <a name="remarks"></a>解説  
  
## <a name="recordset"></a>レコードセット  
 使用して、**再同期**メソッド、現在のレコードを再同期を**レコード セット**基になるデータベースとします。 これは、機能は、基になるデータベースの変更を表示するか、静的または順方向専用カーソルを使用している場合に便利です。  
  
 設定した場合、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**、**再同期**でのみ使用読み取り専用ではない**Recordset**オブジェクト。  
  
 異なり、 [Requery](../../../ado/reference/ado-api/requery-method.md) 、メソッド、**再同期**メソッドが再実行されない、**レコード セット**オブジェクトには、コマンドの基になります。 基になるデータベースの新しいレコードは表示されません。  
  
 基になるデータとの競合により再同期を実行しようとするが失敗したかどうか (たとえば、レコードが削除されました別のユーザーによって)、プロバイダーに警告が返さ、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションと、実行時エラーが発生します。 使用して、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**競合**) および[ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)競合しているレコードを検索するプロパティです。  
  
 場合、[一意テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と[コマンドを再同期](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)動的プロパティを設定し、**レコード セット**して、複数のテーブルから、に対して結合操作の実行結果は、**再同期**メソッドで指定されたコマンドを実行、**コマンドを再同期**プロパティで指定したテーブルでのみ、**一意テーブル**プロパティです。  
  
## <a name="fields"></a>フィールド  
 使用して、**再同期**の値を再同期する方法、**フィールド**のコレクション、**レコード**基になるデータ ソースを持つオブジェクト。 [カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティがこのメソッドによって影響を受けません。  
  
 場合*ResyncValues*に設定されている**adResyncAllValues** (既定値)、 [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)、[値](../../../ado/reference/ado-api/value-property-ado.md)、および[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)プロパティの[フィールド](../../../ado/reference/ado-api/field-object.md)コレクション内のオブジェクトが同期されます。 場合*ResyncValues*に設定されている**処理**、のみ、 **UnderlyingValue**プロパティが同期されています。  
  
 値、**ステータス**それぞれのプロパティ**フィールド**呼び出し時にオブジェクトの動作にも影響**再同期**です。 **フィールド**を持つオブジェクト**ステータス**値**adFieldPendingUnknown**または**adFieldPendingInsert**、**再同期**も何も起こりません。 **ステータス**の値**adFieldPendingChange**または**adFieldPendingDelete**、**再同期**フィールドのデータ値を同期します。データ ソースに存在します。  
  
 **再同期**が変更されない**ステータス**の値**フィールド**オブジェクトをエラーが発生しない限り、ときに**再同期**と呼びます。 たとえば、フィールドが存在しない場合、プロバイダーは返す適切な**ステータス**値を**フィールド**などのオブジェクト**adFieldDoesNotExist**です。 返される**ステータス**の値の中で、値を論理的に結合できます、**ステータス**プロパティです。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) を再同期します。](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [メソッドの例 (vc++) を再同期します。](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [UnderlyingValue プロパティ](../../../ado/reference/ado-api/underlyingvalue-property.md)

