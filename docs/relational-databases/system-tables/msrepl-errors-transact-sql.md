---
title: MSrepl_errors (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSrepl_errors
- MSrepl_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_errors system table
ms.assetid: c6e023c1-2c32-4269-8d76-e442ea309e4b
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 992e5594f208cd64ef48d90f2b29e7018719a6da
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103720"
---
# <a name="msreplerrors-transact-sql"></a>MSrepl_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_errors**テーブルには、ディストリビューション エージェントおよびマージ エージェントのエラーに関する拡張情報を持つ行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|エラーの ID。|  
|**time**|**datetime**|エラーが発生した時刻。|  
|**error_type_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**source_type_id**|**int**|エラー ソースの種類の ID。|  
|**source_name**|**nvarchar(100)**|エラー ソースの名前です。|  
|**error_code**|**sysname**|エラー コード。|  
|**error_text**|**ntext**|エラー メッセージです。|  
|**xact_seqno**|**varbinary(16)**|失敗した実行バッチの先頭のトランザクション ログ シーケンス番号です。 これは、ディストリビューション エージェントでのみ使用されます。失敗した実行バッチ内にある、先頭のトランザクションのトランザクション ログ シーケンス番号です。|  
|**command_id**|**int**|失敗した実行バッチのコマンド ID。 これは、ディストリビューション エージェントでのみ使用されます。失敗した実行バッチ内にある、先頭のコマンドのコマンド ID です。|  
|**session_id**|**int**|エラーが発生したエージェント セッションの ID。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
