---
title: ActualSize プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f71de5881975eb9ba38b2d21ef8f1590aae95d90
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275101"
---
# <a name="actualsize-property-ado"></a>ActualSize プロパティ (ADO)
フィールドの値をバイト単位の実際の長さを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 返します、**長い**値。  
  
## <a name="remarks"></a>コメント  
 使用して、 **ActualSize**の実際の長さを取得するプロパティ、[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトの値。 すべてのフィールドについて、 **ActualSize**プロパティは読み取り専用です。 ADO の長さを判断できない場合、**フィールド**オブジェクトの値、 **ActualSize**プロパティから返される**adUnknown**です。  
  
 **ActualSize**と[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)プロパティは、次の例で示すように異なります、します。 A**フィールド**の宣言された型とオブジェクト**それぞれ**し、50 文字の最大長を返します、 **DefinedSize** 50 でのプロパティの値が、 **ActualSize**プロパティの値が返されますが、現在のレコードのフィールドに格納されているデータの長さ。 **フィールド**で、 **DefinedSize** 255 バイトは、可変長の列として扱われます。 より大きい。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [ActualSize と DefinedSize プロパティの例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize と DefinedSize プロパティの例 (vc++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize プロパティ](../../../ado/reference/ado-api/definedsize-property.md)
