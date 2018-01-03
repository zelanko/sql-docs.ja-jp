---
title: "Status プロパティ (ADO レコード セット) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords: Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26539c8162d53566c31bde8e8f131f0760aed704
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="status-property-ado-recordset"></a>Status プロパティ (ADO レコード セット)
バッチ更新に関して、現在のレコードまたはその他の一括操作の状態を示します。  
  
## <a name="return-value"></a>戻り値  
 1 つ以上の合計を返して[可能](../../../ado/reference/ado-api/recordstatusenum.md)値。  
  
## <a name="remarks"></a>解説  
 使用して、**ステータス**プロパティを確認してどのような変更が保留になって一括更新中に変更されたレコードのです。 使用することも、**ステータス**を呼び出す場合などの一括操作中に失敗したレコードの状態を表示するプロパティ、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)のメソッド、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、または設定、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティを**レコード セット**オブジェクトをブックマークの配列。 このプロパティを使用して、特定のレコードが失敗し、それに応じて解決方法を指定できます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ステータスのプロパティの例 (レコード セット) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Status プロパティの例 (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
