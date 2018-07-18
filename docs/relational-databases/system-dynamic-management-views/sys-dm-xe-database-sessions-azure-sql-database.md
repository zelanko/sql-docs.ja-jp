---
title: sys.dm_xe_database_sessions (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 33ea5179-16bb-4abd-96cc-9bc696e80987
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 28759d7101a8a798223a92b9201e0e9aa930a4fa
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984201"
---
# <a name="sysdmxedatabasesessions-azure-sql-database"></a>sys.dm_xe_database_sessions (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  セッション イベントに関する情報を返します。 イベントは、個別の実行ポイントです。 イベントに述語を適用すると、必要な情報がイベントに含まれていない場合にイベントの実行を中止できます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|イベント セッションのメモリ アドレス。 NULL 値は許可されません。|  
|event_name|**nvarchar(60)**|アクションがバインドされているイベントの名前。 NULL 値は許可されません。|  
|event_package_guid|**uniqueidentifier**|イベントを含むパッケージの GUID。 NULL 値は許可されません。|  
|event_predicate|**nvarchar(2048)**|イベントに適用される述語ツリーの XML 表現。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
2015-07-13 の時点では、'sys.dm_xe_objects' は、名前には ' (' _d) が含まれていないこれらの Xevent Dmv の 1 つです。 入力ミスまたはエラーでは、次の表の右側の列ではありません。 名前は、Microsoft SQL Server と Azure SQL データベースで同じです。 GeneMi です。  
  
|関連元|変換先|リレーションシップ|  
|--------|------|----------------|  
|sys.dm_xe_database_session_events.event_session_address|sys.dm_xe_database_sessions.address|多対一|  
|sys.dm_xe_database_session_events.event_package_guid, sys.dm_xe_database_session_events.event_name|sys.dm_xe_objects.name、sys.dm_xe_objects.package_guid|多対一|  
  
## <a name="see-also"></a>参照  
[Azure SQL Database の拡張イベント](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)  
[拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
 
