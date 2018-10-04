---
title: syscollector_execution_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b89823af1295b329046395a8f3c345401ca61805
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779720"
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セットまたはコレクション パッケージのタスク実行に関する情報を提供します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|各コレクション セットの実行を識別します。 このビューを他の詳細ログと結合するために使用されます。 NULL 値は許可されません。|  
|**task_name**|**nvarchar(128)**|この情報に対応するコレクション セット タスクまたはコレクション パッケージ タスクの名前です。 NULL 値は許可されません。|  
|**execution_row_count_in**|**int**|データ フローの最初に処理される行数です。 NULL 値が許可されます。|  
|**execution_row_count_out**|**int**|データ フローの最後に処理される行数です。 NULL 値が許可されます。|  
|**execution_row_count_errors**|**int**|データ フロー中に失敗した行数です。 NULL 値が許可されます。|  
|**execution_time_ms**|**int**|タスクの完了に要する時間 (ミリ秒単位) です。 NULL 値が許可されます。|  
|**log_time**|**datetime**|この情報が記録された日時です。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 に対する SELECT 権限が必要です**dc_operator**します。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
