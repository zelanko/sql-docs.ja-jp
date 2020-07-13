---
title: Resync メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_Resync
- Fields::Resync
- Recordset20::Resync
- Fields::raw_Resync
helpviewer_keywords:
- Resync method [ADO]
ms.assetid: 73b355d4-a4c0-434b-bfc4-039b1c76b32e
author: rothja
ms.author: jroth
ms.openlocfilehash: 54c92fad618ffaad9b22a8ed73b287c0a5716959
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756310"
---
# <a name="resync-method"></a>Resync メソッド
基になるデータベースから、現在の[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトまたは[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの[Fields](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションのデータを更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Recordset.Resync AffectRecords, ResyncValues Record.Fields.Resync ResyncValues  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 任意。 再**同期**メソッドによって影響を受けるレコードの数を決定する[AffectEnum](../../../ado/reference/ado-api/affectenum.md)値。 既定値は**adAffectAll**です。 この値は、**レコード**オブジェクトの**Fields**コレクションの**Resync**メソッドでは使用できません。  
  
 *ResyncValues*  
 任意。 基になる値が上書きされるかどうかを指定する[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)値です。 既定値は**adResyncAllValues**です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="recordset"></a>レコードセット  
 現在の**レコードセット**内のレコードを基になるデータベースと再同期するには、 **Resync**メソッドを使用します。 これは、静的カーソルまたは順方向専用カーソルを使用していても、基になるデータベースの変更を確認する場合に便利です。  
  
 [[カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md)] プロパティを**adUseClient**に設定した場合、再**同期**は読み取り専用以外の**レコードセット**オブジェクトに対してのみ使用できます。  
  
 [Requery](../../../ado/reference/ado-api/requery-method.md)メソッドとは異なり、 **Resync**メソッドでは、**レコードセット**オブジェクトの基になるコマンドは再実行されません。 基になるデータベースの新しいレコードは表示されません。  
  
 基になるデータとの競合 (たとえば、レコードが別のユーザーによって削除された) によって再同期の試行が失敗した場合、プロバイダーは[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションに警告を返し、実行時エラーが発生します。 [フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**Adfilterconflicts tingrecords**) と[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティを使用して、競合しているレコードを検索します。  
  
 一意の[テーブル](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)と再[同期コマンド](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)の動的プロパティが設定されていて、**レコードセット**が複数のテーブルに対して結合操作を実行した結果である場合、 **resync**メソッドでは、 **unique table**プロパティに指定されているテーブルに対してのみ、 **resync command**プロパティに指定されたコマンドが実行されます。  
  
## <a name="fields"></a>フィールド  
 **同期**メソッドを使用して、**レコード**オブジェクトの**Fields**コレクションの値を基になるデータソースと再同期します。 [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティは、このメソッドの影響を受けません。  
  
 *ResyncValues*が**adResyncAllValues** (既定値) に設定されている場合は、コレクション内の[Field](../../../ado/reference/ado-api/field-object.md)オブジェクトの[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)、 [value](../../../ado/reference/ado-api/value-property-ado.md)、および[originalvalue](../../../ado/reference/ado-api/originalvalue-property-ado.md)プロパティが同期されます。 *ResyncValues*が**adResyncUnderlyingValues**に設定されている場合、 **UnderlyingValue**プロパティのみが同期されます。  
  
 呼び出し時の各**フィールド**オブジェクトの**Status**プロパティの値は、再**同期**の動作にも影響します。 **Adfieldpendingunknown**または**Adfieldpendingunknown**の**Status**値を持つ**Field**オブジェクトの場合、再**同期**は無効です。 **Adfieldpendingchange**または**Adfieldpendingdelete**の**状態**値については、再**同期**によって、データソースにまだ存在するフィールドのデータ値が同期されます。  
  
 **再同期は**、再**同期**が呼び出されたときにエラーが発生しない限り、**フィールド**オブジェクトの**状態**値を変更しません。 たとえば、フィールドが存在しなくなった場合、プロバイダーは、 **adFieldDoesNotExist**などの**フィールド**オブジェクトに対して適切な**状態**値を返します。 返された**状態**値は、 **status**プロパティの値内で論理的に結合できます。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [Resync メソッドの例 (VB)](../../../ado/reference/ado-api/resync-method-example-vb.md)   
 [Resync メソッドの例 (VC + +)](../../../ado/reference/ado-api/resync-method-example-vc.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [UnderlyingValue プロパティ](../../../ado/reference/ado-api/underlyingvalue-property.md)
