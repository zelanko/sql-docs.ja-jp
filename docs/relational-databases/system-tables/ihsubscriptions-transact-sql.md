---
title: "IHsubscriptions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- IHsubscriptions_TSQL
- IHsubscriptions
dev_langs: TSQL
helpviewer_keywords: IHsubscriptions system table
ms.assetid: 9ec21119-35f1-4e39-abaa-b2c790c485b1
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9487ac5859c0bd35cbcbfc326f6a175fc480f17d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihsubscriptions-transact-sql"></a>IHsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsubscriptions**システム テーブルを含むサブスクリプションごとに 1 つの行、パブリケーションに対するから、SQL Server 以外のパブリッシャー、現在のディストリビューターを使用しています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**コ**|**int**|パブリッシュされたアーティクルを一意に識別します。|  
|**srvid**|**smallint**|サブスクライバーのサーバー ID。|  
|**dest_db 指定してください。**|**sysname**|対象データベースの名前です。|  
|**login_name**|**sysname**|サブスクリプションを追加するときに使用するログイン名です。|  
|**distribution_jobid**|**binary (16)**|ディストリビューション エージェントのジョブ ID です。|  
|**timestamp**|**timestamp**|サブスクリプションを作成した日付と時刻。|  
|**queued_reinit**|**bit**|アーティクルが初期化または再初期化の対象としてマークされているかどうかを指定します。 値**1**サブスクライブされるアーティクルが初期化または再初期化のマークされていることを指定します。|  
|**ステータス**|**tinyint**|サブスクリプションの状態です。<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = サブスクライブします。<br /><br /> **2**アクティブを = です。|  
|**sync_type**|**tinyint**|初期同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = none です。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ、ディストリビューション エージェントに、サブスクライバーで実行されます。<br /><br /> **1** = プル、ディストリビューション エージェントがディストリビューターで実行されます。|  
|**update_mode**|**tinyint**|更新モード。<br /><br /> **0** = 読み取り専用です。<br /><br /> **1** = 即時更新します。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 戻す。<br /><br /> **1** = は送信しません。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
