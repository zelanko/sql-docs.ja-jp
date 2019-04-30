---
title: エラー オブジェクトのプロパティの例 (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Number property [ADO], Visual Basic example
- Source property [ADO], Visual Basic example
- NativeError property [ADO], Visual Basic example
- Description property [ADO], Visual Basic example
- HelpFile property [ADO], Visual Basic example
- SQLState property [ADO], Visual Basic example
- HelpContext property [ADO], Visual Basic example
ms.assetid: 5c728458-d85c-497c-afcf-2cfa36c3342a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 139ffaee3210709dd82f328eca88bb3ae2973bbe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140411"
---
# <a name="description-helpcontext-helpfile-nativeerror-number-source-and-sqlstate-properties-example-vb"></a>Description、HelpContext、HelpFile、NativeError、数、ソース、および SQLState プロパティの例 (VB)
この例は、エラーをトリガーし、こと、トラップが表示されます、[説明](../../../ado/reference/ado-api/description-property.md)、 [HelpContext](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)、 [HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)、 [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)、 [数](../../../ado/reference/ado-api/number-property-ado.md)、[ソース](../../../ado/reference/ado-api/source-property-ado-error.md)、および[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)結果のプロパティ[エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。  
  
```  
'BeginDescriptionVB  
Public Sub Main()  
  
    Dim Cnxn As ADODB.Connection  
    Dim Err As ADODB.Error  
    Dim strError As String  
  
    On Error GoTo ErrorHandler  
  
    ' Intentionally trigger an error  
    Set Cnxn = New ADODB.Connection  
    Cnxn.Open "nothing"  
  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
  
    ' Enumerate Errors collection and display  
    ' properties of each Error object  
    For Each Err In Cnxn.Errors  
        strError = "Error #" & Err.Number & vbCr & _  
            "   " & Err.Description & vbCr & _  
            "   (Source: " & Err.Source & ")" & vbCr & _  
            "   (SQL State: " & Err.SQLState & ")" & vbCr & _  
            "   (NativeError: " & Err.NativeError & ")" & vbCr  
        If Err.HelpFile = "" Then  
            strError = strError & "   No Help file available"  
        Else  
            strError = strError & _  
               "   (HelpFile: " & Err.HelpFile & ")" & vbCr & _  
               "   (HelpContext: " & Err.HelpContext & ")" & _  
               vbCr & vbCr  
        End If  
  
        Debug.Print strError  
    Next  
  
    Resume Next  
End Sub  
'EndDescriptionVB  
```  
  
## <a name="see-also"></a>参照  
 [Description プロパティ](../../../ado/reference/ado-api/description-property.md)   
 [Error オブジェクト](../../../ado/reference/ado-api/error-object.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [HelpContext、HelpFile プロパティ](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [NativeError プロパティ (ADO)](../../../ado/reference/ado-api/nativeerror-property-ado.md)   
 [Number プロパティ (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [ソースのプロパティ (ADO Error)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [SQLState プロパティ](../../../ado/reference/ado-api/sqlstate-property.md)
