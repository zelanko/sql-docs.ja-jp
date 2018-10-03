---
title: syscollector_execution_log_full (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_full
- syscollector_execution_log_full_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log_full view
ms.assetid: 6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99ce8003b70ad41be225a7678c97ed44d9f6c7dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755870"
---
# <a name="syscollectorexecutionlogfull-transact-sql"></a>syscollector_execution_log_full (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行ログがいっぱいになったときにコレクション セットまたはコレクション パッケージに関する情報を提供します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|各コレクション セットの実行を識別します。 このビューを他の詳細ログと結合するために使用されます。 NULL 値が許可されます。|  
|parent_log_id|**bigint**|親のパッケージまたはコレクション セットを識別します。 NULL 値は許可されません。 ID は親子関係としてチェーン化されます。これにより、どのパッケージがどのコレクション セットによって開始されたかを判別できます。 このビューでは、呼び出しチェーンを明確に判別できるように、ログ エントリが親子関係に基づいてグループ化され、パッケージの名前にインデントが設定されます。|  
|NAME|**nvarchar (4000)**|このログ エントリが表すコレクション セットまたはコレクション パッケージの名前です。 NULL 値が許可されます。|  
|status|**smallint**|コレクション セットまたはコレクション パッケージの現在のステータスを示します。 NULL 値が許可されます。<br /><br /> 値は次のとおりです。<br /><br /> 0 = 実行中<br /><br /> 1 = が完了しました<br /><br /> 2 = 失敗|  
|runtime_execution_mode|**smallint**|コレクション セットのアクティビティが、データの収集かデータのアップロードかを示します。 NULL 値が許可されます。|  
|start_time|**datetime**|コレクション セットまたはコレクション パッケージが開始された日時です。 NULL 値が許可されます。|  
|last_iteration_time|**datetime**|継続的に実行されるパッケージで、スナップショットが最後にキャプチャされた日時を表します。 NULL 値が許可されます。|  
|finish_time|**datetime**|完了済みのパッケージおよびコレクション セットについて、実行が完了した日時を表します。 NULL 値が許可されます。|  
|duration|**int**|パッケージまたはコレクション セットが実行されている時間 (秒) です。 NULL 値が許可されます。|  
|failure_message|**nvarchar(2048)**|コレクション セットまたはコレクション パッケージでエラーが発生した場合に、そのコンポーネントの最近のエラー メッセージを表します。 NULL 値が許可されます。 詳細なエラー情報を取得する、 [fn_syscollector_get_execution_details &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md)関数。|  
|演算子 (operator)|**nvarchar(128)**|コレクション セットまたはコレクション パッケージをだれが開始したかを示します。 NULL 値が許可されます。|  
|package_execution_id|**uniqueidentifier**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] ログ テーブルへのリンクを提供します。 NULL 値が許可されます。|  
|collection_set_id|**int**|msdb 内のデータ コレクション構成テーブルへのリンクを提供します。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 SELECT 権限が必要**dc_operator**します。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
