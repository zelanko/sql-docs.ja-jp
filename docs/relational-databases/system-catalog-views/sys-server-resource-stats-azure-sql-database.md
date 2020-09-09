---
description: server_resource_stats (Azure SQL Database)
title: server_resource_stats (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.service: sql-database
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: ed975dd768bc9d7979dd254fddec715ed07b3b2f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542508"
---
# <a name="sysserver_resource_stats-azure-sql-database"></a>server_resource_stats (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

Azure SQL Managed Instance の CPU 使用率、IO、およびストレージデータを返します。 データは、5 分間隔で収集と集計が実行されます。 15 秒ごとの報告につき 1 行作成されます。 返されるデータには、CPU 使用率、ストレージサイズ、IO 使用率、SKU が含まれます。 履歴データは約 14 日間保持されます。

**Server_resource_stats**ビューには、データベースが関連付けられている Azure SQL Managed Instance のバージョンによって異なる定義があります。 新しいサーバーバージョンにアップグレードするときに、これらの違いとアプリケーションで必要な変更を検討してください。
 
  
 次の表では、v12 サーバーで使用できる列について説明します。  
  
|[列]|データ型|説明|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime2**|15秒のレポート間隔の開始を示す UTC 時刻|  
|end_time|**datetime**|15秒のレポート間隔の終了を示す UTC 時刻|
|resource_type|Nvarchar(128)|メトリックが提供されるリソースの種類|
|resource_name|nvarchar(128)|リソースの名前。|
|sku|nvarchar(128)|インスタンスのサービス階層を Managed Instance します。 使用できる値を次に示します。 <br><ul><li>General Purpose</li></ul><ul><li>Business Critical</li></ul>|
|hardware_generation|nvarchar(128)|ハードウェア生成識別子: Gen 4 または Gen 5|
|virtual_core_count|INT|インスタンスあたりの仮想コア数 (パブリックプレビューの場合は8、16、24) を表します。|
|avg_cpu_percent|decimal (5, 2)|インスタンスによって使用される Managed Instance サービス階層の制限の割合での平均コンピューティング使用率。 この値は、インスタンス内のすべてのデータベースのすべてのリソースプールの CPU 時間の合計として計算され、指定された間隔でその層の使用可能な CPU 時間で除算されます。|
|reserved_storage_mb|bigint|インスタンスあたりの予約済みストレージ (顧客がマネージインスタンスに対して購入したストレージ領域の量)|
|storage_space_used_mb|decimal (18, 2)|マネージインスタンス内のすべてのデータベースファイルで使用されるストレージ (ユーザーデータベースとシステムデータベースの両方を含む)|
|io_request|bigint|間隔内の i/o 物理操作の合計数|
|io_bytes_read|bigint|間隔内に読み取られた物理バイトの数|
|io_bytes_written|bigint|間隔内に書き込まれた物理バイト数|

 
> [!TIP]  
>  これらの制限とサービスレベルの詳細については、 [サービス階層の Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tiers)に関するトピックを参照してください。  
    
## <a name="permissions"></a>アクセス許可  
 このビューは、 **master** データベースに接続する権限を持つすべてのユーザーロールで使用できます。  
  
## <a name="remarks"></a>解説  
 **Server_resource_stats**によって返されるデータは、実行しているサービス階層/パフォーマンスレベルで許容される最大限度に対する割合として表される、avg_cpu 以外のバイトまたはメガバイト (列名で示される) で使用される合計として表現されます。  
 
## <a name="examples"></a>例  
 次の例では、過去1週間のコンピューティング使用率の平均が80% 以上のすべてのデータベースを返します。  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT resource_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.server_resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY resource_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>参照  
 [Managed Instance サービスレベル](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tiers)
