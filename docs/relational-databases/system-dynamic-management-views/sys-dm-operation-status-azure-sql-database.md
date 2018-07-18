---
title: sys.dm_operation_status (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 06/05/2017
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_operation_status_TSQL
- dm_operation_status
- sys.dm_operation_status
- sys.dm_operation_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_operation_status dynamic management view
- sys.dm_operation_status dynamic management view
ms.assetid: cc847784-7f61-4c69-8b78-5f971bb24d61
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 6d1df62f4ac877ed82ba1d7b555f8fd9ef759362
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979454"
---
# <a name="sysdmoperationstatus-azure-sql-database"></a>sys.dm_operation_status (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバーのデータベースに対して実行される操作に関する情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|操作の ID。 NULL 以外です。|  
|resource_type|**int**|操作が実行される対象のリソースの種類を示します。 NULL 以外です。 このビューを現在のリリースで実行された操作を追跡します[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のみ、対応する整数値は 0。|  
|resource_type_desc|**nvarchar(2048)**|操作が実行される対象のリソースの種類の説明。 このビューを現在のリリースで実行された操作を追跡します[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のみです。|  
|major_resource_id|**sql_variant**|操作が実行される対象の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の名前。 Null 以外です。|  
|minor_resource_id|**sql_variant**|内部使用のみです。 NULL 以外です。|  
|operation|**nvarchar(60)**|に対して実行された操作、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、CREATE または ALTER などです。|  
|state|**tinyint**|操作の状態。<br /><br /> 0 = 保留<br />1 = 実行中<br />2 = 完了<br />3 = 失敗<br />4 = 取り消し|  
|state_desc|**nvarchar(120)**|PENDING = 操作はリソースまたはクォータが利用可能になるのを待機しています。<br /><br /> IN_PROGRESS = 操作は開始され、実行中です。<br /><br /> COMPLETED = 操作が正常に完了しました。<br /><br /> FAILED = 操作が失敗しました。 参照してください、 **error_desc**詳細列。<br /><br /> CANCELLED = ユーザーの要求によって操作が停止しました。|  
|percent_complete|**int**|操作が完了した割合 (%)。 値は連続していないと、有効な値を以下に示します。 NULL 以外です。<br/><br/>0 = 操作が開始されていません<br/>50 = 実行中の操作<br/>100 = 操作が完了しました|  
|error_code|**int**|失敗した操作中に発生したエラーを示すコード。 値が 0 の場合は、操作が正常に完了したことを示します。|  
|error_desc|**nvarchar(2048)**|失敗した操作中に発生したエラーの説明。|  
|error_severity|**int**|失敗した操作中に発生したエラーの重大度レベル。 エラーの重大度に関する詳細については、次を参照してください。[データベース エンジン エラーの重大度](http://go.microsoft.com/fwlink/?LinkId=251052)します。|  
|error_state|**int**|将来使用するために予約されています。 将来の互換性は保証されません。|  
|start_time|**datetime**|操作が開始した時点のタイムスタンプ。|  
|last_modify_time|**datetime**|実行時間の長い操作のレコードが最後に変更された時点のタイムスタンプ。 操作が正常に完了した場合、このフィールドには操作が完了した時点のタイムスタンプが表示されます。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューはのみ利用可能、**マスター**データベース、サーバー レベル プリンシパル ログインをします。  
  
## <a name="remarks"></a>コメント  
 このビューを使用するに接続する必要があります、**マスター**データベース。 使用して、`sys.dm_operation_status`で表示、**マスター**のデータベース、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバーに対して実行される次の操作の状態を追跡するために、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]:  
  
-   データベースを作成します。  
  
-   データベースをコピーします。 データベースのコピーによって、ソース サーバーおよび対象サーバーの両方にあるこのビューに、レコードが作成されます。  
  
-   データベースの変更  
  
-   サービス層のパフォーマンス レベルの変更  
  
-   データベースのサービス層を変更します (Basic から Standard への変更など)。  
  
-   地理的レプリケーション リレーションシップの設定  
  
-   地理的レプリケーション リレーションシップの終了  
  
-   [データベースの復元]  
  
-   データベースの削除  
  
## <a name="example"></a>例  
 データベース 'mydb' に関連付けられた最新の地理的レプリケーション操作を表示します。  
  
```  
SELECT * FROM sys.dm_ operation_status   
   WHERE major_resource_id = ‘myddb’   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>参照  
 [地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.geo_replication_links &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
