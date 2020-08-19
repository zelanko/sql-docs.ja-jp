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
ms.openlocfilehash: 7869ff91269d033b14a7f77e014da70962a1c1d5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441934"
---
# <a name="status-property-ado-recordset"></a>Status プロパティ (ADO Recordset)
バッチ更新やその他の一括操作に関して、現在のレコードの状態を示します。  
  
## <a name="return-value"></a>戻り値  
 1つ以上の [Recordstatusenum](../../../ado/reference/ado-api/recordstatusenum.md) 値の合計を返します。  
  
## <a name="remarks"></a>解説  
 [ **状態** ] プロパティを使用して、バッチ更新中に変更されたレコードの保留中の変更を確認します。 また、 **status**プロパティを使用して、レコード[セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの[Resync](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、 [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)などのメソッドを呼び出す場合や、レコード**セット**オブジェクトの[Filter](../../../ado/reference/ado-api/filter-property.md)プロパティをブックマークの配列に設定する場合など、一括操作中に失敗したレコードの状態を表示することもできます。 このプロパティを使用すると、特定のレコードが失敗したかどうかを判断し、それに応じて解決できます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Status プロパティの例 (レコードセット) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Status プロパティの例 (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
