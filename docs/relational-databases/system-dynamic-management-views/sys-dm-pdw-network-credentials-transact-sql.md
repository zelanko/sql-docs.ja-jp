---
description: dm_pdw_network_credentials (Transact-sql)
title: dm_pdw_network_credentials (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 922c1ec6594f01488515bc1e9f18efa07a53e884
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489802"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>dm_pdw_network_credentials (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  すべての対象サーバーのアプライアンスに格納されているすべてのネットワーク資格情報の一覧を返し [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ます。 結果は、[制御] ノードとすべての計算ノードに表示されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id。|  
|target_server_name|**nvarchar(32)**|[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ユーザー名とパスワードの資格情報を使用してにアクセスするターゲットサーバーの IP アドレス。|  
|username|**nvarchar(32)**|パスワードが格納されているユーザー名。|  
|last_modified|**datetime**|資格情報を最後に変更した操作の日時。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 この動的管理ビューのキーは *pdw_node_id* プラス *target_server_name*です。  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
