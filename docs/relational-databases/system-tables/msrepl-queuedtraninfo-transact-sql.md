---
title: MSrepl_queuedtraninfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_queuedtraninfo_TSQL
- MSrepl_queuedtraninfo
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_queuedtraninfo system table
ms.assetid: af7a5baf-32ea-475f-b6b9-68c557b4980c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: debe88da4effd02ac15af965656232d4ec1f3395
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795488"
---
# <a name="msreplqueuedtraninfo-transact-sql"></a>MSrepl_queuedtraninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_queuedtraninfo** SQL ベースのキューに置かれた更新を使用している、キューに置かれたすべての更新サブスクリプションによって発行されたキューに登録されたコマンドに関する情報を格納する、テーブルがレプリケーション プロセスによって使用されます。 このテーブルは、サブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**tranid**|**sysname**|キューに登録されたコマンドが実行されたときのトランザクション ID。|  
|**maxorderkey**|**bigint**|内部使用のみ。|  
|**commandcount**|**bigint**|内部使用のみ。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
