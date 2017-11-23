---
title: "MSdistribution_agents (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/28/2015
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
- MSdistribution_agents_TSQL
- MSdistribution_agents
dev_langs: TSQL
helpviewer_keywords: MSdistribution_agents system table
ms.assetid: 0e8f0653-1351-41d1-95d2-40f6d5a050ca
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f71cc1c79f36dcc14980ce4a04b1079fba6a8ee9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msdistributionagents-transact-sql"></a>MSdistribution_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdistribution_agents**テーブルには、ローカルのディストリビューターで実行されるディストリビューション エージェントごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ディストリビューション エージェントの ID。|  
|**name**|**nvarchar (100)**|ディストリビューション エージェントの名前。|  
|**化コ**|**int**|パブリッシャー データベースの ID。|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**subscriber_id**|**smallint**|既知のエージェントだけが使用するサブスクライバーの ID。 匿名のエージェントに対しては、予約済みとなります。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ。<br /><br /> **1**プルを = です。<br /><br /> **2** = 匿名です。|  
|**local_job**|**bit**|ローカル ディストリビューターに SQL Server エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**binary (16)**|ジョブの識別番号。|  
|**subscription_guid**|**binary (16)**|エージェントのサブスクリプションの GUID 値。|  
|**profile_id**|**int**|構成の ID、 [MSagent_profiles (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブル。|  
|**anonymous_subid**|**uniqueidentifier**|匿名エージェントの ID です。|  
|**subscriber_name**|**sysname**|匿名のエージェントだけが使用するサブスクライバーの名前。|  
|**virtual_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**anonymous_agent_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**creation_date**|**datetime**|ディストリビューション エージェントまたはマージ エージェントが作成された日時。|  
|**queue_id**|**sysname**|キュー更新サブスクリプションのキューを判別するための識別子。 キューに登録されていないサブスクリプションの場合、値は NULL です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キュー ベースのパブリケーションでは、値は、サブスクリプションに使用するキューを一意に識別する GUID。 SQL Server ベースのキュー パブリケーションの場合、列に値が含まれています**SQL**です。<br /><br /> 注: を使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューは廃止されており、現在サポートされていません。|  
|**queue_status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offload_enabled**|**bit**|エージェントをリモートから起動できるかどうかを示します。<br /><br /> **0**エージェントをリモートでアクティブにできませんを指定します。<br /><br /> **1**リモートとで指定されたリモート コンピューターで、エージェントをアクティブ化にすることを指定します、 *offload_server*プロパティです。|  
|**offload_server**|**sysname**|エージェントをリモートから起動するときに使用するサーバーのネットワーク名。|  
|**dts_package_name**|**sysname**|DTS パッケージの名前です。 たとえば、という名前のパッケージ**DTSPub_Package**、指定`@dts_package_name = N'DTSPub_Package'`です。|  
|**dts_package_password**|**nvarchar (524)**|パッケージのパスワード。|  
|**dts_package_location**|**int**|パッケージの場所。 パッケージの場所を指定できます**ディストリビューター**または**サブスクライバー**です。|  
|**sid**|**varbinary (85)**|最初の実行時の、ディストリビューション エージェントまたはマージ エージェントのセキュリティ識別番号 (SID) です。|  
|**queue_server**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**subscriber_security_mode**|**smallint**|サブスクライバーに接続するときにエージェントが使用するセキュリティ モードです。次のいずれかの値をとります。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server 認証<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証です。|  
|**subscriber_login**|**sysname**|サブスクライバーに接続するときに使用するログイン名です。|  
|**subscriber_password**|**nvarchar (524)**|サブスクライバーに接続するときに使用するパスワードの暗号化された値。|  
|**reset_partial_snapshot_progress**|**bit**|途中までしかダウンロードされていないスナップショットを破棄して、スナップショット プロセス全体を最初からやり直すかどうかを示します。|  
|**job_step_uid**|**uniqueidentifier**|SQL Server エージェント ジョブの一意の ID はステップが、エージェントを開始します。|  
|**subscriptionstreams**|**tinyint**|変更のバッチをサブスクライバーに並列的に適用するために、ディストリビューション エージェントごとに許可される接続の数を設定します。 サポートされている値の範囲は 1 ～ 64 です。|  
|**メモリ最適化**|**bit**|1 は、メモリ最適化テーブルのサブスクライバーを使用できることを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
