---
title: "GetObjectOwner メソッド (ADOX) |Microsoft ドキュメント"
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
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 51092c3cf38f9b8ae9d5d81bbbea0177df097f1d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner メソッド (ADOX)
内のオブジェクトの所有者を返します、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**文字列**を指定する値、[名前](../../../ado/reference/adox-api/name-property-adox.md)の[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)オブジェクトを所有しています。  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectName*  
 A**文字列**所有者を返す対象となるオブジェクトの名前を指定する値。  
  
 *ObjectType*  
 A**長い**いずれかの値の[ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md)所有者を取得する対象のオブジェクトの種類を指定する定数。  
  
 *ObjectTypeId*  
 省略可。 A**バリアント**OLE DB 仕様で定義されていないプロバイダーのオブジェクト型の GUID を指定する値。 このパラメーターは必要な場合*ObjectType*に設定されている**adPermObjProviderSpecific**です。 それ以外の場合は使用されません。  
  
## <a name="remarks"></a>解説  
 プロバイダーが返すオブジェクトの所有者をサポートしていない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [GetObjectOwner と SetObjectOwner メソッドの例 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner メソッド](../../../ado/reference/adox-api/setobjectowner-method.md)
