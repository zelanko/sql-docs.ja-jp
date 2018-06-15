---
title: MSsubscription_articles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a5f1530091601cb241da7f1e4b1d48e02f699497
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005009"
---
# <a name="mssubscriptionarticles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_articles**テーブルには、キューに置かれたサブスクリプション内のアーティクルに関する情報が含まれています。 このテーブルは、レプリケーションの種類がキュー更新の場合と、フェールオーバーとしてキュー更新を行う即時更新の場合にのみ設定されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|アーティクルを処理するエージェントの ID|  
|**artid**|**int**|アーティクル ID を**sysarticles**テーブル。|  
|**article**|**sysname**|アーティクルの名前、 **sysarticles**テーブル。|  
|**dest_table**|**sysname**|変換先テーブルの名前、 **sysarticles**テーブル。|  
|**所有者**|**sysname**|サブスクリプションの所有者|  
|**cft_table**|**sysname**|レプリケーションのタイプがキュー更新の場合、アーティクルの競合テーブルの名前|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
