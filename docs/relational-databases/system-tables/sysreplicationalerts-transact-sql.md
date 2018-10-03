---
title: sysreplicationalerts (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1932ad1a889d32cd3bef1c26916e79960370b52f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783370"
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション警告の発生を引き起こした状態についての情報を保持します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|警告の ID です。|  
|**status**|**int**|ユーザー定義の値です。<br /><br /> **0** = 非対処します。<br /><br /> **1** = サービスを提供します。|  
|**agent_type**|**int**|エージェントのタイプです。<br /><br /> **1** = スナップショット エージェント。<br /><br /> **2** = ログ リーダー エージェント。<br /><br /> **3** = ディストリビューション エージェント。<br /><br /> **4**マージ エージェントを = です。|  
|**agent_id**|**int**|テーブルからエージェント ID **MSsnapshot_agents**、 **MSlogreader_agents**、 **MSdistribution_agents**、または**MSmerge_agents**します。|  
|**error_id**|**int**|格納されているエラーの ID **MSrepl_errors**します。|  
|**alert_error_code**|**int**|このレコードの記録中に発生した警告のメッセージ ID です。|  
|**time**|**datetime**|そのレコードが挿入された時刻です。|  
|**パブリッシャー**|**sysname**|この警告を発生したエージェントに関係するパブリッシャー名です。|  
|**publisher_db**|**sysname**|この警告を発生したエージェントに関係するパブリッシャー データベースです。|  
|**パブリケーション**|**sysname**|この警告を発生したエージェントに関係するパブリケーションです。|  
|**publication_type**|**int**|パブリケーションの種類。<br /><br /> **0** = スナップショット。<br /><br /> **1** = トランザクション。<br /><br /> **2** = マージします。|  
|**サブスクライバー**|**sysname**|この警告を発生したエージェントに関係するサブスクライバー名です。|  
|**@subscriber_db**|**sysname**|この警告を発生したエージェントに関係するサブスクライバー データベース名です。|  
|**article**|**sysname**|この警告を発生したエージェントに関係するアーティクル名です。|  
|**destination_object**|**sysname**|警告に関係するサブスクリプション テーブル名です。|  
|**source_object**|**sysname**|警告に関係するパブリッシュされたテーブル名です。|  
|**alert_error_text**|**ntext**|警告のテキストです。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
