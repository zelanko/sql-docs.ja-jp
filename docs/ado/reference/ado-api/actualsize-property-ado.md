---
title: ActualSize プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8288fa9f39593cb1f5fb91818925d36d731b9f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760687"
---
# <a name="actualsize-property-ado"></a>ActualSize プロパティ (ADO)
フィールドの値の実際の長さをバイト単位で示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **Long 型**の値を返します。  
  
## <a name="remarks"></a>解説  
 **ActualSize**プロパティを使用して、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの値の実際の長さを返します。 すべてのフィールドに対して、 **ActualSize**プロパティは読み取り専用です。 ADO が**フィールド**オブジェクトの値の長さを判断できない場合、 **ActualSize**プロパティは**adunknown**を返します。  
  
 次の例に示すように、 **ActualSize**プロパティと[未定義サイズ](../../../ado/reference/ado-api/definedsize-property.md)プロパティは異なります。 **AdVarChar**の型が宣言され、最大長が50文字の**フィールド**オブジェクトは、定義済みの**size**プロパティ値50を返しますが、返される**ActualSize**プロパティ値は、現在のレコードのフィールドに格納されているデータの長さです。 255**バイトを超える値が**指定された**フィールド**は、可変長列として扱われます。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [ActualSize とのサイズプロパティの例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize とのサイズプロパティの例 (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize プロパティ](../../../ado/reference/ado-api/definedsize-property.md)
