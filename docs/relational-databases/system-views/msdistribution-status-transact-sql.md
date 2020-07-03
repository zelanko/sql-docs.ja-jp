---
title: MSdistribution_status (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_status_TSQL
- MSdistribution_status
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_status view
ms.assetid: 90d447de-3a4a-4f3e-aeab-e8fff6348361
author: stevestein
ms.author: sstein
ms.openlocfilehash: df060b429b48eb1e1a99c48dbb2789fce3e10833
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889167"
---
# <a name="msdistribution_status-transact-sql"></a>MSdistribution_status (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSdistribution_status**ビューでは、ディストリビューションデータベースの状態コマンドに関する追加情報が公開されます。 このビューは、ディストリビューション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|アーティクルを識別します。|  
|**agent_id**|**int**|レプリケーション エージェントを識別します。|  
|**UndelivCmdsInDistDB**|**int**|サブスクライバーへの配信が保留されているコマンドの数。|  
|**Sinvcmdsindistdb**|**int**|サブスクライバーに配信されたコマンドの数。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
