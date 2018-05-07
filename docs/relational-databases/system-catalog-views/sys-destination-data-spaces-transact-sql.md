---
title: sys.destination_data_spaces (TRANSACT-SQL) |Microsoft ドキュメント
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
- sys.destination_data_spaces
- destination_data_spaces_TSQL
- destination_data_spaces
- sys.destination_data_spaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.destination_data_spaces catalog view
ms.assetid: 92df932b-ad5c-43f8-81f4-b158823ab189
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: acc10d0843e1cc24dcd1080fa71b273e39348428
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdestinationdataspaces-transact-sql"></a>sys.destination_data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パーティション構成のデータ領域の転送先ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_scheme_id**|**int**|データ領域にパーティション分割されるパーティション構成の ID です。|  
|**destination_id**|**int**|パーティション構成内で一意な、転送先マッピングの ID (1 から始まる序数) です。|  
|**data_space_id**|**int**|この構成の転送先のデータがマッピングされるデータ領域の ID です。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
