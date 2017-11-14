---
title: "保存して開く方法の例 (VB) |Microsoft ドキュメント"
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
dev_langs:
- VB
helpviewer_keywords:
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad4d79342ae4903e3469f3685210e882d64d318f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="save-and-open-methods-example-vb"></a>保存して開く方法の例 (VB)
これら 3 つの例を示す方法、[保存](../../../ado/reference/ado-api/save-method.md)と[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドを併用することができます。  
  
 出張が起こってと、データベースからテーブルを実行することを想定しています。 としてデータにアクセスするにする前に、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)移動可能な形式で保存します。 アクセスする、転送先に到着したときに、**レコード セット**ローカル、切断されている**レコード セット**です。 変更を行い、 **Recordset**、し、もう一度保存します。 最後に、ホームを取得する場合は、データベースにもう一度接続し、外出先での変更で更新します。  
  
 最初に、アクセスし、保存、***作成者***テーブル。  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 この時点で、転送先に到着しました。 場合は、アクセス、***作成者***として、ローカル テーブル切断**Recordset**です。 必要があります、 **MSPersist**保存したファイルへのアクセスを使用しているコンピューター上のプロバイダー a:\Pubs.xml です。  
  
```  
Attribute VB_Name = "Save"  
```  
  
 最後に、戻ってます。 今すぐ変更内容をデータベースを更新します。  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [レコード セットの保存に関する詳細情報](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)

