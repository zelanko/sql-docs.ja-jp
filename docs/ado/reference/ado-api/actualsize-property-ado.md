---
title: "ActualSize プロパティ (ADO) |Microsoft ドキュメント"
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
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d66019d7a71dd480f1a88a28fe94d72a176497c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="actualsize-property-ado"></a>ActualSize プロパティ (ADO)
フィールドの実際の長さを示します。s 値 (バイト単位)。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 返します、**長い**値。  
  
## <a name="remarks"></a>解説  
 使用して、 **ActualSize**の実際の長さを取得するプロパティ、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの値。 すべてのフィールドについて、 **ActualSize**プロパティは読み取り専用です。 ADO の長さを判断できない場合、**フィールド**オブジェクトの値、 **ActualSize**プロパティから返される**adUnknown**です。  
  
 **ActualSize**と[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)プロパティは、次の例で示すように異なります、します。 A**フィールド**の宣言された型とオブジェクト**それぞれ**し、50 文字の最大長を返します、 **DefinedSize** 50 でのプロパティの値が、 **ActualSize**プロパティの値が返されますが、現在のレコードのフィールドに格納されているデータの長さ。 **フィールド**で、 **DefinedSize** 255 バイトは、可変長の列として扱われます。 より大きい。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [ActualSize と DefinedSize プロパティの例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize と DefinedSize プロパティの例 (vc++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize プロパティ](../../../ado/reference/ado-api/definedsize-property.md)

