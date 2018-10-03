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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4676f1d0a9d96779303898631164101bbdc4201d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752910"
---
# <a name="actualsize-property-ado"></a>ActualSize プロパティ (ADO)
フィールドの値をバイト単位の実際の長さを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 返します、**長い**値。  
  
## <a name="remarks"></a>コメント  
 使用して、 **ActualSize**の実際の長さを返すプロパティを[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの値。 すべてのフィールドについて、 **ActualSize**プロパティは読み取り専用です。 ADO の長さを判断できない場合、**フィールド**オブジェクトの値を**ActualSize**プロパティが返す**adUnknown**します。  
  
 **ActualSize**と[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)プロパティは、次の例に示すように異なります。 A**フィールド**の宣言された型を持つオブジェクト**adVarChar**し、50 文字の最大長を返します、 **DefinedSize** 50 のプロパティの値が、 **ActualSize**プロパティの値が返されますが、現在のレコードのフィールドに格納されたデータの長さ。 **フィールド**で、 **DefinedSize**可変長列として扱われます 255 バイトより大きい。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [ActualSize および DefinedSize プロパティの例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize および DefinedSize プロパティの例 (vc++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize プロパティ](../../../ado/reference/ado-api/definedsize-property.md)
