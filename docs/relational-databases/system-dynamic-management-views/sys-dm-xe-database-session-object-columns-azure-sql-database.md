---
title: sys.dm_xe_database_session_object_columns
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: 8d58dfe13c3bb68290bcd0b968c14a8eab27ab40
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85675870"
---
# <a name="sysdm_xe_database_session_object_columns-azure-sql-database"></a>sys.dm_xe_database_session_object_columns (Azure SQL Database)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  セッションにバインドされたオブジェクトの構成値を示します。  
  
||  
|-|  
|**に適用さ**れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 には、dm_xe_database_sessions との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|column_name|**nvarchar(60)**|構成値の名前。 NULL 値は許可されません。|  
|column_id|**int**|列の ID。 は、オブジェクト内で一意です。 NULL 値は許可されません。|  
|column_value|**nvarchar(2048)**|列の構成値。 NULL 値が許可されます。|  
|object_type|**nvarchar(60)**|オブジェクトの古い型。  Null 値はありません。 object_type は次のいずれかです。<br /><br /> イベント<br /><br /> ターゲット (target)|  
|object_name|**nvarchar(60)**|この列が所属するオブジェクトの名前。 NULL 値は許可されません。|  
|object_package_guid|**uniqueidentifier**|オブジェクトを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|From|終了|リレーションシップ|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns。 object_name<br /><br /> dm_xe_database_session_object_columns。 object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|多対一|  
|dm_xe_database_session_object_columns。 column_name<br /><br /> dm_xe_database_session_object_columns。 column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|多対一|  
  
## <a name="see-also"></a>関連項目  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
