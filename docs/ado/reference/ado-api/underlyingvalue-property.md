---
description: UnderlyingValue プロパティ
title: UnderlyingValue Property |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
author: rothja
ms.author: jroth
ms.openlocfilehash: 12788438d7db4cf51df564ea7d262bb4e7ef693d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441704"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue プロパティ
データベース内の [フィールド](../../../ado/reference/ado-api/field-object.md) オブジェクトの現在の値を示します。  
  
## <a name="return-value"></a>戻り値  
 **フィールド**の値を示す**バリアント**値を返します。  
  
## <a name="remarks"></a>解説  
 **UnderlyingValue**プロパティを使用して、現在のフィールド値をデータベースから取得します。 **UnderlyingValue**プロパティのフィールド値は、トランザクションに表示される値であり、別のトランザクションによる最近の更新の結果である可能性があります。 これは、もともと[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)に返された値を反映する[originalvalue](../../../ado/reference/ado-api/originalvalue-property-ado.md)プロパティとは異なる場合があります。  
  
 これは、 [Resync](../../../ado/reference/ado-api/resync-method.md) メソッドを使用する場合と似ていますが、 **UnderlyingValue** プロパティは、現在のレコードから特定のフィールドの値のみを返します。 これは、再 [同期](../../../ado/reference/ado-api/resync-method.md) メソッドが [value](../../../ado/reference/ado-api/value-property-ado.md) プロパティを置き換えるために使用するのと同じ値です。  
  
 このプロパティを **Originalvalue** プロパティと共に使用すると、バッチ更新で発生した競合を解決できます。  
  
## <a name="record"></a>Record  
 [レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの場合、 [Update](../../../ado/reference/ado-api/update-method.md)が呼び出される前に追加されたフィールドのこのプロパティは空になります。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [OriginalValue プロパティと UnderlyingValue プロパティの例 (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue プロパティと UnderlyingValue プロパティの例 (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue プロパティ (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)
