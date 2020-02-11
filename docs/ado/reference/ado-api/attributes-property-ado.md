---
title: Attributes プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b40b71dee32608756721d84a2e13f5f54f7bcbfa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920541"
---
# <a name="attributes-property-ado"></a>Attributes プロパティ (ADO)
オブジェクトの1つまたは複数の特性を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **Long 型**の値を設定または返します。  
  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの場合、 **Attributes**プロパティは読み取り/書き込み可能であり、その値は1つ以上の[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)値の合計になります。 既定値は 0 です。  
  
 [Parameter](../../../ado/reference/ado-api/parameter-object.md)オブジェクトの場合、 **Attributes**プロパティは読み取り/書き込み可能であり、その値は1つ以上の[parameterattributes 列挙](../../../ado/reference/ado-api/parameterattributesenum.md)値の合計になります。 既定値は**Adparamsigned**です。  
  
 [Field](../../../ado/reference/ado-api/field-object.md)オブジェクトの場合、 **Attributes**プロパティには1つ以上の[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)値の合計を指定できます。 通常は読み取り専用です。 ただし、[レコード](../../../ado/reference/ado-api/record-object-ado.md)の[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに追加された新しい**フィールド**オブジェクトの場合、**属性**は、**フィールド**の[Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティが指定されていて、**フィールドコレクションの** [Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出すことによって新しい**フィールド**が正常にデータプロバイダーによって追加された後にのみ、読み取り/書き込みになります。  
  
 [プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクトの場合、 **Attributes**プロパティは読み取り専用であり、その値は1つ以上の[propertyattributes 列挙](../../../ado/reference/ado-api/propertyattributesenum.md)値の合計になります。  
  
## <a name="remarks"></a>解説  
 **接続**オブジェクト、**パラメーター**オブジェクト、**フィールド**オブジェクト、または**プロパティ**オブジェクトの特性を設定または取得するには、 **Attributes**プロパティを使用します。  
  
 複数の属性を設定すると、適切な定数を合計することができます。 互換性のない定数を含む合計にプロパティ値を設定すると、エラーが発生します。  
  
> [!NOTE]
>  **リモートデータサービスの使用状況**このプロパティは、クライアント側の**接続**オブジェクトでは使用できません。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [Attributes と Name プロパティの例 (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributes と Name プロパティの例 (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [AppendChunk メソッド (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk メソッド (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
