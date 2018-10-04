---
title: sysmergesubscriptions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysmergesubscriptions_TSQL
- sysmergesubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubscriptions system table
ms.assetid: 6adc78da-991d-4c08-98c3-ecb4762e0e99
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e8e94cb9660d3b53ff3ed8db75dd500cde9067e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806540"
---
# <a name="sysmergesubscriptions-transact-sql"></a>sysmergesubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既知のサブスクライバーごとに 1 行を保持する、パブリッシャー側のローカル テーブルです。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|subscriber_server|**sysname**|サーバーの ID です。 サブスクリプション データベースのコピーを別のサーバーに移動する際、srvid フィールドをサーバー固有の値にマップするために使用されます。|  
|db_name|**sysname**|サブスクライブするデータベースの名前です。|  
|pubid|**uniqueidentifier**|現在のサブスクリプションが作成されたパブリケーションの ID です。|  
|datasource_type|**int**|データ ソースのタイプです。<br /><br /> **0** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **2** jet OLE DB を = です。|  
|subid|**uniqueidentifier**|サブスクリプションの一意な ID 番号です。|  
|replnickname|**[バイナリ]**|レプリカの圧縮されたニックネームです。|  
|replicastate|**uniqueidentifier**|パブリッシャー側の値をサブスクライバー側の値と比較して前回の同期が成功したかどうかを判断するために使用される一意識別子です。|  
|status|**tinyint**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = アクティブ。<br /><br /> **2** = を削除します。|  
|subscriber_type|**int**|サブスクライバーのタイプです。<br /><br /> **1**グローバル =。<br /><br /> **2**ローカルを = です。<br /><br /> **3** = 匿名です。|  
|subscription_type|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ。<br /><br /> **1** = プルします。<br /><br /> **2** = 匿名です。|  
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
|attempted_validate|**datetime**|最後の**datetime**サブスクリプションの検証が試行されたことです。|  
|last_sync_date|**datetime**|**Datetime**同期します。|  
|last_sync_status|**int**|サブスクリプションの状態です。<br /><br /> **0** = すべてのジョブが開始を待機しています。<br /><br /> **1** = 1 つまたは複数のジョブを開始します。<br /><br /> **2** = すべてのジョブが正常に実行されました。<br /><br /> **3** = 少なくとも 1 つジョブを実行します。<br /><br /> **4** = すべてのジョブがスケジュールされ、アイドル状態です。<br /><br /> **5** = 少なくとも 1 つジョブが前回のエラーの後に実行しようとしています。<br /><br /> **6** = 少なくとも 1 つが正常に実行するジョブが失敗しました。|  
|last_sync_summary|**sysname**|前回の同期の結果の説明です。|  
|metadatacleanuptime|**datetime**|最後の**datetime**その有効期限が切れたメタデータがマージ レプリケーション システム テーブルから削除されました。|  
|partition_id|**int**|サブスクリプションが所属する事前計算済みパーティションを識別します。|  
|cleanedup_unsent_changes|**bit**|未送信の変更用のメタデータがサブスクライバー側でクリーンアップされたことを示します。|  
|replica_version|**int**|サブスクリプションが所属するサブスクライバー用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを識別します。次のいずれかの値になります。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|supportability_mode|**int**|内部使用のみです。|  
|application_name|**nvarchar(128)**|内部使用のみです。|  
|subscriber_number|**int**|内部使用のみです。|  
|last_makegeneration_datetime|**datetime**|最後の**datetime** makegeneration プロセスがパブリッシャーに対して実行されました。 詳細については、-makegenerationinterval パラメーターを参照してください。 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
