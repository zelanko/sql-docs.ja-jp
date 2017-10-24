---
title: "GetSchemaObject メソッド (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f7dca37be4fdebaab7bb16f82086b01a90a3665
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject メソッド (ADO MD)
ADO MD スキーマ オブジェクトを取得します ([ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)、または[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)) によってその[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>構文  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjType*  
 A [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) (ディメンション、階層、レベル、またはメンバー) を取得するスキーマ オブジェクトの種類を指定する値。  
  
 *UniqueName*  
 A**文字列**を指定する、 **UniqueName**取得するオブジェクトのプロパティの値。  
  
## <a name="remarks"></a>解説  
 **GetSchemaObject**で指定したとおり、一意の名前を使用してオブジェクトを取得、 **UniqueName**プロパティです。 親オブジェクトの名前は、既知である必要はありませんし、親のコレクションは、スキーマ オブジェクトを取得する事前設定する必要はありません。  
  
## <a name="applies-to"></a>適用対象  
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)

