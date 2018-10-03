---
title: sys.service_contract_usages (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_usages
- sys.service_contract_usages
- sys.service_contract_usages_TSQL
- service_contract_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_usages catalog view
ms.assetid: 20af425e-1152-4a46-b1ac-94cff5fc9f02
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a34d69fe4d8d8de6668e804bc574c18196f0aa8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667610"
---
# <a name="sysservicecontractusages-transact-sql"></a>sys.service_contract_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サービスとコントラクトの 1 つの組ごとに 1 行を格納するカタログ ビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|コントラクトを使用するサービスの識別子。 Null を許容しません。|  
|**service_contract_id**|**int**|サービスが使用するコントラクトの識別子。 Null を許容しません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
