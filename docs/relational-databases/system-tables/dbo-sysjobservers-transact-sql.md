---
title: "dbo.sysjobservers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a706c537f4f983563dacb1f137314680824dd30
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のジョブと 1 つ以上の対象サーバーとの関連付けまたはリレーションシップを格納します。このテーブルは、msdb データベースに格納されます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|ジョブ識別番号。|  
|server_id|**int**|サーバーの識別番号。|  
|last_run_outcome|**tinyint**|前回のジョブの実行結果。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = キャンセル|  
|last_outcome_ メッセージ|**nvarchar (1024)**|last_run_outcome 列に関連付けられているメッセージ (存在する場合)。|  
|last_run_date|**int**|ジョブの前回の実行日付。|  
|last_run_time|**int**|ジョブの前回の実行時刻。|  
|last_run_duration|**int**|ジョブが実行された期間を時間、分、および秒単位で表したもの。 数式を使用して計算: (*時間*\*10000) + (*分*\*100) +*秒*です。|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
