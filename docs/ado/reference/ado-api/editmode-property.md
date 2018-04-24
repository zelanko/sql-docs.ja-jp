---
title: EditMode プロパティ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d64f1ea25b8febe0ca9c474f76642cf1f74a9302
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="editmode-property"></a>EditMode プロパティ
現在のレコードの編集状態を示します。  
  
## <a name="return-value"></a>戻り値  
 返します、 [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)値。  
  
## <a name="remarks"></a>解説  
 ADO では、現在のレコードに関連付けられている編集バッファーを保持します。 このプロパティは、このバッファーに変更が加えされているかどうか、または新しいレコードが作成されるかどうかを示します。 使用して、 **EditMode**プロパティ、現在のレコードの編集状態を確認します。 編集のプロセスが中断された場合は、保留中の変更をテストして使用する必要があるかどうかを判断、[更新](../../../ado/reference/ado-api/update-method.md)または[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッドです。  
  
 *即時更新モード*、 **EditMode**にプロパティをリセット**adEditNone**呼び出しに成功した後、**更新**メソッドが呼び出されます. 呼び出し時に[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)は正常に削除されませんまたはデータ ソース内の複数のレコード (たとえば、参照整合性違反の場合) が原因、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)に残る編集モード (**EditMode** = **adEditInProgress**)。 したがって、**ただし**現在のレコードから移動する前に呼び出す必要があります (たとえば[移動](../../../ado/reference/ado-api/move-method-ado.md)、 [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)、または[を閉じる](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 *バッチ更新モード*(をプロバイダーが複数の変更をキャッシュし、呼び出した場合にのみ、基になるデータ ソースに書き込みます、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッド) の値、 **EditMode**プロパティが変更されたは、最初の操作を実行しへの呼び出しではリセットされません、**更新**メソッドです。 後続の操作は、の値を変更しない、 **EditMode**プロパティ、別の操作が実行される場合でもです。 たとえば、最初の操作は、新しいレコードを追加して、2 つ目は、既存の変更を加えます録画のプロパティは、 **EditMode**は引き続き**adEditAdd**です。 **EditMode**するプロパティはリセットされません**adEditNone**呼び出しの後まで**UpdateBatch**です。 調べるにはどのような操作が実行された、設定、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを[adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md)保留中の変更のレコードがだけが参照可能であり、確認できるように、 [の状態](../../../ado/reference/ado-api/status-property-ado-recordset.md)データにどのような変更が加えられたを決定するには、各レコードのプロパティです。  
  
> [!NOTE]
>  **EditMode**現在のレコードがある場合にのみ、有効な値を返すことができます。 **EditMode**場合に、エラーが返されます[BOF または EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)が true の場合、または現在のレコードが削除された場合。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [カーソル。、LockType、および EditMode のプロパティの例 (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [カーソル。、LockType、および EditMode のプロパティの例 (vc++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [AddNew メソッド (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Delete メソッド (ADO レコード セット)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [ただしメソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Update メソッド](../../../ado/reference/ado-api/update-method.md)
