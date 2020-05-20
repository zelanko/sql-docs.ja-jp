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
ms.openlocfilehash: 2769fcd0ec6dde419c9ebba2f3cfb0017cf74b0b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831391"
---
# <a name="sysroutes-transact-sql"></a>sys. route (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  このカタログビューには、ルートごとに1つの行が含まれています。 Service Broker では、ルートを使用してサービスのネットワーク アドレスを特定します。   

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ルートの名前。データベース内で一意です。 NULL 値は許容されません。|  
|**route_id**|**int**|ルートの識別子。 NULL 値は許容されません。|  
|**principal_id**|**int**|ルートを所有するデータベース プリンシパルの識別子。 NULLABLE.|  
|**remote_service_name**|**nvarchar(256)**|リモートサービスの名前。 NULLABLE.|  
|**broker_instance**|**nvarchar(128)**|リモートサービスをホストするブローカーの識別子。 NULLABLE.|  
|**最短**|**datetime**|ルートの有効期限が切れる日付と時刻。 この値はローカルタイムゾーンを使用しないことに注意してください。 代わりに、値は UTC の有効期限を示します。 NULLABLE.|  
|**address**|**nvarchar(256)**|Service Broker リモートサービスのメッセージを送信するネットワークアドレス。 NULLABLE. SQL Database Managed Instance の場合、アドレスはローカルである必要があります。|  
|**mirror_address**|**nvarchar(256)**|アドレスに指定されたサーバーのミラーリングパートナーのネットワークアドレス。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
