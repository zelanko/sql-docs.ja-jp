---
title: NumericScale プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: rothja
ms.author: jroth
ms.openlocfilehash: 3970ab8d8f446c4269e4b79c306d2dd9d2cf0426
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762331"
---
# <a name="numericscale-property-ado"></a>NumericScale プロパティ (ADO)
[パラメーター](../../../ado/reference/ado-api/parameter-object.md)または[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの数値の小数点以下桁数を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 数値が解決される小数点以下の桁数を示す**バイト**値を設定または返します。  
  
## <a name="remarks"></a>解説  
 数値**パラメーター**または**フィールド**オブジェクトの値を表すために使用される、小数点の右側の桁数を決定するには、 **numericscale**プロパティを使用します。  
  
 **パラメーター**オブジェクトの場合、 **numericscale**プロパティは読み取り/書き込み可能です。  
  
 **フィールド**オブジェクトの場合、 **numericscale**は通常読み取り専用です。 ただし、[レコード](../../../ado/reference/ado-api/record-object-ado.md)の[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに追加された新しい**フィールド**オブジェクトの場合は、**フィールド**の[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティが指定され、データプロバイダーが[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションの[Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出して新しい**フィールド**を正常に追加した後にのみ、 **numericscale**が読み取り/書き込みになります。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>参照  
 [NumericScale および Precision プロパティの例 (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale および Precision プロパティの例 (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision プロパティ (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
