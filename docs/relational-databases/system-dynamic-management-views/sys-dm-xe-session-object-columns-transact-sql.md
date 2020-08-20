---
description: dm_xe_session_object_columns (Transact-sql)
title: dm_xe_session_object_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_object_columns_TSQL
- sys.dm_xe_session_object_columns_TSQL
- dm_xe_session_object_columns
- sys.dm_xe_session_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- xe
- sys.dm_xe_session_object_columns dynamic management view
ms.assetid: e97f3307-2da6-4c54-b818-a474faec752e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba65acaf8feb98a959e9ef37c7fdd26d1ce29121
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498268"
---
# <a name="sysdm_xe_session_object_columns-transact-sql"></a>dm_xe_session_object_columns (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  セッションにバインドされたオブジェクトの構成値を示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 sys.dm_xe_sessions.address との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|column_name|**nvarchar (256)**|構成値の名前。 NULL 値は許可されません。|  
|column_id|**int**|列の ID。 は、オブジェクト内で一意です。 NULL 値は許可されません。|  
|column_value|**nvarchar (3072)**|列の構成値。 NULL 値が許可されます。|  
|object_type|**nvarchar(60)**|オブジェクトの型。 NULL 値は許可されません。 object_type は次のいずれかです。<br /><br /> event<br /><br /> ターゲット (target)|  
|object_name|**nvarchar (256)**|この列が所属するオブジェクトの名前。 NULL 値は許可されません。|  
|object_package_guid|**uniqueidentifier**|オブジェクトを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|ソース|終了|リレーションシップ|  
|----------|--------|------------------|  
|dm_xe_session_object_columns。 object_name、<br /><br /> dm_xe_session_object_columns.object_package_guid|dm_xe_objects。 package_guid、<br /><br /> sys.dm_xe_objects.name|多対一|  
|dm_xe_session_object_columns。 column_name、<br /><br /> dm_xe_session_object_columns.column_id|dm_xe_object_columns。名前、<br /><br /> sys.dm_xe_object_columns.column_id|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

