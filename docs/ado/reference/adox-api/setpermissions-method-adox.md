---
title: SetPermissions メソッド (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
author: rothja
ms.author: jroth
ms.openlocfilehash: 4287e836dd46c579ee81a4baf0e175e8b49acf67
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942640"
---
# <a name="setpermissions-method-adox"></a>SetPermissions メソッド (ADOX)
オブジェクトの[グループ](../../../ado/reference/adox-api/group-object-adox.md)または[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)に対する権限を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 権限を設定するオブジェクトの名前を示す**文字列**値です。  
  
 *ObjectType*  
 [Objecttypeenum](../../../ado/reference/adox-api/objecttypeenum.md)定数の1つであり、アクセス許可を取得するオブジェクトの型を指定する**Long 型**の値です。  
  
 *操作*  
 **Long**値。権限を設定するときに実行するアクションの種類を指定する[actionenum](../../../ado/reference/adox-api/actionenum.md)定数の1つです。  
  
 *権限*  
 設定する権限を示す1つ以上の[右 Senum](../../../ado/reference/adox-api/rightsenum.md)定数のビットマスクとして使用できる**Long 型**の値。  
  
 *識別子*  
 任意。 オブジェクトがこれらのアクセス許可を継承する方法を指定する、 [Inherittypeenum](../../../ado/reference/adox-api/inherittypeenum.md)定数の1つである**Long**値。 既定値は**Adinheritnone**です。  
  
 *ObjectTypeId*  
 任意。 OLE DB 仕様で定義されていないプロバイダーオブジェクト型の GUID を示す**バリアント**値です。 *ObjectType*が**Adpermobjproviderspecific**に設定されている場合、このパラメーターは必須です。それ以外の場合は使用されません。  
  
## <a name="remarks"></a>注釈  
 プロバイダーがグループまたはユーザーのアクセス権の設定をサポートしていない場合、エラーが発生します。  
  
> [!NOTE]
>  **SetPermissions**を呼び出す場合、 **adaccessrevoke**にアクションを設定すると、 *Rights*パラメーターの設定が上書きされます。 *Rights*パラメーターに指定された権限を有効にする場合は、*アクション*を**adaccessrevoke**に設定しないでください。  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)  
    :::column-end:::
    :::column:::
        [User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>参照  
 [GetPermissions および SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
