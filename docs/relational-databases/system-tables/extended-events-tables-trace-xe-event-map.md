---
title: trace_xe_event_map (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_event_map_TSQL
- trace_xe_event_map
dev_langs:
- TSQL
helpviewer_keywords:
- trace_xe_event_map
- extended events [SQL Server], tables
ms.assetid: 537aa292-3540-47e8-be28-56dc01abc343
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc823459c701bd0045e594f753a803a0a092a244
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817108"
---
# <a name="extended-events-tables---tracexeeventmap"></a>拡張イベント テーブル - trace_xe_event_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SQL トレース イベント クラスに割り当てられている拡張イベントのイベントごとに 1 行のデータを格納します。 このテーブルは、sys スキーマ内の master データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|trace_event_id|**smallint**|マップされている SQL トレース イベント クラスの ID。|  
|package_name|**nvarchar(60)**|マップされたイベントが存在する拡張イベント パッケージの名前。|  
|xe_event_name|**nvarchar(60)**|SQL トレース イベントのクラスにマップされている拡張イベントのイベントの名前。|  
  
## <a name="remarks"></a>コメント  
 次のクエリを使用すると、SQL トレース イベント クラスと同様の拡張イベントを特定できます。  
  
```  
SELECT te.name, xe.package_name, xe.xe_event_name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NOT NULL  
```  
  
 すべてのイベント クラスに同等の拡張イベントが存在するとは限りません。 次のクエリを使用すると、拡張イベントと同様ではないイベント クラスの一覧を表示できます。  
  
```  
SELECT te.trace_event_id, te.name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NULL  
```  
  
 前のクエリでは、返されるイベント クラスのほとんどは、監査に関係しています。 監査には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査を使用することをお勧めします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査では、拡張イベントを使用して監査を作成します。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [trace_xe_action_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)  
  
  
