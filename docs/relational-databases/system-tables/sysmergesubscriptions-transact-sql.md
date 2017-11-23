---
title: "sysmergesubscriptions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sysmergesubscriptions_TSQL
- sysmergesubscriptions
dev_langs: TSQL
helpviewer_keywords: sysmergesubscriptions system table
ms.assetid: 6adc78da-991d-4c08-98c3-ecb4762e0e99
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd713b90c4d295eee99953c6561e9a7d057fc39b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergesubscriptions-transact-sql"></a>sysmergesubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既知のサブスクライバーごとに 1 行を保持する、パブリッシャー側のローカル テーブルです。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|subscriber_server|**sysname**|サーバーの ID です。 サブスクリプション データベースのコピーを別のサーバーに移動する際、srvid フィールドをサーバー固有の値にマップするために使用されます。|  
|db_name|**sysname**|サブスクライブするデータベースの名前です。|  
|pubid|**uniqueidentifier**|現在のサブスクリプションが作成されたパブリケーションの ID です。|  
|datasource_type|**int**|データ ソースのタイプです。<br /><br /> **0** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **2** jet OLE DB を = です。|  
|subid|**uniqueidentifier**|サブスクリプションの一意な ID 番号です。|  
|replnickname|**[バイナリ]**|レプリカの圧縮されたニックネームです。|  
|replicastate|**uniqueidentifier**|パブリッシャー側の値をサブスクライバー側の値と比較して前回の同期が成功したかどうかを判断するために使用される一意識別子です。|  
|ステータス|**tinyint**|サブスクリプションの状態です。<br /><br /> **0** = 非アクティブです。<br /><br /> **1**アクティブを = です。<br /><br /> **2** = 削除します。|  
|subscriber_type|**int**|サブスクライバーのタイプです。<br /><br /> **1** = グローバルです。<br /><br /> **2**ローカルを = です。<br /><br /> **3** = 匿名です。|  
|subscription_type|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ。<br /><br /> **1**プルを = です。<br /><br /> **2** = 匿名です。|  
|sync_type|**tinyint**|同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = 同期なし。|  
|description|**nvarchar (255)**|サブスクリプションの簡単な説明です。|  
|priority|**real**|サブスクリプション優先度を指定し、優先度に基づく競合解決を実装します。 等しい**0.00**のすべてのローカルまたは匿名サブスクリプションです。|  
|recgen|**bigint**|前回受信した generation 値です。|  
|recguid|**uniqueidentifier**|前回受信した generation 値の一意な ID です。|  
|sentgen|**bigint**|前回送信した generation 値です。|  
|sentguid|**uniqueidentifier**|前回送信した generation 値の一意な ID です。|  
|schemaversion|**int**|前回受信したスキーマの値です。|  
|schemaguid|**uniqueidentifier**|前回受信したスキーマの一意な ID です。|  
|last_validated|**datetime**|**Datetime**サブスクライバー データの最後に正常に検証します。|  
|attempted_validate|**datetime**|最後の**datetime**サブスクリプションに対して検証が試行されたことです。|  
|last_sync_date|**datetime**|**Datetime**同期します。|  
|last_sync_status|**int**|サブスクリプションの状態です。<br /><br /> **0** = すべてのジョブが開始を待機しています。<br /><br /> **1** = 1 つまたは複数のジョブを開始します。<br /><br /> **2** = すべてのジョブが正常に実行されました。<br /><br /> **3** = 少なくとも 1 つジョブを実行します。<br /><br /> **4** = すべてのジョブがスケジュールされ、アイドル状態です。<br /><br /> **5** = 少なくとも 1 つジョブが前回のエラーの後に実行しようとしています。<br /><br /> **6** = 少なくとも 1 つは正常に実行するジョブが失敗しました。|  
|last_sync_summary|**sysname**|前回の同期の結果の説明です。|  
|metadatacleanuptime|**datetime**|最後の**datetime**その有効期限の切れたメタデータがマージ レプリケーション システム テーブルから削除されました。|  
|partition_id|**int**|サブスクリプションが所属する事前計算済みパーティションを識別します。|  
|cleanedup_unsent_changes|**bit**|未送信の変更用のメタデータがサブスクライバー側でクリーンアップされたことを示します。|  
|replica_version|**int**|サブスクリプションが所属するサブスクライバー用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを識別します。次のいずれかの値になります。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|supportability_mode|**int**|内部使用のみです。|  
|application_name|**nvarchar (128)**|内部使用のみです。|  
|subscriber_number|**int**|内部使用のみです。|  
|last_makegeneration_datetime|**datetime**|最後の**datetime** makegeneration プロセスがパブリッシャーに対して実行されました。 詳細については、-makegenerationinterval パラメーターを参照してください。[レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
