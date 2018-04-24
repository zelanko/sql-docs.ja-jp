---
title: ステータスのプロパティの例 (フィールド) (VB) |Microsoft ドキュメント
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
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9c931092b6fea724d3be747cf8c6e69dd8517e6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="status-property-example-field-vb"></a>状態プロパティ (フィールド) (VB) の使用例
次の例を使用して読み取り/書き込みフォルダーからドキュメントを開くと、[インターネット パブリッシング用プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 [ステータス](../../../ado/reference/ado-api/status-property-ado-field.md)のプロパティ、[フィールド](../../../ado/reference/ado-api/field-object.md)のオブジェクト、[レコード](../../../ado/reference/ado-api/record-object-ado.md)は最初に設定されます**adFieldPendingInsert**、し、を更新します。**adfieldok で**です。  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=http://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 次の例は既知の削除**フィールド**から、**レコード**ドキュメントから開きます。 **ステータス**プロパティが最初に設定する**adfieldok で**、し**adFieldPendingUnknown**です。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 次のコードを削除、**フィールド**から、**レコード**読み取り専用のドキュメントを開きます。 **ステータス**に設定されます**adFieldPendingDelete**です。 [更新](../../../ado/reference/ado-api/update-method.md)、削除は失敗して**ステータス**なります**adFieldPendingDelete** plus **adFieldPermissionDenied**です。 [ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)をクリア、保留中**ステータス**設定します。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status プロパティ (ADO Field)](../../../ado/reference/ado-api/status-property-ado-field.md)
