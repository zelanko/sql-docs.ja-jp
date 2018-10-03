---
title: sys.service_contract_message_usages (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 280686087a0099fa374664eb0cbfe9d7c2b244ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742060"
---
# <a name="sysservicecontractmessageusages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コントラクトとメッセージ型の 1 つの組ごとに 1 行のデータを格納するカタログ ビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|メッセージ型を使用するコントラクトの識別子。 Null を許容しません。|  
|**message_type_id**|**int**|コントラクトで使用されるメッセージ型の識別子。 Null を許容しません。|  
|**is_sent_by_initiator**|**bit**|メッセージ交換の発信側で送信できるメッセージ型。 Null を許容しません。|  
|**is_sent_by_target**|**bit**|メッセージ交換の発信先で送信できるメッセージ型。 Null を許容しません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
