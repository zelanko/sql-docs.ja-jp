---
title: "SetObjectOwner メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 35b592bf1503c457532d8988f0fd6e09f06115dd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="setobjectowner-method"></a>SetObjectOwner メソッド
内のオブジェクトの所有者を指定します、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)です。  
  
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
 A**文字列**を指定する値、[名前](../../../ado/reference/adox-api/name-property-adox.md)の[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)オブジェクトを所有します。  
  
 *ObjectTypeId*  
 省略可。 A**バリアント**OLE DB 仕様で定義されていないプロバイダーのオブジェクト型の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**です。 それ以外の場合は使用されません。  
  
## <a name="remarks"></a>解説  
 プロバイダーが指定するオブジェクトの所有者をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [GetObjectOwner と SetObjectOwner メソッドの例 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
