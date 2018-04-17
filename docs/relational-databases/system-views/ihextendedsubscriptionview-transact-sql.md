---
title: IHextendedSubscriptionView (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c4425a28e270c738a2908e0595f796fdded3710a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHextendedSubscriptionView**ビューは、SQL Server 以外のパブリケーションに対するサブスクリプションの情報を公開します。 このビューは、**配布**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|アーティクルの一意識別子。|  
|**dest_db**|**sysname**|転送先データベースの名前。|  
|**srvid**|**smallint**|サブスクライバーの一意識別子。|  
|**login_name**|**sysname**|サブスクライバーに接続するときに使用するログイン名。|  
|**distribution_jobid**|**[バイナリ]**|ディストリビューション エージェント ジョブを識別します。|  
|**publisher_database_id**|**int**|パブリケーション データベースの識別子。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ、ディストリビューション エージェントに、サブスクライバーで実行されます。<br /><br /> **1** = プル、ディストリビューション エージェントがディストリビューターで実行されます。|  
|**sync_type**|**tinyint**|初期同期の種類。<br /><br /> **1**自動を =<br /><br /> **2** = なし|  
|**ステータス**|**tinyint**|サブスクリプションの状態です。<br /><br /> **0** = 非アクティブ<br /><br /> **1** = サブスクライブ<br /><br /> **2** = アクティブ|  
|**snapshot_seqno_flag**|**bit**|スナップショット シーケンス番号が使用されているかどうかを示します。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。<br /><br /> **0** = パブリケーションでは共有ディストリビューション エージェントを使用して、パブリッシャー データベース/サブスクライバー データベースの各ペアが 1 つの共有エージェントです。<br /><br /> **1** = このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。|  
|**subscription_time**|**datetime**|内部使用のみです。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **1** = は送信しません。<br /><br /> **0** = 戻す。|  
|**agent_id**|**int**|ディストリビューション エージェントの一意識別子。|  
|**update_mode**|**tinyint**|更新モードの種類を示します。次のいずれかの値になります。<br /><br /> **0** = 読み取り専用です。<br /><br /> **1** = 即時更新します。<br /><br /> **2**メッセージ キューを使用するキュー更新を = です。<br /><br /> **3**イミディ エイト = メッセージ キューを使用してフェールオーバーとしてキューに置かれた更新プログラムで更新します。<br /><br /> **4** SQL Server キューを使用するキュー更新を = です。<br /><br /> **5** = キュー更新フェールオーバーでは、SQL Server キューを使用する即時更新します。|  
|**publisher_seqno**|**varbinary(16)**|このサブスクリプションに対するパブリッシャー側のトランザクションのシーケンス番号。|  
|**ss_cplt_seqno**|**varbinary(16)**|同時実行スナップショット処理の完了を示すために使用するシーケンス番号。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
