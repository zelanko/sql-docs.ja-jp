---
title: sys.dm_pdw_os_event_logs (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a4916ef80bec444f3de23b8ad601a0da91165c9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  異なるノードに別の Windows のイベントに関する情報をログに記録を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|アプライアンスのノードがこのログはからです。<br /><br /> pdw_node_id と log_name は、このビューのキーを形成します。||  
|log_name|**nvarchar (255)**|Windows イベント ログの名前です。<br /><br /> pdw_node_id と log_name は、このビューのキーを形成します。||  
|log_source|**nvarchar (255)**|Windows イベント ログのソースの名前です。||  
|event_id|**int**|イベントの ID です。 一意ではありません。||  
|event_type|**nvarchar (255)**|重大度を識別する、イベントの種類。|' 情報 '、'Warning'、'Error'|  
|event_message|**nvarchar (4000)**|イベントの詳細。||  
|generate_time|**datetime**|イベントが作成された時刻です。||  
|write_time|**datetime**|イベントがログに実際に書き込まれた時刻です。||  
  
 このビューで保持される最大行数のについてを参照してくださいシステム ビューの最大値、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)トピックです。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
