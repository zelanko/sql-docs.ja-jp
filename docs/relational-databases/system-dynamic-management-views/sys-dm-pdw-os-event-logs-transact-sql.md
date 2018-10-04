---
title: sys.dm_pdw_os_event_logs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ad9c7b96858c1ded81c2651c389ae63490af6408
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47699200"
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  異なるノードに別の Windows のイベントに関する情報をログに記録を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|アプライアンスのノードがこのログはからです。<br /><br /> pdw_node_id と log_name は、このビューのキーを形成します。||  
|log_name|**nvarchar (255)**|Windows イベント ログの名前です。<br /><br /> pdw_node_id と log_name は、このビューのキーを形成します。||  
|log_source|**nvarchar (255)**|Windows イベント ログのソースの名前です。||  
|event_id|**int**|イベントの ID です。 一意ではありません。||  
|event_type|**nvarchar (255)**|重大度を識別する、イベントの種類。|' 情報 '、'Warning'、'Error'|  
|event_message|**nvarchar (4000)**|イベントの詳細。||  
|generate_time|**datetime**|イベントが作成された時刻です。||  
|write_time|**datetime**|イベントがログに実際に書き込まれた時刻です。||  
  
 このビューで保持される最大行数は、詳細については、システム ビューの最大値」セクションを参照してください、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9)トピック。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
