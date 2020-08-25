---
description: SetObjectOwner メソッド
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
author: rothja
ms.author: jroth
ms.openlocfilehash: acefd94f29b030a6bee724686e11023a354d8921
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769411"
---
# <a name="setobjectowner-method"></a>SetObjectOwner メソッド
[カタログ](./catalog-object-adox.md)内のオブジェクトの所有者を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectName*  
 所有者を指定するオブジェクトの名前を示す **文字列** 値です。  
  
 *ObjectType*  
 Owner 型を指定する[Objecttypeenum](./objecttypeenum.md)定数の1つである**Long**値。  
  
 *OwnerName*  
 オブジェクトを所有する[ユーザー](./user-object-adox.md)または[グループ](./group-object-adox.md)の[名前](./name-property-adox.md)を指定する**文字列**値。  
  
 *ObjectTypeId*  
 任意。 OLE DB 仕様で定義されていないプロバイダーオブジェクト型の GUID を示す **バリアント** 値です。 *ObjectType*が**Adpermobjproviderspecific**に設定されている場合、このパラメーターは必須です。それ以外の場合は使用されません。  
  
## <a name="remarks"></a>解説  
 プロバイダーがオブジェクトの所有者の指定をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [GetObjectOwner メソッドと SetObjectOwner メソッドの例 (VB)](./getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner メソッド (ADOX)](./getobjectowner-method-adox.md)