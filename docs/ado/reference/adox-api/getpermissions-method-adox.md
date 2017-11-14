---
title: "GetPermissions メソッド (ADOX) |Microsoft ドキュメント"
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
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 542abb8ab3c8fb5857508b4fafb6f50412c825bb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getpermissions-method-adox"></a>GetPermissions メソッド (ADOX)
権限を返します、[グループ](../../../ado/reference/adox-api/group-object-adox.md)または[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクトまたはオブジェクトのコンテナーです。  
  
## <a name="syntax"></a>構文  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**オブジェクトに対するグループまたはユーザーが持っているアクセス許可が含まれるビットマスクを指定する値。 この値は 1 つ以上のすることができます、 [RightsEnum](../../../ado/reference/adox-api/rightsenum.md)定数。  
  
#### <a name="parameters"></a>パラメーター  
 *名前*  
 A**バリアント**アクセス許可を設定する対象のオブジェクトの名前を指定する値。 設定*名前*オブジェクト コンテナーのアクセス許可を取得する場合は null 値にします。  
  
 *ObjectType*  
 A**長い**いずれかの値の[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)アクセス許可を取得する対象のオブジェクトの種類を指定する定数。  
  
 *ObjectTypeId*  
 省略可。 A**バリアント**OLE DB 仕様で定義されていないプロバイダーのオブジェクト型の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**です。 それ以外の場合は使用されません。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[グループ オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[ユーザー オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [GetPermissions と SetPermissions メソッドの例 (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)

