---
description: Groups および Users Append、ChangePassword メソッドの例 (VB)
title: Groups および Users Append、ChangePassword メソッドの例 (VB) |Microsoft Docs
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
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: rothja
ms.author: jroth
ms.openlocfilehash: 7aa335dc2aabdf05ab34a0245bb0aafc14b17cf1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439984"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Groups および Users Append、ChangePassword メソッドの例 (VB)
この例では、[グループ](../../../ado/reference/adox-api/groups-collection-adox.md)の[append](../../../ado/reference/adox-api/append-method-adox-groups.md)メソッドと、システムに新しい[グループ](../../../ado/reference/adox-api/group-object-adox.md)と新しい[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)を追加することによる[ユーザー](../../../ado/reference/adox-api/users-collection-adox.md)の[追加](../../../ado/reference/adox-api/append-method-adox-users.md)方法を示します。 新しい**グループ**は、新しい**ユーザー**の**Groups**コレクションに追加されます。 その結果、新しい **ユーザー** が **グループ**に追加されます。 また、 [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) メソッドを使用して **ユーザー** パスワードを指定します。  
  
> [!NOTE]
>  Windows 認証をサポートするデータソースプロバイダーに接続する場合は、接続文字列にユーザー ID とパスワードの情報ではなく、 **Trusted_Connection = yes** または **INTEGRATED Security = SSPI** を指定する必要があります。  
  
```  
' BeginGroupVB  
Sub Main()  
    On Error GoTo GroupXError  
  
    Dim cat As ADOX.Catalog  
    Dim usrNew As ADOX.User  
    Dim usrLoop As ADOX.User  
    Dim grpLoop As ADOX.Group  
  
    Set cat = New ADOX.Catalog  
  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';" & _  
        "jet oledb:system database=" & _  
        "'system.mdw'"  
  
    With cat  
        'Create and append new group with a string.  
        .Groups.Append "Accounting"  
  
        ' Create and append new user with an object.  
        Set usrNew = New ADOX.User  
        usrNew.Name = "Pat Smith"  
        usrNew.ChangePassword "", "Password1"  
        .Users.Append usrNew  
  
        ' Make the user Pat Smith a member of the  
        ' Accounting group by creating and adding the  
        ' appropriate Group object to the user's Groups  
        ' collection. The same is accomplished if a User  
        ' object representing Pat Smith is created and  
        ' appended to the Accounting group Users collection  
        usrNew.Groups.Append "Accounting"  
  
        ' Enumerate all User objects in the  
        ' catalog's Users collection.  
        For Each usrLoop In .Users  
            Debug.Print "  " & usrLoop.Name  
            Debug.Print "    Belongs to these groups:"  
            ' Enumerate all Group objects in each User  
            ' object's Groups collection.  
            If usrLoop.Groups.Count <> 0 Then  
                For Each grpLoop In usrLoop.Groups  
                    Debug.Print "    " & grpLoop.Name  
                Next grpLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next usrLoop  
  
        ' Enumerate all Group objects in the default  
        ' workspace's Groups collection.  
        For Each grpLoop In .Groups  
            Debug.Print "  " & grpLoop.Name  
            Debug.Print "    Has as its members:"  
            ' Enumerate all User objects in each Group  
            ' object's Users collection.  
            If grpLoop.Users.Count <> 0 Then  
                For Each usrLoop In grpLoop.Users  
                    Debug.Print "    " & usrLoop.Name  
                Next usrLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next grpLoop  
  
        ' Delete new User and Group objects because this  
        ' is only a demonstration.  
        ' These two line are commented out because the sub "OwnersX" uses  
        ' the group "Accounting".  
'        .Users.Delete "Pat Smith"  
'        .Groups.Delete "Accounting"  
  
    End With  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set usrNew = Nothing  
    Exit Sub  
  
GroupXError:  
  
    Set cat = Nothing  
    Set usrNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndGroupVB  
```  
  
## <a name="see-also"></a>参照  
 [Append メソッド (ADOX Groups)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append メソッド (ADOX Users)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [ChangePassword メソッド (ADOX)](../../../ado/reference/adox-api/changepassword-method-adox.md)   
 [Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)   
 [Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)   
 [Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
