---
title: NumericScale プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 575618ad1760cdca6c32e1b8e2797070583506de
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="numericscale-property-ado"></a>NumericScale プロパティ (ADO)
内の数値の小数点以下桁数を示す、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)または[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バイト**する数値の小数点以下桁数を示す値が解決されます。  
  
## <a name="remarks"></a>解説  
 使用して、 **NumericScale**型の数値の値を表すに使用される、小数点の右側に数字の数を決定するプロパティ**パラメーター**または**フィールド**オブジェクト。  
  
 **パラメーター** 、オブジェクト、 **NumericScale**読み取り/書き込みプロパティです。  
  
 **フィールド**オブジェクト、 **NumericScale**は通常読み取り専用です。 ただし、新規の**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、 **NumericScale**読み取り/書き込みした場合のみ、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを**フィールド**が指定されているデータ プロバイダーが追加、新しいおよび**フィールド**を呼び出すことによって[更新](../../../ado/reference/ado-api/update-method.md)のメソッド、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクション。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>参照  
 [NumericScale と (VB) の有効桁数のプロパティの例](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale と (vc++) の有効桁数のプロパティの例](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision プロパティ (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
