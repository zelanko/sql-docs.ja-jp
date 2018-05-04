---
title: sysmergesubsetfilters (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 096048edcfef0334333af4f97561f8e6261cf078
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パーティション分割されたアーティクルの結合フィルター情報を格納します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**filtername**|**sysname**|アーティクルを作成するときに使用したフィルターの名前。|  
|**join_filterid**|**int**|結合フィルター オブジェクトの ID。|  
|**pubid**|**uniqueidentifier**|パブリケーションの ID。|  
|**artid**|**uniqueidentifier**|アーティクルの ID。|  
|**art_nickname**|**int**|アーティクルのニックネーム。|  
|**join_articlename**|**sysname**|行が属しているかどうかを判断するために結合するテーブルの名前。|  
|**join_nickname**|**int**|行が属しているかどうかを判断するために結合するテーブルのニックネーム。|  
|**join_unique_key**|**int**|一意のキーの結合を示します**join_tablename**:<br /><br /> 0 = 一意キーではない<br /><br /> 1 = 一意キー|  
|**expand_proc**|**sysname**|マージ エージェントが、サブスクライバーに対して送信または削除する必要がある行を識別するために使用するストアド プロシージャの名前。|  
|**join_filterclause**|**nvarchar(1000)**|結合で使用するフィルター句。|  
|**filter_type**|**tinyint**|フィルターの種類。次のいずれかになります。<br /><br /> 1 = 結合フィルター<br /><br /> 2 = 論理レコード リンク<br /><br /> 3 = 結合フィルターと論理レコード リンクの両方|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
