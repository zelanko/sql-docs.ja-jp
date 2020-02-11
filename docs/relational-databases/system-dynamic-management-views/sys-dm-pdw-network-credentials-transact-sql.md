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
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b75eb53da9961025e3310f27e4a12608dd4fda78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899355"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>dm_pdw_network_credentials (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  すべての対象サーバーの[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスに格納されているすべてのネットワーク資格情報の一覧を返します。 結果は、[制御] ノードとすべての計算ノードに表示されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id。|  
|target_server_name|**nvarchar (32)**|ユーザー名とパスワードの資格情報[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用してにアクセスするターゲットサーバーの IP アドレス。|  
|username|**nvarchar (32)**|パスワードが格納されているユーザー名。|  
|last_modified|**DATETIME**|資格情報を最後に変更した操作の日時。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 この動的管理ビューのキーは*pdw_node_id*プラス*target_server_name*です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
