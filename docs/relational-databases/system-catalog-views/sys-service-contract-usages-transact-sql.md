---
title: service_contract_usages (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fbf34e4247feb3911201f27518be57375971b40d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894918"
---
# <a name="sysservice_contract_usages-transact-sql"></a>service_contract_usages (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このカタログビューには、(サービス、コントラクト) のペアごとに1行が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|コントラクトを使用するサービスの識別子。 NULL 値は許容されません。|  
|**service_contract_id**|**int**|サービスによって使用されるコントラクトの識別子。 NULL 値は許容されません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
