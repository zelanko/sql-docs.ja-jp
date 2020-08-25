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
ms.openlocfilehash: 869daa9afc840e7580e6498510ef07d4be002802
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777081"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue プロパティ
データベース内の [フィールド](./field-object.md) オブジェクトの現在の値を示します。  
  
## <a name="return-value"></a>戻り値  
 **フィールド**の値を示す**バリアント**値を返します。  
  
## <a name="remarks"></a>解説  
 **UnderlyingValue**プロパティを使用して、現在のフィールド値をデータベースから取得します。 **UnderlyingValue**プロパティのフィールド値は、トランザクションに表示される値であり、別のトランザクションによる最近の更新の結果である可能性があります。 これは、もともと[レコードセット](./recordset-object-ado.md)に返された値を反映する[originalvalue](./originalvalue-property-ado.md)プロパティとは異なる場合があります。  
  
 これは、 [Resync](./resync-method.md) メソッドを使用する場合と似ていますが、 **UnderlyingValue** プロパティは、現在のレコードから特定のフィールドの値のみを返します。 これは、再 [同期](./resync-method.md) メソッドが [value](./value-property-ado.md) プロパティを置き換えるために使用するのと同じ値です。  
  
 このプロパティを **Originalvalue** プロパティと共に使用すると、バッチ更新で発生した競合を解決できます。  
  
## <a name="record"></a>Record  
 [レコード](./record-object-ado.md)オブジェクトの場合、 [Update](./update-method.md)が呼び出される前に追加されたフィールドのこのプロパティは空になります。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](./field-object.md)  
  
## <a name="see-also"></a>参照  
 [OriginalValue プロパティと UnderlyingValue プロパティの例 (VB)](./originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue プロパティと UnderlyingValue プロパティの例 (VC + +)](./originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue プロパティ (ADO)](./originalvalue-property-ado.md)   
 [Resync メソッド](./resync-method.md)