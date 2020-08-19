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
ms.openlocfilehash: 19af2bf0e7058a8f483da25c0db926ebc19807c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441014"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject メソッド (ADO MD)
[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)によって ADO MD スキーマオブジェクト ([ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)、または[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)) を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjType*  
 取得するスキーマオブジェクト (ディメンション、階層、レベル、またはメンバー) の種類を指定する [Schemaobjecttypeenum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) 値。  
  
 *UniqueName*  
 取得するオブジェクトの**UniqueName**プロパティ値を指定する**文字列**。  
  
## <a name="remarks"></a>解説  
 **Getschemaobject** は、 **UniqueName** プロパティで指定されているように、一意の名前を使用してオブジェクトを取得します。 親オブジェクトの名前を把握しておく必要はありません。また、スキーマオブジェクトを取得するために親コレクションを設定する必要もありません。  
  
## <a name="applies-to"></a>適用対象  
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
