---
title: dm_database_copies (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- dm_database_copies_TSQL
- sys.dm_database_copies
- dm_database_copies
- sys.dm_database_copies_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_database_copies
- sys.dm_database_copies
ms.assetid: d03d4657-86d1-4496-97e6-cc3bc292e0b1
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f63469fb4955895b1eb1e3e8466dfbce6306e502
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824631"
---
# <a name="sysdm_database_copies-azure-sql-database"></a>sys.dm_database_copies (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベースのコピーに関する情報を返します。  
  
Geo レプリケーションリンクに関する情報を取得するには、 [geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)または[dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)ビュー (SQL Database V12 で利用可能) を使用します。
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|`sys.databases` ビューの現在のデータベースの ID。|  
|**start_date**|**datetimeoffset**|地域の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データセンターにおいてデータベース コピーが開始された時刻 (UTC)。|  
|**modify_date**|**datetimeoffset**|地域の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データセンターにおいてデータベース コピーが完了した時刻 (UTC)。 この時点で、新しいデータベースはプライマリデータベースとトランザクション上の一貫性があります。 完了情報は1分ごとに更新されます。<br /><br />Percent_complete フィールドの最終更新を反映した UTC 時間。|  
|**percent_complete**|**real**|コピーされたバイトの割合 (%)。 値の範囲は 0 ～ 100 です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] は、フェールオーバーなどのエラーから自動的に復旧した後に、データベース コピーを再開することがあります。 この場合、percent_complete は0から再起動されます。|  
|**error_code**|**int**|値が 0 より大きい場合は、コピー中に発生したエラーを示すコード。 値 0 は、エラーが発生しなかったことを示します。|  
|**error_desc**|**nvarchar (4,096)**|コピー中に発生したエラーの説明です。|  
|**error_severity**|**int**|データベース コピーが失敗した場合は 16 を返します。|  
|**error_state**|**int**|コピーが失敗した場合は 1 を返します。|  
|**copy_guid**|**uniqueidentifier**|コピー操作の一意の ID。|  
|**partner_server**|**sysname**|コピーが作成される SQL Database サーバーの名前。|  
|**partner_database**|**sysname**|パートナーサーバー上のデータベースコピーの名前。|  
|**replication_state**|**tinyint**|このデータベースの連続コピーレプリケーションの状態。 値は次のとおりです。<br /><br /> 0 = 保留中。 データベースコピーの作成がスケジュールされていますが、必要な準備手順がまだ完了していないか、シード処理クォータによって一時的にブロックされています。<br /><br /> 1 = シード処理。 シードされているコピーデータベースは、まだソースデータベースと完全に同期されていません。 この状態では、コピーに接続することはできません。 進行中のシード処理操作を取り消すには、コピーデータベースを削除する必要があります。|  
|**replication_state_desc**|**nvarchar(256)**|Replication_state の説明。次のいずれかになります。<br /><br /> PENDING<br /><br /> SEEDING<br />|  
|**maximum_lag**|**int**|予約済みのフィールド。|  
|**is_continuous_copy**|**bit**|0 = 0 を返します。|  
|**is_target_role**|**bit**|0 = ソースデータベース<br /><br /> 1 = データベースのコピー|  
|**is_interlink_connected**|bit|予約済みのフィールド。|  
|**is_offline_secondary**|bit|予約済みのフィールド。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、サーバーレベルプリンシパルログインの**master**データベースでのみ使用できます。  
  
## <a name="remarks"></a>解説  
 ソースサーバーまたはターゲットサーバーの**master**データベースでは、 **sys. dm_database_copies**ビューを使用でき [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ます。 データベースのコピーが正常に完了し、新しいデータベースがオンラインになると、 **dm_database_copies**ビューの行が自動的に削除されます。  
  
  
