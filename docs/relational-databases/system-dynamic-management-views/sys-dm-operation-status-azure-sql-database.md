---
title: dm_operation_status (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 06/05/2017
ms.service: sql-database
ms.reviewer: ''
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
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c49e4e01dd8ddaf0667546a8cc221a7918f42c81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "70911203"
---
# <a name="sysdm_operation_status-azure-sql-database"></a>sys.dm_operation_status (Azure SQL データベース)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  
  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバーのデータベースに対して実行される操作に関する情報を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|session_activity_id|**UNIQUEIDENTIFIER**|操作の ID。 NULL 以外。|  
|resource_type|**int**|操作が実行されるリソースの種類を表します。 NULL 以外。 現在のリリースでは、このビューは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のみで実行される操作を追跡し、対応する整数値は 0 です。|  
|resource_type_desc|**nvarchar (2048)**|操作が実行される対象のリソースの種類の説明。 現在のリリースでは、このビューは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のみで実行される操作を追跡します。|  
|major_resource_id|**sql_variant**|操作が実行される対象の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の名前。 NULL 以外。|  
|minor_resource_id|**sql_variant**|内部使用専用です。 NULL 以外。|  
|operation|**nvarchar (60)**|CREATE や ALTER など[!INCLUDE[ssSDS](../../includes/sssds-md.md)]、に対して実行される操作。|  
|state|**tinyint**|操作の状態。<br /><br /> 0 = 保留<br />1 = 実行中<br />2 = 完了<br />3 = 失敗<br />4 = 取り消し|  
|state_desc|**nvarchar (120)**|PENDING = 操作はリソースまたはクォータが利用可能になるのを待機しています。<br /><br /> IN_PROGRESS = 操作が開始され、進行中です。<br /><br /> COMPLETED = 操作が正常に完了しました。<br /><br /> FAILED = 操作が失敗しました。 詳細については、 **error_desc**列を参照してください。<br /><br /> CANCELLED = ユーザーの要求によって操作が停止しました。|  
|percent_complete|**int**|操作が完了した割合 (%)。 値が連続しておらず、有効な値が以下に一覧表示されます。 Not NULL。<br/><br/>0 = 操作は開始されていません<br/>50 = 操作が進行中です<br/>100 = 操作の完了|  
|error_code|**int**|失敗した操作中に発生したエラーを示すコード。 値が 0 の場合、操作が正常に完了したことを示します。|  
|error_desc|**nvarchar (2048)**|失敗した操作中に発生したエラーの説明です。|  
|error_severity|**int**|失敗した操作中に発生したエラーの重大度レベルです。 エラーの重大度の詳細については、「[データベースエンジンエラーの重大度](https://go.microsoft.com/fwlink/?LinkId=251052)」を参照してください。|  
|error_state|**int**|将来使用するために予約されています。 将来の互換性は保証されません。|  
|start_time|**DATETIME**|操作が開始されたタイムスタンプ。|  
|last_modify_time|**DATETIME**|実行に時間のかかる操作において、レコードが最後に更新されたときのタイムスタンプです。 操作が正常に完了した場合、このフィールドには操作が完了したときのタイムスタンプが表示されます。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、サーバーレベルプリンシパルログインの**master**データベースでのみ使用できます。  
  
## <a name="remarks"></a>解説  
 このビューを使用するには、 **master**データベースに接続している必要があります。 サーバーの`sys.dm_operation_status` **master**データベースのビューを使用して、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に対して実行される次の操作の状態を追跡します。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
-   データベースの作成  
  
-   データベースをコピーします。 データベースコピーでは、ソースサーバーと対象サーバーの両方でこのビューにレコードが作成されます。  
  
-   データベースを変更する  
  
-   サービス層のパフォーマンス レベルの変更  
  
-   Basic から Standard への変更など、データベースのサービス階層を変更します。  
  
-   地理的レプリケーション リレーションシップの設定  
  
-   Geo レプリケーションリレーションシップの終了  
  
-   ダイアログ ボックスの  
  
-   データベースの削除  
  
## <a name="example"></a>例  
 データベース ' mydb ' に関連付けられている最新の geo レプリケーション操作を表示します。  
  
```  
SELECT * FROM sys.dm_operation_status   
   WHERE major_resource_id = 'myddb'   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>参照  
 [Geo レプリケーションの動的管理ビューおよび関数 &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [dm_geo_replication_link_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [geo_replication_links &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
