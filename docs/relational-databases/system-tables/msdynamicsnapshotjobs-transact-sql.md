---
title: MSdynamicsnapshotjobs (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f717d5cf35349dcb99ec2022c5c0c92df5ea4286
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812808"
---
# <a name="msdynamicsnapshotjobs-transact-sql"></a>MSdynamicsnapshotjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Msdynamicsnapshotjobs**テーブルは、フィルター処理されたデータスナップショットを生成するために適用されるパラメーター化された行フィルター情報を追跡します。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**ID**|**int**|フィルター選択されたデータスナップショットジョブの ID です。|  
|**name**|**sysname**|フィルター選択されたデータスナップショットジョブの名前。|  
|**pubid**|**uniqueidentifier**|このパブリケーションの一意な識別番号です。|  
|**job_id**|**uniqueidentifier**|ディストリビューター側の SQL Server エージェントジョブの ID。|  
|**agent_id**|**int**|SQL Server エージェントの ID です。|  
|**dynamic_filter_login**|**sysname**|パブリケーションに対して定義されたパラメーター化された行フィルター内の[SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)関数を評価するために使用される値です。|  
|**dynamic_filter_hostname**|**sysname**|パブリケーションに対して定義されたパラメーター化された行フィルター内の[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)関数を評価するために使用される値です。|  
|**dynamic_snapshot_location**|**nvarchar(255)**|フィルター選択されたデータスナップショットが使用されている場合に、スナップショットファイルの読み取り元フォルダーへのパス。|  
|**partition_id**|**int**|ジョブが属しているデータパーティションの ID。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
