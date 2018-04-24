---
title: UnderlyingValue プロパティ |Microsoft ドキュメント
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
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0fa427c2410079d028afb99a839f39fefa003264
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="underlyingvalue-property"></a>UnderlyingValue プロパティ
現在の値を示す、[フィールド](../../../ado/reference/ado-api/field-object.md)データベース内のオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**の値を示す値、**フィールド**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **UnderlyingValue**プロパティをデータベースから現在のフィールド値を返します。 フィールドの値で、 **UnderlyingValue**プロパティは、値は、トランザクションを表示し、別のトランザクションによって新しい更新プログラムの結果である可能性があります。 これが異なる場合があります、 [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)プロパティで、最初に返された値を反映して、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
 これを使用すると同様、[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドですが、 **UnderlyingValue**プロパティは、現在のレコードから特定のフィールドの値のみを返します。 これは、同じ値を[再同期](../../../ado/reference/ado-api/resync-method.md)置換するメソッドを使用して、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティです。  
  
 このプロパティを使用する場合、 **OriginalValue**プロパティ、バッチ更新から発生する競合を解決することができます。  
  
## <a name="record"></a>レコード  
 [レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトをこのプロパティは空にする前に追加されたフィールドについてなります[更新](../../../ado/reference/ado-api/update-method.md)と呼びます。  
  
## <a name="applies-to"></a>適用対象  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>参照  
 [OriginalValue と UnderlyingValue プロパティの例 (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue と UnderlyingValue プロパティの例 (vc++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue プロパティ (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)
