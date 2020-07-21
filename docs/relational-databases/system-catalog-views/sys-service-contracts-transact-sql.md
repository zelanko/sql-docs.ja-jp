---
title: service_contracts (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contracts_TSQL
- sys.service_contracts_TSQL
- sys.service_contracts
- service_contracts
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contracts catalog view
ms.assetid: 787dd47e-4210-439d-9c4a-57a727a0dbd8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f0aaada78471cb31e24d3adfd5d1f541d33430a7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894912"
---
# <a name="sysservice_contracts-transact-sql"></a>sys.service_contracts (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このカタログビューには、データベース内の各コントラクトの行が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|コントラクトの名前。データベース内で一意です。 NULL 値は許容されません。|  
|**service_contract_id**|**int**|コントラクトの識別子。 NULL 値は許容されません。|  
|**principal_id**|**int**|コントラクトを所有するデータベース プリンシパルの識別子。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
  
