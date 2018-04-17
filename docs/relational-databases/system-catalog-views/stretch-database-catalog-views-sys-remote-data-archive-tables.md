---
title: sys.remote_data_archive_tables (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_tables
- sys.remote_data_archive_tables_TSQL
- remote_data_archive_tables
- remote_data_archive_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_tables catalog view
ms.assetid: 765069b7-60fd-414c-875f-3455460b75cd
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29d6916024358efb9e806a5f8d1eeaf6a3715d89
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stretch-database-catalog-views---sysremotedataarchivetables"></a>データベースのカタログ ビューでの stretch sys.remote_data_archive_tables
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch が有効なローカル テーブルからデータを格納する各リモート テーブルの 1 つの行が含まれています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Stretch が有効なローカル テーブルのオブジェクトの ID。|  
|**remote_database_id**|**int**|自動生成されたローカルの識別子、リモート データベース。|  
|**remote_table_name**|**sysname**|Stretch が有効なローカル テーブルに対応するリモートのデータベース内のテーブルの名前です。|  
|**filter_predicate**|**nvarchar(max)**|フィルター述語では、存在する場合、移行するテーブル内の行を識別します。 値が null の場合、テーブル全体が移行の対象になります。<br /><br /> 詳細については、次を参照してください。[テーブルに対して Stretch Database を有効にする](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)と[フィルター述語を使用して、移行する行を選択](~/sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md)です。|  
|**migration_direction**|**tinyint**|データが移行されている方向です。 使用可能な値は次のです。<br/>1 (送信)<br/>2 (受信)|  
|**migration_direction_desc**|**nvarchar(60)**|データが移行されている方向の説明です。 使用可能な値は次のです。<br/>送信 (1)<br/>受信 (2)|  
|**is_migration_paused**|**bit**|移行が一時停止されているかどうかを示します。|  
|**is_reconciled**|**bit**| リモート SQL Server のテーブルと同期されているかどうかを示します。<br/><br/>ときに、値の**is_reconciled**が 1 (true)、リモート SQL Server のテーブルとの同期され、リモート データを含むクエリを実行することができます。<br/><br/>ときに、値の**is_reconciled**は 0 (false)、リモート SQL Server のテーブルと同期がとれていません。最近移行済みの行は、もう一度移行する必要があります。 これは、リモート Azure データベースを復元するとき、またはリモート テーブルから行を手動で削除するときに発生します。 テーブルを調整するまでは、リモート データを含むクエリを実行できません。 テーブルを調整するために実行[sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md)です。 |  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

