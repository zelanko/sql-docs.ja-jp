---
description: sys.dm_xe_database_sessions (Azure SQL Database)
title: dm_xe_database_sessions (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d49c252a60cdf08c7ac55c287333de9805d5ff26
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88322718"
---
# <a name="sysdm_xe_database_sessions-azure-sql-database"></a>sys.dm_xe_database_sessions (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  セッション イベントに関する情報を返します。 イベントは、個別の実行ポイントです。 イベントに述語を適用すると、イベントに必要な情報が含まれていない場合に、イベントの発生を防ぐことができます。  
  
||  
|-|  
|**に適用さ**れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 NULL 値は許可されません。|  
|event_name|**nvarchar(60)**|アクションが関連付けられているイベントの名前。 NULL 値は許可されません。|  
|event_package_guid|**uniqueidentifier**|イベントを含むパッケージの GUID。 NULL 値は許可されません。|  
|event_predicate|**nvarchar(2048)**|イベントに適用される述語ツリーの XML 表現。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
2015-07-13 のように、' Xevent ' は dm_xe_objects、名前に ' _database ' が含まれていないこれらの Dmv の1つです。 次の表の右側の列では、タイプミスやエラーではありません。 名前は Microsoft SQL Server と Azure SQL Database で同じです。  
  
|ソース|終了|リレーションシップ|  
|--------|------|----------------|  
|dm_xe_database_session_events。 event_session_address|dm_xe_database_sessions. アドレス|多対一|  
|sys. dm_xe_database_session_events. event_package_guid、dm_xe_database_session_events event_name|sys.dm_xe_objects.name、sys.dm_xe_objects.package_guid|多対一|  
  
## <a name="see-also"></a>参照  
[Azure SQL データベースでの拡張イベント](https://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
 
