---
title: sys.dm_xe_database_session_events (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 9e985a19-f93f-4c56-b644-12c529298011
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 3177cd3e49c902743c7ff9f6b22f0b195faf2f8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmxedatabasesessionevents-azure-sql-database"></a>sys.dm_xe_database_session_events (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  セッション イベントに関する情報を返します。 イベントは、個別の実行ポイントです。 イベントに述語を適用すると、必要な情報がイベントに含まれていない場合にイベントの実行を中止できます。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|イベント セッションのメモリ アドレス。 NULL 値は許可されません。|  
|event_name|**nvarchar(60)**|アクションがバインドされているイベントの名前。 NULL 値は許可されません。|  
|event_package_guid|**uniqueidentifier**|イベントを含むパッケージの GUID。 NULL 値は許可されません。|  
|event_predicate|**nvarchar(2048)**|イベントに適用される述語ツリーの XML 表現。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 VIEW DATABASE STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|多対一|  
|sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name、sys.dm_xe_objects.package_guid|多対一|  
  
  
