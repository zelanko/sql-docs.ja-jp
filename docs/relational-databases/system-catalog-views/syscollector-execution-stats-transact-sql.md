---
title: syscollector_execution_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_execution_stats
- syscollector_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_execution_stats view
- data collector view
ms.assetid: 23e35ac5-fbbf-4922-970c-f4fac44c1263
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e08a724fa5186a6615a73bb288e6005b40b8f5a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セットまたはコレクション パッケージのタスク実行に関する情報を提供します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|各コレクション セットの実行を識別します。 このビューを他の詳細ログと結合するために使用されます。 NULL 値は許可されません。|  
|**task_name**|**nvarchar(128)**|この情報に対応するコレクション セット タスクまたはコレクション パッケージ タスクの名前です。 NULL 値は許可されません。|  
|**execution_row_count_in**|**int**|データ フローの最初に処理される行数です。 NULL 値が許可されます。|  
|**execution_row_count_out**|**int**|データ フローの最後に処理される行数です。 NULL 値が許可されます。|  
|**execution_row_count_errors**|**int**|データ フロー中に失敗した行数です。 NULL 値が許可されます。|  
|**execution_time_ms**|**int**|タスクの完了に要する時間 (ミリ秒単位) です。 NULL 値が許可されます。|  
|**log_time**|**datetime**|この情報が記録された日時です。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 に対する SELECT 権限が必要です**dc_operator**です。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
