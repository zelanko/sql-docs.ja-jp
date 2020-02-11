---
title: Type プロパティの例 (プロパティ) (VB) |Microsoft Docs
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
- Type property [property] [ADO], Visual Basic example
ms.assetid: 2ee8e4c5-1d66-4a77-8892-6dad7e07e611
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a8def5c7089be85c9b6eb7700a8a5bcdaeebe99e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937857"
---
# <a name="type-property-example-property-vb"></a>Type プロパティの例 (プロパティ) (VB)
この例では、 [Type](../../../ado/reference/ado-api/type-property-ado.md)プロパティを示します。 これは、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)などのコレクションの名前と種類を一覧表示するためのユーティリティのモデルです。  
  
 **プロパティ**コレクションにアクセスするために[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を開く必要はありません。これらは、**レコードセット**オブジェクトがインスタンス化されるときに存在します。 ただし、[[カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md)] プロパティを**adUseClient**に設定すると、**レコードセット**オブジェクトの**properties**コレクションに動的なプロパティがいくつか追加されるため、この例はもう少し興味深いものになります。 具体的には、 [Item](../../../ado/reference/ado-api/item-property-ado.md)プロパティを使用して各[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクトにアクセスします。  
  
```  
'BeginTypePropertyVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' recordset variables  
    Dim rst As ADODB.Recordset  
    Dim prop As ADODB.Property  
     ' property variables  
    Dim ix As Integer  
    Dim strMsg As String  
  
     ' create client-side recordset  
    Set rst = New ADODB.Recordset  
    rst.CursorLocation = adUseClient  
     ' enumerate property types  
    For ix = 0 To rst.Properties.Count - 1  
        Set prop = rst.Properties.Item(ix)  
        Select Case prop.Type  
           Case adBigInt  
              strMsg = "adBigInt"  
           Case adBinary  
              strMsg = "adBinary"  
           Case adBoolean  
              strMsg = "adBoolean"  
           Case adBSTR  
              strMsg = "adBSTR"  
           Case adChapter  
              strMsg = "adChapter"  
           Case adChar  
              strMsg = "adChar"  
           Case adCurrency  
              strMsg = "adCurrency"  
           Case adDate  
              strMsg = "adDate"  
           Case adDBDate  
              strMsg = "adDBDate"  
           Case adDBTime  
              strMsg = "adDBTime"  
           Case adDBTimeStamp  
              strMsg = "adDBTimeStamp"  
           Case adDecimal  
              strMsg = "adDecimal"  
           Case adDouble  
              strMsg = "adDouble"  
           Case adEmpty  
              strMsg = "adEmpty"  
           Case adError  
              strMsg = "adError"  
           Case adFileTime  
              strMsg = "adFileTime"  
           Case adGUID  
              strMsg = "adGUID"  
           Case adIDispatch  
              strMsg = "adIDispatch"  
           Case adInteger  
              strMsg = "adInteger"  
           Case adIUnknown  
              strMsg = "adIUnknown"  
           Case adLongVarBinary  
              strMsg = "adLongVarBinary"  
           Case adLongVarChar  
              strMsg = "adLongVarChar"  
           Case adLongVarWChar  
              strMsg = "adLongVarWChar"  
           Case adNumeric  
              strMsg = "adNumeric"  
           Case adPropVariant  
              strMsg = "adPropVariant"  
           Case adSingle  
              strMsg = "adSingle"  
           Case adSmallInt  
              strMsg = "adSmallInt"  
           Case adTinyInt  
              strMsg = "adTinyInt"  
           Case adUnsignedBigInt  
              strMsg = "adUnsignedBigInt"  
           Case adUnsignedInt  
              strMsg = "adUnsignedInt"  
           Case adUnsignedSmallInt  
              strMsg = "adUnsignedSmallInt"  
           Case adUnsignedTinyInt  
              strMsg = "adUnsignedTinyInt"  
           Case adUserDefined  
              strMsg = "adUserDefined"  
           Case adVarBinary  
              strMsg = "adVarBinary"  
           Case adVarChar  
              strMsg = "adVarChar"  
           Case adVariant  
              strMsg = "adVariant"  
           Case adVarNumeric  
              strMsg = "adVarNumeric"  
           Case adVarWChar  
              strMsg = "adVarWChar"  
           Case adWChar  
              strMsg = "adWChar"  
           Case Else  
              strMsg = "*UNKNOWN*"  
        End Select  
            'show results  
        Debug.Print "Property " & ix & ": " & prop.Name & _  
                    ", Type = " & strMsg  
    Next ix  
  
    ' clean up  
    Set rst = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    Set rst = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndTypePropertyVB  
```  
  
## <a name="see-also"></a>参照  
 [Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)   
 [Type プロパティ (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
