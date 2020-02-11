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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: bfdd322107da1a08edb3933aee9d5b79b6c2b47a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67904434"
---
# <a name="sysroutes-transact-sql"></a>sys. route (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  このカタログビューには、ルートごとに1つの行が含まれています。 Service Broker では、ルートを使用してサービスのネットワーク アドレスを特定します。   

|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ルートの名前。データベース内で一意です。 NULL 値は許容されません。|  
|**route_id**|**int**|ルートの識別子。 NULL 値は許容されません。|  
|**principal_id**|**int**|ルートを所有するデータベース プリンシパルの識別子。 NULLABLE.|  
|**remote_service_name**|**nvarchar(256)**|リモートサービスの名前。 NULLABLE.|  
|**broker_instance**|**nvarchar(128**|リモートサービスをホストするブローカーの識別子。 NULLABLE.|  
|**最短**|**DATETIME**|ルートの有効期限が切れる日付と時刻。 この値はローカルタイムゾーンを使用しないことに注意してください。 代わりに、値は UTC の有効期限を示します。 NULLABLE.|  
|**先**|**nvarchar(256)**|Service Broker リモートサービスのメッセージを送信するネットワークアドレス。 NULLABLE. SQL Database Managed Instance の場合、アドレスはローカルである必要があります。|  
|**mirror_address**|**nvarchar(256)**|アドレスに指定されたサーバーのミラーリングパートナーのネットワークアドレス。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
