---
title: 属性のプロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae152e6c324f244919da9e100211cadf0c1ac12a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="attributes-property-ado"></a>属性プロパティ (ADO)
オブジェクトの 1 つまたは複数の特性を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**値。  
  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、**属性**プロパティが読み取り/書き込み、およびその値が 1 つまたは複数の合計を指定できます[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)値。 既定ではゼロ (0) です。  
  
 [パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクト、**属性**プロパティが読み取り/書き込み、でき、その値が 1 つ以上の合計[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)値。 既定値は**adParamSigned**です。  
  
 [フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト、**属性**プロパティは、1 つまたは複数の合計を指定できます[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)値。 これは通常読み取り専用です。 ただし、新規の**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、**属性**読み取り/書き込みのみ後に、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを**フィールド**が指定されていると、新しい**フィールド**データ プロバイダーによって、を呼び出すことによってを正常に追加されました。[更新](../../../ado/reference/ado-api/update-method.md)のメソッド、**フィールド**コレクション。  
  
 [プロパティ](../../../ado/reference/ado-api/property-object-ado.md)オブジェクト、**属性**プロパティは読み取り専用でき、その値が 1 つ以上の合計[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)値。  
  
## <a name="remarks"></a>解説  
 使用して、**属性**プロパティを設定または取得の特性を**接続**オブジェクト、**パラメーター**オブジェクト、**フィールド**オブジェクト、または**プロパティ**オブジェクト。  
  
 複数の属性を設定すると、適切な定数を合計することができます。 互換性のない定数を含む合計にプロパティの値を設定した場合、エラーが発生します。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**このプロパティはクライアント側で使用できません**接続**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [属性と名前のプロパティの例 (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [属性と名前のプロパティの例 (vc++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [AppendChunk メソッド (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans、CommitTrans、および RollbackTrans メソッド (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk メソッド (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
