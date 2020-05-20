---
title: conversation_groups (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- conversation_groups_TSQL
- conversation_groups
- sys.conversation_groups
- sys.conversation_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.conversation_groups catalog view
ms.assetid: 3f35815e-2de4-42a2-a972-8f0141dad0b3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b2c4815c87ba4c122efa9794294798c376cd79f1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821754"
---
# <a name="sysconversation_groups-transact-sql"></a>conversation_groups (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ交換グループごとに 1 行のデータを格納するカタログ ビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**conversation_group_id**|**uniqueidentifier**|メッセージ交換グループの識別子。 NULL 値は許容されません。|  
|**service_id**|**int**|このグループのメッセージ交換で使用されるサービスの識別子。 NULL 値は許容されません。|  
|**is_system**|**bit**|システム インスタンスであるかどうかを示します。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
