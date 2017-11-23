---
title: "sys.dm_database_copies (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9ea0a5834ae83cd49deec2731f6ce2c3f8ccacc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdatabasecopies-azure-sql-database"></a>sys.dm_database_copies (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベース コピーに関する情報を返します。  
  
Geo レプリケーション リンクに関する情報を返すを使用して、 [sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)または[sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)ビュー (SQL Database V12 で使用可能)。
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|`sys.databases` ビューの現在のデータベースの ID。|  
|**start_date**|**datetimeoffset**|地域の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データセンターにおいてデータベース コピーが開始された時刻 (UTC)。|  
|**modify_date**|**datetimeoffset**|地域の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データセンターにおいてデータベース コピーが完了した時刻 (UTC)。 新しいデータベースには、この時点でのプライマリ データベースのトランザクションが反映されます。 完了情報は、1 分間隔では更新されます。<br /><br />Percent_complete フィールドの最後の更新を反映した UTC 時刻です。|  
|**percent_complete**|**real**|コピーされたバイトの割合 (%)。 値の範囲は 0 ～ 100 です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] は、フェールオーバーなどのエラーから自動的に復旧した後に、データベース コピーを再開することがあります。 この場合、percent_complete は 0 から再開されます。|  
|**error_code**|**int**|値が 0 より大きい場合は、コピー中に発生したエラーを示すコード。 エラーが発生しなかった場合は 0 です。|  
|**error_desc**|**nvarchar (4096)**|コピー中に発生したエラーの説明。|  
|**error_severity**|**int**|データベース コピーが失敗した場合は 16 を返します。|  
|**error_state**|**int**|コピーが失敗した場合は 1 を返します。|  
|**copy_guid**|**uniqueidentifier**|コピー操作の一意の ID。|  
|**partner_server**|**sysname**|コピーが作成された SQL データベース サーバーの名前です。|  
|**partner_database**|**sysname**|パートナー サーバー上のデータベース コピーの名前です。|  
|**replication_state**|**tinyint**|このデータベースの連続コピー レプリケーションの状態。 値は次のとおりです。<br /><br /> 0 = 保留中です。 データベースのコピーの作成がスケジュールされているが、必要な準備手順がまだ完了していないまたはシード クォータによって一時的にブロックします。<br /><br /> 1 = シード処理中です。 シード処理されているデータベースのコピーはまだ完全に同期されませんとソース データベース。 この状態では、コピーに接続することはできません。 進行中のシード処理操作をキャンセルするには、データベースのコピーを削除する必要があります。|  
|**replication_state_desc**|**nvarchar (256)**|replication_state の説明。次のいずれかになります。<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|予約フィールドです。|  
|**is_continuous_copy**|**bit**|0 = 0 を返します|  
|**is_target_role**|**bit**|0 = ソース データベース<br /><br /> 1 = データベースのコピー|  
|**is_interlink_connected**|bit|予約フィールドです。|  
|**is_offline_secondary**|bit|予約フィールドです。|  
  
## <a name="permissions"></a>Permissions  
 このビューはのみで使用できます、**マスター**データベース、サーバー レベル プリンシパル ログインをします。  
  
## <a name="remarks"></a>解説  
 使用することができます、 **sys.dm_database_copies**で表示、**マスター**ソースまたはターゲットのデータベース[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー。 データベースのコピーが正常に完了して、新しいデータベースが内の行ではオンラインで、 **sys.dm_database_copies**ビューが自動的に削除されます。  
  
  
