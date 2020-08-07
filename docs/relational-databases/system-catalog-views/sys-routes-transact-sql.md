---
title: sys. route (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b15dc8ebf9bbe9616ada47627a638b7d34d7c278
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862899"
---
# <a name="sysroutes-transact-sql"></a>sys. route (Transact-sql)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  このカタログビューには、ルートごとに1つの行が含まれています。 Service Broker では、ルートを使用してサービスのネットワーク アドレスを特定します。   

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ルートの名前。データベース内で一意です。 NULL 値は許容されません。|  
|**route_id**|**int**|ルートの識別子。 NULL 値は許容されません。|  
|**principal_id**|**int**|ルートを所有するデータベース プリンシパルの識別子。 NULLABLE.|  
|**remote_service_name**|**nvarchar (256)**|リモートサービスの名前。 NULLABLE.|  
|**broker_instance**|**nvarchar(128)**|リモートサービスをホストするブローカーの識別子。 NULLABLE.|  
|**lifetime**|**datetime**|ルートの有効期限が切れる日付と時刻。 この値はローカルタイムゾーンを使用しないことに注意してください。 代わりに、値は UTC の有効期限を示します。 NULLABLE.|  
|**address**|**nvarchar (256)**|Service Broker リモートサービスのメッセージを送信するネットワークアドレス。 NULLABLE. SQL Managed Instance の場合、アドレスはローカルである必要があります。|  
|**mirror_address**|**nvarchar (256)**|アドレスに指定されたサーバーのミラーリングパートナーのネットワークアドレス。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
