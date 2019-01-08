---
title: MSsubscriptions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriptions_TSQL
- MSsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriptions system table
ms.assetid: b7e8301d-d115-41f6-8d4f-e0d25f453b25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b0c5d53519b09c9f30ccdf7e973e25e5a06a6a3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823596"
---
# <a name="mssubscriptions-transact-sql"></a>MSsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriptions**ローカル ディストリビューターによって処理されるサブスクリプションでアーティクルをパブリッシュされた各テーブルに 1 つの行が含まれます。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher_database_id**|**int**|パブリッシャー データベースの ID。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**article_id**|**int**|アーティクルの ID。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> **0** = プッシュ。<br /><br /> **1** = プルします。<br /><br /> **2** = 匿名です。|  
|**sync_type**|**tinyint**|同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = 同期なし。|  
|**status**|**tinyint**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = サブスクライブします。<br /><br /> **2** = アクティブ。|  
|**subscription_seqno**|**varbinary(16)**|スナップショット トランザクション シーケンス番号。|  
|**snapshot_seqno_flag**|**bit**|値が、スナップショット トランザクションのシーケンス番号のソースを示す**1**つまり**subscription_seqno**スナップショット シーケンス番号します。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**subscription_time**|**datetime**|内部使用のみです。|  
|**loopback_detection**|**bit**|双方向トランザクション レプリケーション トポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **1** = は送信しません。<br /><br /> **0** = 戻す。<br /><br /> 注:この列は、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] の双方向レプリケーション機能との互換性のために用意されています。 それ以降のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ピア ツー ピア レプリケーションを代わりに使用してください。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
|**agent_id**|**int**|エージェントの ID。|  
|**update_mode**|**tinyint**|更新の種類。|  
|**publisher_seqno**|**varbinary(16)**|このサブスクリプションに対するパブリッシャー側のトランザクションのシーケンス番号。|  
|**ss_cplt_seqno**|**varbinary(16)**|同時実行スナップショット処理の完了を示すために使用するシーケンス番号。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
