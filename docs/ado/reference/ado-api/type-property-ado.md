---
title: Type プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ee1058299becb4a7a4234debc097516cb02dd41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937864"
---
# <a name="type-property-ado"></a>Type プロパティ (ADO)
[パラメーター](../../../ado/reference/ado-api/parameter-object.md)、[フィールド](../../../ado/reference/ado-api/field-object.md)、または[プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクトの操作の種類またはデータ型を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)値を設定または返します。  
  
## <a name="remarks"></a>解説  
 **Parameter**オブジェクトの場合、 **Type**プロパティは読み取り/書き込み可能です。 [レコード](../../../ado/reference/ado-api/record-object-ado.md)の[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに追加された新しい**フィールド**オブジェクトの場合は、**フィールド**の [[値](../../../ado/reference/ado-api/value-property-ado.md)] プロパティが指定され、データプロバイダーが**フィールド**コレクションの[Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出して新しい**フィールド**を正常に追加した後にのみ、「読み取り/書き込み専用」と**入力**します。  
  
 他のすべてのオブジェクトについては、 **Type**プロパティは読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [Type プロパティの例 (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Type プロパティの例 (プロパティ) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType プロパティ (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type プロパティ (ADO Stream)](../../../ado/reference/ado-api/type-property-ado-stream.md)
