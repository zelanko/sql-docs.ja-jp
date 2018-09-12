---
title: sys.routes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 54817a71f8ef6cd4206b96848be0b903e282b750
ms.sourcegitcommit: d8e3da95f5a2b7d3997d63c53e722d494b878eec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2018
ms.locfileid: "44171734"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  ルートごとに 1 行のデータを格納するカタログ ビューです。 Service Broker では、ルートを使用してサービスのネットワーク アドレスを特定します。   

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|ルートの名前。データベース内で一意です。 Null を許容しません。|  
|**route_id**|**int**|ルートの識別子。 Null を許容しません。|  
|**principal_id**|**int**|ルートを所有するデータベース プリンシパルの識別子。 NULL 値は許可されます。|  
|**remote_service_name**|**nvarchar (256)**|リモート サービスの名前。 NULL 値は許可されます。|  
|**broker_instance**|**nvarchar(128)**|リモート サービスをホストするブローカーの識別子。 NULL 値は許可されます。|  
|**lifetime**|**datetime**|ルートが期限切れとなる日時。 この値はローカル タイム ゾーンの値ではなく、 UTC での有効期限の日時です。 NULL 値は許可されます。|  
|**address**|**nvarchar (256)**|Service Broker がリモート サービス宛のメッセージを送信するネットワーク アドレス。 NULL 値は許可されます。 SQL Database マネージ インスタンスのアドレスをローカルにある必要があります。|  
|**mirror_address**|**nvarchar (256)**|アドレスで指定されているサーバーの、ミラーリング パートナーのネットワーク アドレス。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
