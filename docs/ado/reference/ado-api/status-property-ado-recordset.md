---
description: Status プロパティ (ADO Recordset)
title: Status プロパティ (ADO Recordset) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: rothja
ms.author: jroth
ms.openlocfilehash: cea09babfd2dacf35705adc71cddcdee99aad544
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777301"
---
# <a name="status-property-ado-recordset"></a>Status プロパティ (ADO Recordset)
バッチ更新やその他の一括操作に関して、現在のレコードの状態を示します。  
  
## <a name="return-value"></a>戻り値  
 1つ以上の [Recordstatusenum](./recordstatusenum.md) 値の合計を返します。  
  
## <a name="remarks"></a>解説  
 [ **状態** ] プロパティを使用して、バッチ更新中に変更されたレコードの保留中の変更を確認します。 また、 **status**プロパティを使用して、レコード[セット](./recordset-object-ado.md)オブジェクトの[Resync](./resync-method.md)、 [UpdateBatch](./updatebatch-method.md)、 [CancelBatch](./cancelbatch-method-ado.md)などのメソッドを呼び出す場合や、レコード**セット**オブジェクトの[Filter](./filter-property.md)プロパティをブックマークの配列に設定する場合など、一括操作中に失敗したレコードの状態を表示することもできます。 このプロパティを使用すると、特定のレコードが失敗したかどうかを判断し、それに応じて解決できます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Status プロパティの例 (レコードセット) (VB)](./status-property-example-recordset-vb.md)   
 [Status プロパティの例 (VC++)](./status-property-example-vc.md)