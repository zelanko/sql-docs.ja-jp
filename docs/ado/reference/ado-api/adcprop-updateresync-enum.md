---
title: "ADCPROP_UPDATERESYNC_ENUM |Microsoft ドキュメント"
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
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e5c25ab6802b6a99902c9e52990be80ff14ed6d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
指定するかどうか、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドは暗黙的な続けている[再同期](../../../ado/reference/ado-api/resync-method.md)メソッド操作と、そのその操作のスコープです。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|呼び出す**再同期**ADCPROP_UPDATERESYNC_ENUM に関するその他のすべてのメンバーの合計値にします。|  
|**adResyncAutoIncrement**|1|既定値です。 自動的にインクリメントまたは Microsoft Jet AutoNumber フィールドまたは Microsoft SQL Server の Id 列など、データ ソースによって生成されている列の新しい id 値を取得しようとしています。|  
|**adResyncConflicts**|2|呼び出す**再同期**すべての行の同時実行の競合があるため、update または delete 操作が失敗しました。|  
|**adResyncInserts**|8|呼び出す**再同期**すべて正常に挿入された行にします。 ただし、自動増分列の値は再同期できません。 代わりに、新しく挿入された行の内容は、既存の主キーの値に基づいて再同期化されます。 場合は、主キーが自動増分値では、**再同期**目的の行の内容を取得できません。 AutoIncrement 主キーの値を自動的に増分しながら、呼び出す**UpdateBatch**を総合した値と**adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|呼び出されません**再同期**です。|  
|**adResyncUpdates**|4|呼び出す**再同期**すべて正常に更新された行にします。|  
  
## <a name="applies-to"></a>適用対象  
 [再同期のプロパティ-動的 (ADO) の更新します。](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)

