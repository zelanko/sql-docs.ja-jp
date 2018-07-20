---
title: MSsubscriber_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MSsubscriber_schedule
- MSsubscriber_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_schedule system table
ms.assetid: ff428306-0ef4-49a3-b536-07ccdf6e2196
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1424947221413447e0277df4c10b17c0ea08d8b2
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103660"
---
# <a name="mssubscriberschedule-transact-sql"></a>MSsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscriber_schedule**テーブルには、既定のマージとトランザクション同期スケジュール パブリッシャー/サブスクライバーの各ペアが含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
> [!NOTE]  
>  このシステム テーブルは非推奨し、以前のバージョンをサポートするために保持されている[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前。|  
|**agent_type**|**smallint**|エージェントの種類。<br /><br /> 0 = ディストリビューション エージェント<br /><br /> 1 = マージ エージェント|  
|**frequency_type**|**int**|ディストリビューション エージェントをスケジュール設定する頻度。<br /><br /> **1** = 1 回です。<br /><br /> **2** = 要求時。<br /><br /> **4**毎日を = です。<br /><br /> **8** = 毎週。<br /><br /> **16**毎月を = です。<br /><br /> **32** = 月単位。<br /><br /> **64** = 自動開始します。<br /><br /> **128**定期的なを = です。|  
|**frequency_interval**|**int**|設定した頻度に適用する値**frequency_type**します。|  
|**frequency_relative_interval**|**int**|ディストリビューション エージェントの日付。<br /><br /> **1**最初を = です。<br /><br /> **2**秒を = です。<br /><br /> **4**サードを = です。<br /><br /> **8**第 4 を = です。<br /><br /> **16**最後を = です。|  
|**frequency_recurrence_factor**|**int**|使用される定期実行係数**frequency_type**します。|  
|**frequency_subday**|**int**|定義した期間にスケジュールを組み直す頻度。<br /><br /> **1** = 1 回です。<br /><br /> **2**秒を = です。<br /><br /> **4** = 分。<br /><br /> **8** = 1 時間です。|  
|**frequency_subday_interval**|**int**|間隔**frequency_subday**します。|  
|**active_start_time_of_day**|**int**|ディストリビューション エージェントのスケジュールの開始時刻。HHMMSS の形式で表されます。|  
|**active_end_time_of_day**|**int**|ディストリビューション エージェントのスケジュールの終了時刻。HHMMSS の形式で表されます。|  
|**active_start_date**|**int**|ディストリビューション エージェントのスケジュールの開始日。YYYYMMDD の形式で表されます。|  
|**active_end_date**|**int**|ディストリビューション エージェントのスケジュールの終了日。YYYYMMDD の形式で表されます。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
