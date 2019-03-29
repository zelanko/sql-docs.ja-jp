---
title: sys.dm_user_db_resource_governance (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governance
- sys.resource_governance_TSQL
- resource_governance
- resource_governance_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governance catalog view
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: bb4c43fa4193d9254d7f06f24bd903f974739e87
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567638"
---
# <a name="sysdmuserdbresourcegovernance-transact-sql"></a>sys.dm_user_db_resource_governance (TRANSACT-SQL)

[!INCLUDE[appliesto-xx-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

リソース ガバナンスの Azure SQL Database データベースの構成と容量の設定を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**database_id**|ssNoversion|データベース、Azure SQL Database サーバー内で一意の ID。|
|**logical_database_guid**|UNIQUEIDENTIFIER|ユーザー データベースとユーザー データベースの有効期間にわたって維持の論理の guid です。  名前を変更またはを別のデータベースの設定 SLO は変更されません、GUID。 |
|**physical_database_guid**|UNIQUEIDENTIFIER|物理の guid はユーザー データベースがユーザー データベースの物理インスタンスの有効期間にわたって維持されます。 さまざまな SLO に設定を変更するには、この列になります。|
|**server_name**|NVARCHAR|論理サーバーの名前。|
|**database_name**|NVARCHAR|論理データベース名。|
|**slo_name**|NVARCHAR|サービス レベル目標とハードウェアの世代。|
|**dtu_limit**|ssNoversion|(仮想コアの場合は NULL) のデータベースの DTU の上限。|
|**cpu_limit**|ssNoversion|データベース (データベースの DTU の場合は NULL) の vCore の最大数。|
|**min_cpu**|TINYINT|ユーザーのワークロードで使用できる最小の CPU % です。|
|**max_cpu**|TINYINT|ユーザーのワークロードで使用できる最大 CPU % です。|
|**cap_cpu**|TINYINT|ユーザーのワークロード グループの CPU 使用率の上限です。|
|**min_cores**|SMALLINT|SQL で使用される Cpu の数。|
|**max_dop**|SMALLINT|ユーザーのワークロードで使用される並列処理の最大限度。|
|**min_memory**|ssNoversion|ユーザーのワークロードで使用できる最小メモリの割合。|
|**max_memory**|ssNoversion|ユーザーのワークロードで使用できる最大メモリの割合。|
|**max_sessions**|ssNoversion|ユーザー グループに対するセッションの制限。|
|**max_memory_grant**|ssNoversion|最大メモリは、% で、ユーザーのワークロードでは、各クエリに対して付与します。|
|**max_db_memory**|ssNoversion|ユーザーの DB ワークロードの最大バッファー プール メモリ上限|
|**govern_background_io**|bit|ユーザー グループに、バック グラウンド書き込みが課金されるかどうかを示します。|
|**min_db_max_size_in_mb**|BIGINT|データベースの最小最大ファイル サイズ (mb)。|
|**max_db_max_size_in_mb**|BIGINT|最大最大データベース ファイル (MB 単位)。|
|**default_db_max_size_in_mb**|BIGINT|既定の (mb) の最大データベース ファイル サイズ。|
|**db_file_growth_in_mb**|BIGINT|MB で、azure のデータベース ファイルの既定の増加。|
|**initial_db_file_size_in_mb**|BIGINT|既定のデータベース ファイル サイズを mb 単位で。|
|**log_size_in_mb**|BIGINT|既定のログ ファイル サイズ、(MB 単位)。|
|**instance_cap_cpu**|ssNoversion|インスタンス レベルでの CPU 上限です。|
|**instance_max_log_rate**|BIGINT|ログの世代 (1 秒あたりのバイト単位) のインスタンス レベルで率の上限。|
|**instance_max_worker_threads**|ssNoversion|インスタンス レベルでのワーカー スレッドの上限。|
|**replica_type**|ssNoversion|レプリカの種類、0 はプライマリ、および 1 が、セカンダリです。|
|**max_transaction_size**|BIGINT|最大ログの領域 (KB 単位) のすべてのトランザクションで使用します。|
|**checkpoint_rate_mbps**|ssNoversion|チェックポイント帯域幅 (mbps)。|
|**checkpoint_rate_io**|ssNoversion|IOs で 1 秒あたりの IO の速度がチェックポイントします。|
|**last_updated_date_utc**|DATETIME|最後の設定の変更または再構成の日時。|
|**primary_group_id**|ssNoversion|ワークロード グループのプライマリ ユーザーの id。|
|**primary_group_max_workers**|ssNoversion|プライマリ ユーザーのワークロード グループ レベルでのワーカーの上限。|
|**primary_min_log_rate**|BIGINT|プライマリ ユーザーのワークロード グループ レベルで最小のログの速度 (1 秒あたりのバイト単位)。|
|**primary_max_log_rate**|BIGINT|プライマリ ユーザーのワークロード グループ レベルでログの最大レート (1 秒あたりのバイト単位)。|
|**primary_group_min_io**|ssNoversion|プライマリ ユーザーのワークロード グループ レベルで最小 IO。|
|**primary_group_max_io**|ssNoversion|プライマリ ユーザーのワークロード グループ レベルで最大 IO。|
|**primary_group_min_cpu**|FLOAT|最小 CPU 使用率は、プライマリ ユーザーのワークロード グループ レベルで制限します。|
|**primary_group_max_cpu**|FLOAT|プライマリ ユーザーのワークロード グループ レベルで最大 CPU 使用率を制限します。|
|**primary_log_commit_fee**|ssNoversion|プライマリ ユーザーのワークロード グループ レベルでは、レート ガバナンスのコミット手数料ログ。|
|**primary_pool_max_workers**|ssNoversion|プライマリ ユーザー プール レベルでのワーカーの上限。
|**pool_max_io**|ssNoversion|プライマリ ユーザー プール レベルで最大 IO 制限。|
|**govern_db_memory_in_resource_pool**|bit|バッファー プールの最大サイズは、リソース プール レベルで適用されるかどうかを示しています。 通常、エラスティック プール内のデータベースを設定します。|
|**volume_local_iops**|ssNoversion|ローカル ボリューム (例: c:、d:) の 2 つ目の cap ごと IOs。|
|**volume_managed_xstore_iops**|ssNoversion|IOs リモート ストレージ アカウントの 2 つ目の cap ごと。|
|**volume_external_xstore_iops**|ssNoversion|Azure SQL DB のバックアップとテレメトリによって使用されるリモート ストレージ アカウントの 2 つ目の cap ごと IOs。|
|**volume_type_local_iops**|ssNoversion|IOs は、すべてのローカル ボリュームの 2 つ目の cap ごと。|
|**volume_type_managed_xstore_iops**|ssNoversion|IOs のインスタンスで使用されるすべてのリモート ストレージ アカウントの 2 つ目の cap ごと。|
|**volume_type_external_xstore_iops**|ssNoversion|IOs のインスタンスの Azure SQL DB のバックアップとテレメトリで使用されるすべてのリモート ストレージ アカウントの 2 つ目の cap ごと。|
|**volume_pfs_iops**|ssNoversion|IOs premium file storage 用の 2 つ目の cap ごと。|
|**volume_type_pfs_iops**|ssNoversion|インスタンスによって使用されるすべての premium file storage 用の 2 つ目の cap ごと IOs。|
|||

## <a name="permissions"></a>アクセス許可

このビューには、VIEW DATABASE STATE 権限が必要です。

## <a name="remarks"></a>コメント

ユーザーは、リソース ガバナンスの構成の場合は、この動的管理ビューと Azure SQL Database データベースの容量の設定にアクセスできます。 

> [!IMPORTANT]
> この DMV によって表示されるデータのほとんどは、社内従量課金プラン向けで、変更される可能性があります。

## <a name="examples"></a>使用例

次の例では、インスタンス最大ログ比率データを単一またはプールされたデータベースのデータベース サーバー内のデータベース名で順序付けを返します。

```
SELECT database_name,
       primary_max_log_rate
FROM sys.dm_user_db_resource_governance
ORDER BY database_name DESC;  
```

## <a name="see-also"></a>参照

- [トランザクション ログのレートのガバナンス](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [1 つのデータベースの DTU のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-single-databases)
- [1 つのデータベースの vCore のリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)
