---
title: ただしメソッド (ADO) |Microsoft ドキュメント
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
- Recordset15::CancelUpdate
helpviewer_keywords:
- CancelUpdate method [ADO]
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14557cb420d3a878ae6fa6e7cd70cce45fa6bd71
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276321"
---
# <a name="cancelupdate-method-ado"></a>ただしメソッド (ADO)
現在のまたは新しい行に加えられた変更を取り消します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、または[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトを呼び出す前に、[更新](../../../ado/reference/ado-api/update-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>コメント  
  
## <a name="recordset"></a>レコードセット  
 使用して、**ただし**メソッドを現在の行に加えられた変更を取り消すまたは新しく追加した行を破棄します。 呼び出した後は、現在の行、または新しい行への変更を取り消すことはできません、**更新**メソッドを変更することができますをロールバックすると、トランザクションの一部である場合を除き、 [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッド、またはその一部バッチ更新します。 バッチ更新をキャンセルできます、**更新**で、**ただし**または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッドです。  
  
 呼び出すと、新しい行を追加しているかどうか、**ただし**メソッド、現在の行が前に、の現在の行、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)呼び出します。  
  
 編集モードにし、現在のレコードから移動する場合 (たとえばを使用して、[移動](../../../ado/reference/ado-api/move-method-ado.md)、 [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)、または[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッド) を使用することができます**ただし**を保留中の変更を取り消します。 これを行う場合は、更新プログラムは、データ ソースに正常に通知できません必要があります。 たとえば、削除の試みが失敗する参照整合性違反を省略できる、**レコード セット**呼び出しの後に編集モードで[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)です。  
  
## <a name="record"></a>レコード  
 **ただし**メソッドは、保留中の挿入または削除をキャンセル[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト、および保留中の既存のフィールドの更新をキャンセルし、元の値に戻します。 [ステータス](../../../ado/reference/ado-api/status-property-ado-recordset.md)のすべてのフィールドのプロパティ、**フィールド**に設定されているコレクション**adfieldok で**です。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [更新プログラムとただしメソッドの例 (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [更新プログラムとただしメソッドの例 (vc++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew メソッド (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [ただしメソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode プロパティ](../../../ado/reference/ado-api/editmode-property.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)
