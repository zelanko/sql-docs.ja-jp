---
title: ADCPROP_UPDATERESYNC_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATERESYNC_ENUM
helpviewer_keywords:
- ADCPROP_UPDATERESYNC_ENUM [ADO]
ms.assetid: bc9e1a37-e969-47e9-8382-0bbfffa2034f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afaadf62c38c318c759be1c452ff0953ba19c7d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065295"
---
# <a name="adcpropupdateresyncenum"></a>ADCPROP_UPDATERESYNC_ENUM
指定するかどうか、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドの後に、暗黙的な[再同期](../../../ado/reference/ado-api/resync-method.md)メソッドの操作であれば、その操作のスコープ。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adResyncAll**|15|呼び出す**再同期**ADCPROP_UPDATERESYNC_ENUM に関するその他のすべてのメンバーの合計値にします。|  
|**adResyncAutoIncrement**|1|既定値です。 自動的にインクリメントまたは Microsoft Jet オート ナンバー フィールドまたは Microsoft SQL Server の Identity 列など、データ ソースによって生成される列の新しい id 値を取得しようとしています。|  
|**adResyncConflicts**|2|呼び出す**再同期**のすべての行を同時実行の競合があるため、update または delete 操作が失敗しました。|  
|**adResyncInserts**|8|呼び出す**再同期**すべて正常に挿入された行。 ただし、[自動増分] 列の値は再同期できません。 代わりに、新しく挿入された行の内容は、既存の主キー値に基づいて再同期化されます。 主キーが、[自動増分] の値である場合**再同期**目的の行の内容を取得しません。 [自動増分] 主キーの値を自動的にインクリメントを呼び出す**UpdateBatch**を総合した値と**adResyncAutoIncrement** + **adResyncInserts**.|  
|**adResyncNone**|0|呼び出されません**再同期**します。|  
|**adResyncUpdates**|4|呼び出す**再同期**すべて正常に更新された行。|  
  
## <a name="applies-to"></a>適用対象  
 [Update Resync プロパティ - 動的 (ADO)](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)
