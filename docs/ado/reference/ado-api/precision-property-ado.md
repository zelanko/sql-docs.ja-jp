---
title: Precision プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 59bfebe5885d0f18811b6b6c8df0f12634ed316f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703249"
---
# <a name="precision-property-ado"></a>Precision プロパティ (ADO)
内の数値の有効桁数の度を示す、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトまたは数値の[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**バイト**値を表すために使用する最大桁数を示す値。  
  
## <a name="remarks"></a>コメント  
 使用して、**精度**数値の値を表すために使用する最大桁数を決定するプロパティ**パラメーター**または**フィールド**オブジェクト。  
  
 読み取り/書き込みするには、値、**パラメーター**オブジェクト。  
  
 **フィールド**オブジェクト、**精度**は通常読み取り専用です。 ただし、新規の**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクションを[レコード](../../../ado/reference/ado-api/record-object-ado.md)、**精度**は読み取り/書き込みのみ後に、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを**フィールド**が指定されているデータ プロバイダーからその新しいが正常に追加し、**フィールド**を呼び出すことによって[Update](../../../ado/reference/ado-api/update-method.md)のメソッド、**フィールド**コレクション。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>参照  
 [NumericScale および Precision プロパティの例 (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale および Precision プロパティの例 (vc++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale プロパティ (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
