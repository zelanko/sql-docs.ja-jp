---
title: sys.service_contract_message_usages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d83783a6ad2bdaf28e4da16d0759303920bac770
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysservicecontractmessageusages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コントラクトとメッセージ型の 1 つの組ごとに 1 行のデータを格納するカタログ ビューです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|メッセージ型を使用するコントラクトの識別子。 Null を許容しません。|  
|**message_type_id**|**int**|コントラクトで使用されるメッセージ型の識別子。 Null を許容しません。|  
|**is_sent_by_initiator**|**bit**|メッセージ交換の発信側で送信できるメッセージ型。 Null を許容しません。|  
|**is_sent_by_target**|**bit**|メッセージ交換の発信先で送信できるメッセージ型。 Null を許容しません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
  
