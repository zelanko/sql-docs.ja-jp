---
title: IHsubscriptions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsubscriptions_TSQL
- IHsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- IHsubscriptions system table
ms.assetid: 9ec21119-35f1-4e39-abaa-b2c790c485b1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b677e0f6c9be058650a46aee3465811b8f3eecc7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990147"
---
# <a name="ihsubscriptions-transact-sql"></a>IHsubscriptions (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHsubscriptions**システムテーブルには、現在のディストリビューターを使用して SQL Server 以外のパブリッシャーからのパブリケーションへのサブスクリプションごとに1行の値が格納されます。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|パブリッシュされたアーティクルを一意に識別します。|  
|**srvid**|**smallint**|サブスクライバーのサーバー ID。|  
|**dest_db**|**sysname**|転送先データベースの名前|  
|**login_name**|**sysname**|サブスクリプションを追加するときに使用されるログイン名です。|  
|**distribution_jobid**|**バイナリ (16)**|ディストリビューション エージェントのジョブ ID です。|  
|**timestamp**|**timestamp**|サブスクリプションを作成した日付と時刻。|  
|**queued_reinit**|**bit**|アーティクルに初期化または再初期化のマークを付けるかどうかを指定します。 値**1**は、サブスクライブされたアーティクルが初期化または再初期化のマークが付けられることを示します。|  
|**オンライン**|**tinyint**|サブスクリプションの状態。<br /><br /> **0** = 非アクティブ。<br /><br /> **1** = サブスクライブ済み。<br /><br /> **2** = アクティブ。|  
|**sync_type**|**tinyint**|初期同期の種類。<br /><br /> **1** = 自動。<br /><br /> **2** = なし。|  
|**subscription_type**|**int**|サブスクリプションの種類。<br /><br /> **0** = プッシュ-ディストリビューションエージェントはサブスクライバーで実行されます。<br /><br /> **1** = プル-ディストリビューションエージェントはディストリビューターで実行されます。|  
|**update_mode**|**tinyint**|更新モード:<br /><br /> **0** = 読み取り専用。<br /><br /> **1** = 即時更新。|  
|**loopback_detection**|**bit**|双方向トランザクションレプリケーショントポロジの一部であるサブスクリプションに適用されます。 ディストリビューション エージェントが、サブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを示します。<br /><br /> **0** = 返送します。<br /><br /> **1** = を返しません。|  
  
## <a name="see-also"></a>参照  
 [異種データベースレプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addsubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
