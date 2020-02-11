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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7c822d5f405b353a9c07902fc1ef8f9272ad4353
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68109492"
---
# <a name="sysconversation_groups-transact-sql"></a>conversation_groups (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ交換グループごとに 1 行のデータを格納するカタログ ビューです。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**conversation_group_id**|**UNIQUEIDENTIFIER**|メッセージ交換グループの識別子。 NULL 値は許容されません。|  
|**service_id**|**int**|このグループのメッセージ交換で使用されるサービスの識別子。 NULL 値は許容されません。|  
|**is_system**|**bit**|システム インスタンスであるかどうかを示します。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
