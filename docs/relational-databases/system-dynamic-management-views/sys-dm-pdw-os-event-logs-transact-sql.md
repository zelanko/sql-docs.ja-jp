---
title: dm_pdw_os_event_logs (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 819b38bce871bd1a43b3d259d23b2c95fb6dfdd3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086210"
---
# <a name="sysdm_pdw_os_event_logs-transact-sql"></a>dm_pdw_os_event_logs (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  異なるノード上のさまざまな Windows イベントログに関する情報を保持します。  
  
|列名|データ型|[説明]|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|このログの基になっているアプライアンスノード。<br /><br /> このビューのキーは pdw_node_id と log_name によって形成されます。||  
|log_name|**nvarchar(255)**|Windows イベントログの名前。<br /><br /> このビューのキーは pdw_node_id と log_name によって形成されます。||  
|log_source|**nvarchar(255)**|Windows イベントログのソース名。||  
|event_id|**int**|イベントの ID。 一意ではありません。||  
|event_type|**nvarchar(255)**|重大度を識別するイベントの種類。|' Information '、' Warning '、' Error '|  
|event_message|**nvarchar(4000)**|イベントの詳細。||  
|generate_time|**DATETIME**|イベントが作成された時刻。||  
|write_time|**DATETIME**|イベントが実際にログに書き込まれた時刻。||  
  
 このビューで保持される最大行数の詳細については、「[容量制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)」トピックの「メタデータ」セクションを参照してください。 
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
