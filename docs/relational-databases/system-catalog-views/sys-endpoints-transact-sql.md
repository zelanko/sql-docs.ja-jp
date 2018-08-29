---
title: sys.endpoints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- endpoints
- sys.endpoints
- endpoints_TSQL
- sys.endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoints catalog view
ms.assetid: e6dafa4e-e47e-43ec-acfc-88c0af53c1a1
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce1f8b2ecd2b182a8b6f8bd8a84fbc29d0d7b33c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027484"
---
# <a name="sysendpoints-transact-sql"></a>sys.endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システムで作成されたエンドポイントごとに 1 行のデータを格納します。 SYSTEM エンドポイントは常に 1 つだけ存在します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|エンドポイントの名前。 サーバー内で一意です。 NULL 値は許可されません。|  
|**endpoint_id**|**int**|エンドポイントの ID。 サーバー内で一意です。 65536 より小さい ID のエンドポイントは、システム エンドポイントです。 NULL 値は許可されません。|  
|**principal_id**|**int**|エンドポイントを作成し、所有しているサーバー プリンシパルの ID。 NULL 値が許可されます。|  
|**プロトコル**|**tinyint**|エンドポイントのプロトコル。<br /><br /> 1 = HTTP<br /><br /> 2 = TCP<br /><br /> 3 = 名前付きパイプ<br /><br /> 4 = 共有メモリ<br /><br /> 5 = 仮想インターフェイス アダプター (VIA)<br /><br /> NULL 値は許可されません。|  
|**protocol_desc**|**nvarchar(60)**|エンドポイントのプロトコルの説明。 NULL 値は許可されます。 次のいずれかの値です。<br /><br /> **HTTP**<br /><br /> **TCP**<br /><br /> **NAMED_PIPES**<br /><br /> **SHARED_MEMORY**<br /><br /> **使用して**に注意してください:「経由でプロトコルが非推奨とされます。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|**type**|**tinyint**|エンドポイントのペイロードの種類。<br /><br /> 1 = SOAP<br /><br /> 2 = TSQL<br /><br /> 3 = SERVICE_BROKER<br /><br /> 4 = DATABASE_MIRRORING<br /><br /> NULL 値は許可されません。|  
|**type_desc**|**nvarchar(60)**|エンドポイントのペイロードの種類の説明。 NULL 値が許可されます。 次のいずれかの値です。<br /><br /> **SOAP**<br /><br /> **TSQL**<br /><br /> **SERVICE_BROKER**<br /><br /> **DATABASE_MIRRORING**|  
|**state**|**tinyint**|エンドポイントの状態。<br /><br /> 0 = STARTED。要求のリスニングおよび処理中です。<br /><br /> 1 = STOPPED。要求のリスニング中で処理は行っていません。<br /><br /> 2 = DISABLED。リスニングしていません。<br /><br /> 既定の状態は 1 です。 NULL 値が許可されます。|  
|**state_desc**|**nvarchar(60)**|エンドポイントの状態の説明。<br /><br /> STARTED = 要求のリスニングおよび処理中です。<br /><br /> STOPPED = 要求のリスニング中で、処理は行っていません。<br /><br /> DISABLED = リスニングしていません。<br /><br /> 既定の状態は STOPPED です。<br /><br /> NULL 値が許可されます。|  
|**is_admin_endpoint**|**bit**|エンドポイントが管理者用かどうかを示します。<br /><br /> 0 = 管理者用以外のエンドポイント。<br /><br /> 1 = 管理者用エンドポイント。<br /><br /> NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エンドポイントのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
