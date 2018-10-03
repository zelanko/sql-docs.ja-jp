---
title: trace_xe_action_map (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_action_map_TSQL
- trace_xe_action_map
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], tables
- trace_xe_action_map
ms.assetid: 208a1413-ce7f-4521-b765-d74723627302
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7308df1dafe80d4c4b342c6b5797db6354f98416
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827180"
---
# <a name="extended-events-tables---tracexeactionmap"></a>拡張イベント テーブル - trace_xe_action_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SQL トレース列 ID に割り当てられている拡張イベントのアクションごとに 1 行のデータを格納します。 このテーブルは、sys スキーマ内の master データベースに保存します。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|trace_column_id|**smallint**|マップされる SQL トレース列の ID です。|  
|package_name|**nvarchar(60)**|マップされたアクションがある拡張イベント パッケージの名前です。|  
|xe_action_name|**nvarchar(60)**|SQL トレース列にマップされている拡張イベントのアクションの名前です。|  
  
## <a name="remarks"></a>コメント  
 次のクエリを使用すると、SQL トレース列に相当する拡張イベントのアクショントを特定できます。  
  
```  
SELECT tc.name AS trace_column, am.package_name, am.xe_action_name  
FROM sys.trace_columns AS tc  
INNER JOIN sys.trace_xe_action_map AS am  
   ON tc.trace_column_id = am.trace_column_id  
```  
  
 アクションにマップされない SQL トレース列はテーブルに含まれていません。  
  
## <a name="see-also"></a>参照  
 [trace_xe_event_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-event-map.md)  
  
  
