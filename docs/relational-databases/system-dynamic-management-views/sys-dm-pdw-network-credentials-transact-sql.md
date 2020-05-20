---
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
ms.openlocfilehash: 87134a4898b0eb5e314aa4c0f860755a9618b4c5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830488"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>dm_pdw_network_credentials (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

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
 この動的管理ビューのキーは*pdw_node_id*プラス*target_server_name*です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
