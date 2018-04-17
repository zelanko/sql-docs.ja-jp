---
title: MSreplmonthresholdmetrics (TRANSACT-SQL) |Microsoft ドキュメント
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 090ac1f5a2ff97bcc243506537952308a665a2e6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplmonthresholdmetrics**テーブルがレプリケーションを監視するためのメトリックを定義します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|レプリケーションのパフォーマンスの測定基準を識別し、値は次のいずれかを指定することができます。<br /><br /> **1**有効期限を =<br /><br /> **2**待機時間を =<br /><br /> **4** mergeexpiration を =<br /><br /> **5** mergeslowrunduration を =<br /><br /> **6** mergefastrunduration を =<br /><br /> **7** mergefastrunspeed を =<br /><br /> **8** mergeslowrunspeed を =|  
|**title**|**sysname**|レプリケーション パフォーマンス基準の名前。|  
|**warningbitstatus**|**int**|次のいずれかの基準に対応するしきい値違反の警告を示す、ビットごとの識別子です。<br /><br /> **1** = expiration: トランザクション パブリケーションに対するサブスクリプションが、保有期間のしきい値を超えるによって、保有期間のパーセンテージを超えました。<br /><br /> **2** = 待機時間: トランザクション パブリッシャーからサブスクライバーにデータをレプリケートにかかった時間 (秒) がしきい値を超えています。<br /><br /> **4** = mergeexpiration: マージ パブリケーションに対するサブスクリプションが、保有期間ので、許容されるしきい値を超える保有期間のパーセンテージを超えました。<br /><br /> **8** = mergefastrunduration: マージ サブスクリプションの同期の完了にかかった時間のしきい値を超過、秒単位で高速ネットワーク接続します。<br /><br /> **16** = mergeslowrunduration – マージ サブスクリプションの同期の完了にかかった時間低速またはダイヤルアップ ネットワーク接続経由で (秒単位) がしきい値を超えています。<br /><br /> **32** = mergefastrunspeed 配信率、マージ サブスクリプションの同期中の行は、高速ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。<br /><br /> **64** = mergeslowrunspeed 配信率、マージ サブスクリプションの同期中の行が低速またはダイヤルアップ ネットワーク接続経由でのしきい値の割合を 1 秒あたりの行を維持するために失敗しました。|  
|**alertmessageid**|**int**|しきい値の警告が発生した場合に表示されるエラー メッセージの ID。|  
|**説明**|**nvarchar(3000)**|レプリケーション パフォーマンス基準の説明。|  
|**default_value**|**sql_variant**|レプリケーション パフォーマンス基準の既定値。|  
|**min_value**|**sql_variant**|範囲指定のレプリケーション パフォーマンス基準の最小値。|  
|**max_value**|**sql_variant**|範囲指定のレプリケーション パフォーマンス基準の最大値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
