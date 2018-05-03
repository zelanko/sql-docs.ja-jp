---
title: SetPermissions メソッド (ADOX) |Microsoft ドキュメント
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
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 302f35fff7f01fefd1ff56d60b19e4b0aff5ded8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
 A**長い**いずれかの値の[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)アクセス許可を取得する対象のオブジェクトの種類を指定する定数。  
  
 *操作*  
 A**長い**いずれかの値の[ActionEnum](../../../ado/reference/adox-api/actionenum.md)アクセス許可を設定するときに実行するアクションの種類を指定する定数。  
  
 *権限*  
 A**長い**ビットマスクを指定できる値の 1 つ以上の[RightsEnum](../../../ado/reference/adox-api/rightsenum.md)を設定する権限を示す定数です。  
  
 *継承します。*  
 省略可。 A**長い**いずれかの値の[InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md)オブジェクトがこれらのアクセス許可を継承する方法を指定する定数。 既定値は**adInheritNone**です。  
  
 *ObjectTypeId*  
 省略可。 A**バリアント**OLE DB 仕様で定義されていないプロバイダーのオブジェクト型の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**です。 それ以外の場合は使用されません。  
  
## <a name="remarks"></a>解説  
 プロバイダーがグループまたはユーザーのアクセス許可の設定をサポートしていない場合は、エラーが発生します。  
  
> [!NOTE]
>  呼び出すときに**SetPermissions**、アクションに設定**adAccessRevoke**の設定で上書き、 *Rights*パラメーター。 設定しないでください*アクション*に**adAccessRevoke**で指定された権限の場合、 *Rights*を有効にするパラメーターです。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [GetPermissions と SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
