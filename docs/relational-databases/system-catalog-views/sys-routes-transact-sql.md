---
title: sys.routes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21420e923b4120f547026c6a6a0d96d86deac782
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  ルートごとに 1 行のデータを格納するカタログ ビューです。 Service Broker では、ルートを使用してサービスのネットワーク アドレスを特定します。   

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ルートの名前。データベース内で一意です。 Null を許容しません。|  
|**route_id**|**int**|ルートの識別子。 Null を許容しません。|  
|**principal_id**|**int**|ルートを所有するデータベース プリンシパルの識別子。 NULL 値は許可されます。|  
|**remote_service_name**|**nvarchar (256)**|リモート サービスの名前。 NULL 値は許可されます。|  
|**broker_instance**|**nvarchar(128)**|リモート サービスをホストするブローカーの識別子。 NULL 値は許可されます。|  
|**lifetime**|**datetime**|ルートが期限切れとなる日時。 この値はローカル タイム ゾーンの値ではなく、 UTC での有効期限の日時です。 NULL 値は許可されます。|  
|**address**|**nvarchar (256)**|Service Broker がリモート サービス宛のメッセージを送信するネットワーク アドレス。 NULL 値は許可されます。 SQL データベースのマネージ インスタンスのアドレスをローカルにする必要があります。|  
|**mirror_address**|**nvarchar (256)**|アドレスで指定されているサーバーの、ミラーリング パートナーのネットワーク アドレス。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
  
