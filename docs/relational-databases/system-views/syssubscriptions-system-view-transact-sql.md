---
title: syssubscriptions (システム ビュー) (Transact-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions view
ms.assetid: c9613858-9512-43a9-aa53-7ee8064f064c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a50ce1b42c8963aac0bc152e08c6d39eec73eb2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094786"
---
# <a name="syssubscriptions-system-view-transact-sql"></a>syssubscriptions (システム ビュー) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Syssubscriptions**ビューは、サブスクリプション情報を公開します。 このビューは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|サブスクライブされるアーティクルの一意な ID。|  
|**srvid**|**smallint**|サブスクライバーのサーバー ID。|  
|**dest_db**|**sysname**|サブスクリプション データベースの名前。|  
|**status**|**tinyint**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = サブスクライブします。<br /><br /> **2** = アクティブ。|  
|**sync_type**|**tinyint**|初期同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = none。|  
|**login_name**|**sysname**|サブスクリプションを追加するためパブリッシャーに接続するときのログイン名。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ、ディストリビューション エージェントがディストリビューターで実行されます。<br /><br /> **1** = プル サブスクライバーでディストリビューション エージェントの実行されます。|  
|**distribution_jobid**|**binary(16)**|サブスクリプションの同期で使用されるディストリビューション エージェント ジョブの識別子。|  
|**timestmap**|**timestamp**|サブスクリプションを作成した日付と時刻。|  
|**update_mode**|**tinyint**|更新モード。<br /><br /> **0** = 読み取り専用です。<br /><br /> **1** = 即時更新します。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 戻す。<br /><br /> **1** = は送信しません。|  
|**queued_reinit**|**bit**|アーティクルが初期化または再初期化の対象としてマークされているかどうかを指定します。 値**1**サブスクライブされるアーティクルが初期化または再初期化のマークされているを指定します。|  
|**nosync_type**|**tinyint**|サブスクリプションの初期化の種類。<br /><br /> **0** = 自動 (スナップショット)<br /><br /> **1**レプリケーションのサポートのみを =<br /><br /> **2**バックアップによる初期化を =<br /><br /> **3** = ログ シーケンス番号 (LSN) からの初期化<br /><br /> 詳細については、次を参照してください。、 **@sync_type** パラメーターの[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。<br /><br /> **3** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|サブスクライバーの名前。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [syssubscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/syssubscriptions-transact-sql.md)  
  
  
