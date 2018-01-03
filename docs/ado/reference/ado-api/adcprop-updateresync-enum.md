---
title: "ADCPROP_UPDATERESYNC_ENUM |Microsoft ドキュメント"
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
f1_keywords: ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords: ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d030fa1643cbf836a7380dd3113236ec7961b8d0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
指定するかどうか、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドは暗黙的な続けている[再同期](../../../ado/reference/ado-api/resync-method.md)メソッド操作と、そのその操作のスコープです。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|呼び出す**再同期**ADCPROP_UPDATERESYNC_ENUM に関するその他のすべてのメンバーの合計値にします。|  
|**adResyncAutoIncrement**|@shouldalert|既定値です。 自動的にインクリメントまたは Microsoft Jet AutoNumber フィールドまたは Microsoft SQL Server の Id 列など、データ ソースによって生成されている列の新しい id 値を取得しようとしています。|  
|**adResyncConflicts**|2|呼び出す**再同期**すべての行の同時実行の競合があるため、update または delete 操作が失敗しました。|  
|**adResyncInserts**|8|呼び出す**再同期**すべて正常に挿入された行にします。 ただし、自動増分列の値は再同期できません。 代わりに、新しく挿入された行の内容は、既存の主キーの値に基づいて再同期化されます。 場合は、主キーが自動増分値では、**再同期**目的の行の内容を取得できません。 AutoIncrement 主キーの値を自動的に増分しながら、呼び出す**UpdateBatch**を総合した値と**adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|呼び出されません**再同期**です。|  
|**adResyncUpdates**|4|呼び出す**再同期**すべて正常に更新された行にします。|  
  
## <a name="applies-to"></a>適用対象  
 [Update Resync プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
