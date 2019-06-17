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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fcc44037ac746621c044bca755fd9b957356dc38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705793"
---
# <a name="setpermissions-method-adox"></a>SetPermissions メソッド (ADOX)
アクセス許可を指定します、[グループ](../../../ado/reference/adox-api/group-object-adox.md)または[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 A**文字列**アクセス許可を設定する対象のオブジェクトの名前を指定する値。  
  
 *ObjectType*  
 A**長い**いずれかの値の[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)定数は、アクセス許可を取得する対象のオブジェクトの型を指定します。  
  
 *操作*  
 A**長い**いずれかの値の[ActionEnum](../../../ado/reference/adox-api/actionenum.md)アクセス許可を設定するときに実行するアクションの種類を指定する定数。  
  
 *権限*  
 A**長い**ビットマスクを指定できる値の 1 つ以上の[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)を設定する権限を示す定数。  
  
 *継承*  
 任意。 A**長い**いずれかの値の[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)定数は、オブジェクトがこれらのアクセス許可を継承する方法を指定します。 既定値は**adInheritNone**します。  
  
 *ObjectTypeId*  
 任意。 A**バリアント**OLE DB 仕様で定義されていないプロバイダー オブジェクトの種類の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**。 それ以外は使用されません。  
  
## <a name="remarks"></a>コメント  
 プロバイダーがグループまたはユーザーのアクセス許可の設定をサポートしていない場合、エラーが発生します。  
  
> [!NOTE]
>  呼び出すときに**SetPermissions**、アクションを設定**adAccessRevoke**の設定をオーバーライド、 *Rights*パラメーター。 設定しないでください*アクション*に**adAccessRevoke**で指定した権限の場合、 *Rights*パラメーターが有効にします。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [GetPermissions および SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
