---
title: "syssubscriptions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- syssubscriptions_TSQL
- syssubscriptions
dev_langs: TSQL
helpviewer_keywords: syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c581c037ed78a82a194f74faae709bd81d6bd41c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内のサブスクリプションごとに 1 行のデータを格納します。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID。|  
|**srvid**|**smallint**|サブスクライバーのサーバー ID。|  
|**dest_db 指定してください。**|**sysname**|転送先データベースの名前。|  
|**ステータス**|**tinyint**|サブスクリプションの状態です。<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = サブスクライブします。<br /><br /> **2**アクティブを = です。|  
|**sync_type**|**tinyint**|初期同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = なし|  
|**login_name**|**sysname**|サブスクリプションを追加するときに使用するログイン名です。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> 0 = プッシュ。ディストリビューション エージェントはディストリビューター側で実行されます。<br /><br /> 1 = プル。ディストリビューション エージェントはサブスクライバー側で実行されます。|  
|**distribution_jobid**|**binary (16)**|ディストリビューション エージェントのジョブ ID。|  
|**timestamp**|**timestamp**|タイムスタンプ。|  
|**update_mode**|**tinyint**|更新モード。<br /><br /> **0** = 読み取り専用です。<br /><br /> **1** = 即時更新します。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 戻す。<br /><br /> **1** = は送信しません。|  
|**queued_reinit**|**bit**|アーティクルが初期化または再初期化の対象としてマークされているかどうかを指定します。 値**1**サブスクライブされるアーティクルが初期化または再初期化のマークされていることを指定します。|  
|**nosync_type**|**tinyint**|サブスクリプションの初期化の種類。<br /><br /> **0**自動 (スナップショット) を =<br /><br /> **1**レプリケーションのサポートのみを =<br /><br /> **2**バックアップによる初期化を =<br /><br /> **3**ログ シーケンス番号 (LSN) からの初期化を =<br /><br /> 詳細については、次を参照してください。、  **@sync_type** のパラメーター [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)です。|  
|**済み**|**sysname**|サブスクライバーの名前。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
