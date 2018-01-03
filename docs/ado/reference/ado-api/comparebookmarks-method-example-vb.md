---
title: "CompareBookmarks メソッドの例 (VB) |Microsoft ドキュメント"
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
dev_langs: VB
helpviewer_keywords: CompareBookmarks method [ADO], Visual Basic example
ms.assetid: f156aa48-bfc2-40d1-962b-7b08855776c6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 036399537b1b0d9b5e7eafa429bb4a7775af01f2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="comparebookmarks-method-example-vb"></a>CompareBookmarks メソッドの例 (VB)
この例で、 [CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)メソッドです。 特定のブックマークは特別な何らかの理由でない限りは、ブックマークの相対値は必要ありません。  
  
 ランダムな行を指定する、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)から派生した、***作成者***検索の対象としてテーブル。 各行をターゲットとする相対の位置に表示されます。  
  
```  
'BeginCompareBookmarksVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strSQLAuthors As String  
    Dim strCnxn As String  
  
     ' comparison variables  
    Dim count As Integer  
    Dim target As Variant  
    Dim result As Long  
    Dim strAnswer As String  
    Dim strTitle As String  
    strTitle = "CompareBookmarks Example"  
  
    ' Open a connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
     ' Open recordset as a static cursor type recordset  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT * FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdText  
  
    count = rstAuthors.RecordCount  
    Debug.Print "Rows in the Recordset = "; count  
  
     ' Exit if an empty recordset  
    If count = 0 Then Exit Sub  
  
     ' Get position between 0 and count -1  
    Randomize  
    count = (Int(count * Rnd))  
    Debug.Print "Randomly chosen row position = "; count  
     ' Move row to random position  
    rstAuthors.Move count, adBookmarkFirst  
     ' Remember the mystery row  
    target = rstAuthors.Bookmark  
  
    count = 0  
    rstAuthors.MoveFirst  
         ' Loop through recordset  
    Do Until rstAuthors.EOF  
       result = rstAuthors.CompareBookmarks(rstAuthors.Bookmark, target)  
  
       If result = adCompareNotEqual Then  
          Debug.Print "Row "; count; ": Bookmarks are not equal."  
       ElseIf result = adCompareNotComparable Then  
          Debug.Print "Row "; count; ": Bookmarks are not comparable."  
       Else  
          Select Case result  
             Case adCompareLessThan  
                strAnswer = "less than"  
             Case adCompareEqual  
                strAnswer = "equal to"  
             Case adCompareGreaterThan  
                strAnswer = "greater than"  
             Case Else  
                strAnswer = "in error comparing to"  
          End Select  
            'show the results row-by-row  
          Debug.Print "Row position " & count & " is " & strAnswer & " the target."  
       End If  
  
       count = count + 1  
       rstAuthors.MoveNext  
    Loop  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
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
'EndCompareBookmarksVB  
```  
  
## <a name="see-also"></a>参照  
 [CompareBookmarks メソッド (ADO)](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)   
 [CompareEnum](../../../ado/reference/ado-api/compareenum.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
