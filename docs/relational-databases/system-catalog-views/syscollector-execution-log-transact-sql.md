---
title: syscollector_execution_log (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_TSQL
- syscollector_execution_log
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log view
ms.assetid: 11554d64-0426-42ce-b7ce-5591f67864d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e982c086bdae807220a2c9cf1c9e3260d0d66a83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773497"
---
# <a name="syscollectorexecutionlog-transact-sql"></a>syscollector_execution_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セットまたはコレクション パッケージの実行ログからの情報を提供します。   
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|各コレクション セットの実行を識別します。 このビューを他の詳細ログと結合するために使用されます。 NULL 値は許可されません。|  
|parent_log_id|**bigint**|親のパッケージまたはコレクション セットを識別します。 NULL 値は許可されません。 ID は親子関係としてチェーン化されます。これにより、どのパッケージがどのコレクション セットによって開始されたかを判別できます。 このビューは、ログ エントリをその親と子リンケージでグループ化され、呼び出しチェーンが明確に表示されるよう、パッケージの名前にインデントを設定します。|  
|collection_set_id|**int**|このログ エントリが表すコレクション セットまたはコレクション パッケージを識別します。 NULL 値は許可されません。|  
|collection_item_id|**int**|コレクション アイテムを識別します。 NULL 値が許可されます。|  
|start_time|**datetime**|コレクション セットまたはコレクション パッケージが開始された日時です。 NULL 値は許可されません。|  
|last_iteration_time|**datetime**|継続的に実行されるパッケージで、スナップショットが最後にキャプチャされた日時を表します。 NULL 値が許可されます。|  
|finish_time|**datetime**|完了済みのパッケージおよびコレクション セットについて、実行が完了した日時を表します。 NULL 値が許可されます。|  
|runtime_execution_mode|**smallint**|コレクション セットのアクティビティが、データの収集かデータのアップロードかを示します。 NULL 値が許可されます。<br /><br /> 値は次のとおりです。<br /><br /> 0 = コレクション<br /><br /> 1 = アップロード|  
|status|**smallint**|コレクション セットまたはコレクション パッケージの現在のステータスを示します。 NULL 値は許可されません。<br /><br /> 値は次のとおりです。<br /><br /> 0 = 実行中<br /><br /> 1 = が完了しました<br /><br /> 2 = 失敗|  
|演算子 (operator)|**nvarchar(128)**|コレクション セットまたはコレクション パッケージをだれが開始したかを示します。 NULL 値は許可されません。|  
|package_id|**uniqueidentifier**|このログを生成したコレクション セットまたはコレクション パッケージを識別します。 NULL 値が許可されます。|  
|package_name|**nvarchar (4000)**|このログを生成したパッケージの名前です。 NULL 値が許可されます。|  
|package_execution_id|**uniqueidentifier**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] ログ テーブルへのリンクを提供します。 NULL 値が許可されます。|  
|failure_message|**nvarchar(2048)**|コレクション セットまたはコレクション パッケージでエラーが発生した場合に、そのコンポーネントの最近のエラー メッセージを表します。 NULL 値が許可されます。 詳細なエラー情報を取得する、 [fn_syscollector_get_execution_details &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md)関数。|  
  
## <a name="permissions"></a>アクセス許可  
 dc_operator に対する SELECT 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
