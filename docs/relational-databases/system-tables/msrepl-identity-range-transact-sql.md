---
title: MSrepl_identity_range (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c1949134790942ea510060534a4760e76b63469d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824856"
---
# <a name="msrepl_identity_range-transact-sql"></a>MSrepl_identity_range (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range**テーブルでは、id 範囲の管理がサポートされています。 このテーブルは、パブリケーション、ディストリビューション、およびサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|パブリッシャーの名前です。|  
|**publisher_db**|**sysname**|パブリケーションデータベースの名前です。|  
|**テーブル**|**sysname**|テーブルの名前。|  
|**identity_support**|**int**|Id 範囲の自動処理を有効にするかどうかを指定します。 0は、自動 id 範囲の処理が有効になっていないことを示します。|  
|**next_seed**|**bigint**|ID 範囲の自動処理が有効な場合、次の範囲の開始位置を指定します。|  
|**pub_range**|**bigint**|パブリッシャーの id 範囲のサイズ。|  
|**range**|**bigint**|調整でサブスクライバーに割り当てられる連続する id 値のサイズ。|  
|**max_identity**|**bigint**|ID 範囲の上限です。|  
|**進入**|**int**|Id 範囲のしきい値の割合。|  
|**current_max**|**bigint**|割り当て可能であるが必ずしも割り当てられていない、現在の最大値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
