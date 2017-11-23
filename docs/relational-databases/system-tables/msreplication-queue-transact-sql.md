---
title: "MSreplication_queue (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs: TSQL
helpviewer_keywords: MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25bbbc37215010d60cd20a01ea06cb35176eabf5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_queue** SQL ベースを使用するキュー更新サブスクリプションのキューに置かれたすべてによって発行されたキューに置かれたコマンドを格納するテーブルがレプリケーション プロセスによって使用されます。 次の表は、サブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**tranid**|**sysname**|キューに登録されたコマンドが実行されたときのトランザクション ID。|  
|**データ**|**varbinary (8000)**|キューに登録されたコマンドに関する情報を格納するパック バイトストリームです。|  
|**datalen**|**int**|データの長さ (バイト単位) です。|  
|**commandtype**|**int**|キューに登録されるコマンドのタイプです。<br /><br /> 1 = トランザクション内のユーザー コマンド<br /><br /> 2 = サブスクリプション同期コマンド|  
|**insertdate**|**datetime**|挿入日時です。|  
|**orderkey**|**bigint**|単調に増加する ID 列です。|  
|**cmdstate**|**bit**|コマンドの状態です。<br /><br /> 0 = 完了<br /><br /> 1 = 一部実行|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
