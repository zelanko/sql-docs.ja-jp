---
title: "読み取り、ReadText、書き込み、および WriteText メソッドの例 (VB) |Microsoft ドキュメント"
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
- ReadText method [ADO], Visual Basic example
- Write method [ADO], Visual Basic example
- Read method [ADO], Visual Basic example
- WriteText method [ADO], Visual Basic example
ms.assetid: 699b73f7-04f9-4d46-94b2-6cb12be6de56
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c90b463c42d7f0cc289fdc35620f610a5a2980ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="read-readtext-write-and-writetext-methods-example-vb"></a>読み取り、ReadText、書き込み、および WriteText メソッドの例 (VB)
この例では、両方のテキストにテキスト ボックスの内容を読み取る[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)とバイナリ**ストリーム**です。 その他のプロパティとメソッドが含まれて[位置](../../../ado/reference/ado-api/position-property-ado.md)、[サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)、 [Charset](../../../ado/reference/ado-api/charset-property-ado.md)、および[SetEOS](../../../ado/reference/ado-api/seteos-method.md)です。  
  
```  
'BeginReadVB  
Private Sub cmdRead_Click()  
    On Error GoTo ErrorHandler  
  
    'Declare variables  
    Dim objStream As Stream  
    Dim varA As Variant  
    Dim bytA() As Byte  
    Dim i As Integer  
    Dim strBytes As String  
  
    'Instantiate and Open Stream  
    Set objStream = New Stream  
    objStream.Open  
  
    'Write the text content of a textbox to the stream  
    If Text1.Text = "" Then  
        Err.Raise 1, , "The text field is blank."  
    End If  
    objStream.WriteText Text1.Text  
  
    'Display the text contents and size of the stream  
    objStream.Position = 0  
    Debug.Print "Default text:"  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    'Switch character set and display  
    objStream.Position = 0  
    objStream.Charset = "Windows-1252"  
    Debug.Print "New Charset text:"  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    'Switch to a binary stream and display  
    objStream.Position = 0  
    objStream.Type = adTypeBinary  
    Debug.Print "Binary:"  
    Debug.Print objStream.Read  
    Debug.Print objStream.Size  
  
    'Load an array of bytes with the text box text  
    ReDim bytA(Len(Text1.Text))  
    For i = 1 To Len(Text1.Text)  
        bytA(i - 1) = CByte(Asc(Mid(Text1.Text, i, 1)))  
    Next  
  
    'Write the buffer to the binary stream and display  
    objStream.Position = 0  
    objStream.Write bytA()  
    objStream.SetEOS  
    objStream.Position = 0  
    Debug.Print "Binary after Write:"  
    Debug.Print objStream.Read  
    Debug.Print objStream.Size  
  
    'Switch back to a text stream and display  
    Debug.Print "Translated back:"  
    objStream.Position = 0  
    objStream.Type = adTypeText  
    Debug.Print objStream.ReadText  
    Debug.Print objStream.Size  
  
    ' clean up  
    objStream.Close  
    Set objStream = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not objStream Is Nothing Then  
        If objStream.State = adStateOpen Then objStream.Close  
    End If  
    Set objStream = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndReadVB  
```  
  
## <a name="see-also"></a>参照  
 [Charset プロパティ (ADO)](../../../ado/reference/ado-api/charset-property-ado.md)   
 [位置プロパティ (ADO)](../../../ado/reference/ado-api/position-property-ado.md)   
 [Read メソッド](../../../ado/reference/ado-api/read-method.md)   
 [ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)   
 [SetEOS メソッド](../../../ado/reference/ado-api/seteos-method.md)   
 [Size プロパティ (ADO Stream)](../../../ado/reference/ado-api/size-property-ado-stream.md)   
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Write メソッド](../../../ado/reference/ado-api/write-method.md)   
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)

