---
title: sys.service_queue_usages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
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
- sys.service_queue_usages
- sys.service_queue_usages_TSQL
- service_queue_usages
- service_queue_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queue_usages catalog view
ms.assetid: d58dcdaf-f82d-43d9-941b-f520581442bf
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e593676f104b0a680fa8066f557b95e0eadde22
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysservicequeueusages-transact-sql"></a>sys.service_queue_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サービスとサービス キュー間の参照ごとに 1 行のデータを返すカタログ ビューです。 1 つのサービスは 1 つのキューにのみ関連付けることができます。 1 つのキューは複数のサービスに関連付けることができます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|サービスの識別子。 データベース内で一意です。 Null を許容しません。|  
|**service_queue_id**|**int**|サービスにより使用されるサービス キューの識別子。 Null を許容しません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [sys.services &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)  
  
  
