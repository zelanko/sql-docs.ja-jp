---
title: MSreplmonthresholdmetrics (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c72fccdc6c23e65bd94d3ae7ab5a5b0ab0e4eaa9
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101370"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplmonthresholdmetrics**テーブルがレプリケーションを監視するためのメトリックを定義します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|レプリケーションのパフォーマンスの測定基準を識別し、値は次のいずれかを指定することができます。<br /><br /> **1**有効期限を =<br /><br /> **2**待機時間を =<br /><br /> **4** mergeexpiration を =<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** mergefastrunspeed を =<br /><br /> **8** mergeslowrunspeed を =|  
|**title**|**sysname**|レプリケーション パフォーマンス基準の名前。|  
|**warningbitstatus**|**int**|次のいずれかの基準に対応するしきい値違反の警告を示す、ビットごとの識別子です。<br /><br /> **1** = expiration: トランザクション パブリケーションに対するサブスクリプションが保有期間のしきい値を超えるによって保有期間のパーセンテージを超えました。<br /><br /> **2** = 待機時間: トランザクション パブリッシャーからサブスクライバーへのデータのレプリケートにかかった時間 (秒)、しきい値を超えています。<br /><br /> **4** = mergeexpiration: マージ パブリケーションに対するサブスクリプションが保有期間のしきい値を超えるによって、保有期間のパーセンテージを超えました。<br /><br /> **8** = mergefastrunduration: マージ サブスクリプションの同期の完了にかかった時間、高速ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **16** = mergeslowrunduration – マージ サブスクリプションの同期の完了にかかった時間、低速またはダイヤルアップ ネットワーク接続経由で秒単位で、しきい値を超えています。<br /><br /> **32** = mergefastrunspeed 配信率のしきい値の割合で、1 秒あたりの行を高速ネットワーク接続経由で維持するために、マージ サブスクリプションの同期中の行が失敗しました。<br /><br /> **64** = mergeslowrunspeed 配信率マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合で、1 秒あたりの行を維持するために失敗しました。|  
|**alertmessageid**|**int**|しきい値の警告が発生した場合に表示されるエラー メッセージの ID。|  
|**description**|**nvarchar(3000)**|レプリケーション パフォーマンス基準の説明。|  
|**default_value**|**sql_variant**|レプリケーション パフォーマンス基準の既定値。|  
|**min_value**|**sql_variant**|範囲指定のレプリケーション パフォーマンス基準の最小値。|  
|**max_value**|**sql_variant**|範囲指定のレプリケーション パフォーマンス基準の最大値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
