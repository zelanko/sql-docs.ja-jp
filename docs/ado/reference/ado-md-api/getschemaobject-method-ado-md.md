---
description: GetSchemaObject メソッド (ADO MD)
title: GetSchemaObject メソッド (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
author: rothja
ms.author: jroth
ms.openlocfilehash: b0a54b02cf748d8ff1144e50e3531295dbfe8c55
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778121"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject メソッド (ADO MD)
[UniqueName](./uniquename-property-ado-md.md)によって ADO MD スキーマオブジェクト ([ディメンション](./dimension-object-ado-md.md)、[階層](./hierarchy-object-ado-md.md)、[レベル](./level-object-ado-md.md)、または[メンバー](./member-object-ado-md.md)) を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjType*  
 取得するスキーマオブジェクト (ディメンション、階層、レベル、またはメンバー) の種類を指定する [Schemaobjecttypeenum](./schemaobjecttypeenum.md) 値。  
  
 *UniqueName*  
 取得するオブジェクトの**UniqueName**プロパティ値を指定する**文字列**。  
  
## <a name="remarks"></a>解説  
 **Getschemaobject** は、 **UniqueName** プロパティで指定されているように、一意の名前を使用してオブジェクトを取得します。 親オブジェクトの名前を把握しておく必要はありません。また、スキーマオブジェクトを取得するために親コレクションを設定する必要もありません。  
  
## <a name="applies-to"></a>適用対象  
 [CubeDef オブジェクト (ADO MD)](./cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef オブジェクト (ADO MD)](./cubedef-object-ado-md.md)