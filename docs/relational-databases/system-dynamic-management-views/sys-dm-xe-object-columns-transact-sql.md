---
title: sys.dm_xe_object_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24b7123f557674afe6016138f05803a8d13753c6
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのオブジェクトのスキーマ情報を返します。  
  
> [!NOTE]  
>  イベント オブジェクトは、読み取り専用データと読み取り/書き込みデータの両方の固定スキーマを公開します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|列の名前です。 名前では、オブジェクト内で一意です。 NULL 値は許可されません。|  
|column_id|**int**|列の識別子。 column_id は、column_type と共に使用すると、オブジェクト内で一意です。 NULL 値は許可されません。|  
|object_name|**nvarchar(60)**|この列が所属するオブジェクトの名前。 sys.dm_xe_objects.id との間に多対一のリレーションシップがあります。NULL 値は許可されません。|  
|object_package_guid|**uniqueidentifier**|オブジェクトを含むパッケージの GUID。 NULL 値は許可されません。|  
|type_name|**nvarchar(60)**|この列の型の名前。 NULL 値は許可されません。|  
|type_package_guid|**uniqueidentifier**|列のデータ型を含むパッケージの GUID。 NULL 値は許可されません。|  
|column_type|**nvarchar(60)**|この列の使用方法を示します。 NULL 値は許可されません。 column_type には、次のいずれかを指定できます。<br /><br /> readonly。 変更できない静的な値が列に格納されます。<br /><br /> data。 オブジェクトによって公開される実行時データが列に格納されます。<br /><br /> customizable。 変更できる値が列に格納されます。<br /><br /> 注:、オブジェクトの動作を変更この値を変更することができます。|  
|column_value|**nvarchar (256)**|オブジェクト列に関連付けられた静的な値を表示します。 NULL 値が許可されます。|  
|capabilities|**int**|列の機能を説明するビットマップ。 NULL 値が許可されます。|  
|capabilities_desc|**nvarchar (256)**|このオブジェクトの列の機能の説明。 この値は次のいずれかになります。<br /><br /> Mandatory。 親オブジェクトをイベント セッションにバインドするときに値を設定する必要があります。<br /><br /> NULL|  
|description|**nvarchar (256)**|このオブジェクトの列の説明。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name、sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name、<br /><br /> sys.dm_xe_objects.package_guid|多対一|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

