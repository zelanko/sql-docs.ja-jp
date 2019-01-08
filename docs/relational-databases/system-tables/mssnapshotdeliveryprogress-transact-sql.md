---
title: MSsnapshotdeliveryprogress (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67b6a2c048f8e873d6daa447270e00c1eda86c3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751454"
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshotdeliveryprogress**が正常に配信されたサブスクライバーにスナップショットが適用されているときにファイルを追跡するテーブルを使用します。 マージ エージェントがセッション中にすべてのファイルを配信できなかった場合に、このデータを使用してファイルの配信を再開し、次にマージ エージェントが実行されたときに同じファイルが再度配信されないようにします。 このテーブルは、サブスクライバー側でサブスクリプション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|ファイルが正常に配信された配信元のスナップショット フォルダーへのパスを識別します。 文字列のパラメーター化されたフィルターを使用するパブリケーションの**dynsnap**が値に追加されます。|  
|**progress_token_hash**|**int**|生成されたハッシュ値の値に基づく*progress_token*ために使用される参照の効率を向上させる、指定された*progress_token*値。|  
|**progress_token**|**nvarchar(500)**|正常に配信されたファイルを識別します。値は、ファイル名とパスの組み合わせです。|  
|**progress_timestamp**|**datetime**|**Datetime**スナップショット ファイルが正常に配信するタイミングを示す値です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
