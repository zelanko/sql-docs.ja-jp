---
title: Status プロパティ (ADO フィールド) |Microsoft ドキュメント
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
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70baf781839fe9a606f1aed2c26676dffe102d69
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282011"
---
# <a name="status-property-ado-field"></a>Status プロパティ (ADO フィールド)
状態を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、 [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)値。 既定値は**adfieldok で**です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="record-field-status"></a>レコード フィールドの状態  
 値に変更、**フィールド**のフィールド コレクション内のオブジェクト、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトは、オブジェクトのまでキャッシュ[更新](../../../ado/reference/ado-api/update-method.md)メソッドが呼び出されます。 その時点では、フィールドの値への変更には、エラーが発生しました、OLE DB エラーが発生、 **DB_E_ERRORSOCCURRED** (2147749409)。 いずれかの Status プロパティ、**フィールド**内のオブジェクト、**フィールド**から値をエラーの原因となったコレクションが格納されます、 [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)の原因を説明します。問題を。  
  
 パフォーマンス、追加および削除を強化するために、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、**レコード**までオブジェクトはキャッシュ、**更新**メソッドを呼び出すとを変更し、オプティミスティック更新プログラムのバッチで行われます。 場合、**更新**メソッドは呼び出されません、サーバーは更新されません。 OLE DB プロバイダー エラー (DB_E_ERRORSOCCURRED) が返されます、すべての更新が失敗した場合、**ステータス**プロパティは、操作コードとエラー状態コードの値の組み合わせを示します。 たとえば、 **adFieldPendingInsert OR adFieldPermissionDenied**です。 **ステータス**それぞれのプロパティ**フィールド**原因を特定するために使用する、**フィールド**がない追加、変更、または削除します。  
  
 さまざまな種類の変更、または削除を追加する場合に発生する問題、**フィールド**から報告された、**ステータス**プロパティです。 たとえば、ユーザーを削除した場合、**フィールド**からの削除のマークされている、**フィールド**コレクション。 場合、後続**更新**ため、ユーザーを削除しようとしましたエラーが返されます、**フィールド**、アクセス許可のいない、**フィールド**が、  **。ステータス**の**adFieldPermissionDenied OR adFieldPendingDelete**です。 呼び出す、[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッドの復元元の値と設定、**ステータス**に**adfieldok で**です。  
  
 同様に、**更新**ために、メソッドはエラーを返すことがあります、新しい**フィールド**追加され、不適切な値を指定します。 新しい**フィールド**になります、**フィールド**コレクションし、状態の**adFieldPendingInsert**とおそらく**adFieldCantCreate**(プロバイダーによっては)。 適切な値を指定するには、新しい**フィールド**を呼び出すと**更新**もう一度です。  
  
## <a name="recordset-field-status"></a>レコード セットのフィールドの状態  
 値に変更、**フィールド**いずれかのフィールド コレクション内のオブジェクト、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)までオブジェクトのキャッシュは[更新](../../../ado/reference/ado-api/update-method.md)メソッドが呼び出されます。 その時点では、フィールドの値への変更には、エラーが発生しました、OLE DB エラーが発生、 **DB_E_ERRORSOCCURRED** (2147749409)。 いずれかの Status プロパティ、**フィールド**内のオブジェクト、**フィールド**から値をエラーの原因となったコレクションが格納されます、 [FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)の原因を説明します。問題を。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [状態プロパティ (フィールド) (VB) の使用例](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Status プロパティの例 (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
