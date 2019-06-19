---
title: SetObjectOwner メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: befb99993db3369995934be4f8d5874d4753d288
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718819"
---
# <a name="setobjectowner-method"></a>SetObjectOwner メソッド
内のオブジェクトの所有者を指定します、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectName*  
 A**文字列**所有者を指定する対象のオブジェクトの名前を指定する値。  
  
 *ObjectType*  
 A**長い**いずれかの値の[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)所有者の種類を指定する定数。  
  
 *OwnerName*  
 A**文字列**を指定する値、[名前](../../../ado/reference/adox-api/name-property-adox.md)の[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)オブジェクトの所有者にします。  
  
 *ObjectTypeId*  
 任意。 A**バリアント**OLE DB 仕様で定義されていないプロバイダー オブジェクトの種類の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**。 それ以外は使用されません。  
  
## <a name="remarks"></a>コメント  
 プロバイダーが指定するオブジェクトの所有者をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [GetObjectOwner および SetObjectOwner メソッドの例 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
