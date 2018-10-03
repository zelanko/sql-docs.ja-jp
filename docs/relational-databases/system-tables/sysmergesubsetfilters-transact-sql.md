---
title: sysmergesubsetfilters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0b87c85c3d45c87aed84604bb0b7732c47ffa5e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783280"
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パーティション分割されたアーティクルの結合フィルター情報を格納します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**filtername**|**sysname**|アーティクルを作成するときに使用したフィルターの名前。|  
|**join_filterid**|**int**|結合フィルター オブジェクトの ID。|  
|**pubid**|**uniqueidentifier**|パブリケーションの ID。|  
|**artid**|**uniqueidentifier**|アーティクルの ID。|  
|**art_nickname**|**int**|アーティクルのニックネーム。|  
|**join_articlename**|**sysname**|行が属しているかどうかを判断するために結合するテーブルの名前。|  
|**join_nickname**|**int**|行が属しているかどうかを判断するために結合するテーブルのニックネーム。|  
|**join_unique_key**|**int**|一意なキーに基づいて結合を示します**join_tablename**:<br /><br /> 0 = 一意キーではない<br /><br /> 1 = 一意キー|  
|**expand_proc**|**sysname**|マージ エージェントが、サブスクライバーに対して送信または削除する必要がある行を識別するために使用するストアド プロシージャの名前。|  
|**join_filterclause**|**nvarchar(1000)**|結合で使用するフィルター句。|  
|**filter_type**|**tinyint**|フィルターの種類。次のいずれかになります。<br /><br /> 1 = 結合フィルター<br /><br /> 2 = 論理レコード リンク<br /><br /> 3 = 結合フィルターと論理レコード リンクの両方|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
