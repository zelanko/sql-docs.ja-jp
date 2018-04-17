---
title: MSsubscriptions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65eec6696b85d904d61767c486d6ab42ba68a1ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriptions**テーブルがパブリッシュされたアーティクルごとに、ローカル ディストリビューターによって処理されるサブスクリプションの 1 つの行を保持します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|パブリッシャー データベースの ID。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**article_id**|**int**|アーティクルの ID。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ。<br /><br /> **1**プルを = です。<br /><br /> **2** = 匿名です。|  
|**sync_type**|**tinyint**|同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = 同期なし。|  
|**ステータス**|**tinyint**|サブスクリプションの状態です。<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = サブスクライブします。<br /><br /> **2**アクティブを = です。|  
|**subscription_seqno**|**varbinary(16)**|スナップショット トランザクション シーケンス番号。|  
|**snapshot_seqno_flag**|**bit**|値が、スナップショット トランザクション シーケンス番号のソースを示す**1**ことを意味**subscription_seqno**スナップショット シーケンス番号です。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**subscription_time**|**datetime**|内部使用のみです。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **1** = は送信しません。<br /><br /> **0** = 戻す。<br /><br /> 注: この列はサポートされてのみでの双方向レプリケーション機能との下位互換性[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]です。 以降のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ピア ツー ピア レプリケーションを使用してください。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
|**agent_id**|**int**|エージェントの ID。|  
|**update_mode**|**tinyint**|更新の種類。|  
|**publisher_seqno**|**varbinary(16)**|このサブスクリプションに対するパブリッシャー側のトランザクションのシーケンス番号。|  
|**ss_cplt_seqno**|**varbinary(16)**|同時実行スナップショット処理の完了を示すために使用するシーケンス番号。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
