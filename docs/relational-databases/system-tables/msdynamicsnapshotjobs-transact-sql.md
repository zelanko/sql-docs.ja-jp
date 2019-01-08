---
title: MSdynamicsnapshotjobs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotjobs_TSQL
- MSdynamicsnapshotjobs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotjobs system table
ms.assetid: 4f36a325-0e3c-46c4-aeeb-416346cce0bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8b7934d914af50d61df554c2a82ae221a1d5490f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817284"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdynamicsnapshotjobs**テーブルは、フィルター選択されたデータ スナップショットの生成に適用されるパラメーター化された行フィルターの情報を追跡します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|フィルター選択されたデータ スナップショット ジョブの ID です。|  
|**name**|**sysname**|フィルター選択されたデータ スナップショット ジョブの名前です。|  
|**pubid**|**uniqueidentifier**|このパブリケーションの一意な識別番号です。|  
|**job_id**|**uniqueidentifier**|ディストリビューターで SQL Server エージェント ジョブの ID。|  
|**agent_id**|**int**|SQL Server エージェントの ID。|  
|**dynamic_filter_login**|**sysname**|評価するために使用される値、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)パブリケーションに対して定義されているパラメーター化された行フィルター内の関数。|  
|**dynamic_filter_hostname**|**sysname**|評価するために使用される値、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)パブリケーションに対して定義されているパラメーター化された行フィルター内の関数。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|フィルター選択されたデータ スナップショットが使用される場合、スナップショット ファイルの読み取り元であるフォルダーへのパスです。|  
|**partition_id**|**int**|ジョブが組み込まれているデータ パーティションの ID です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
