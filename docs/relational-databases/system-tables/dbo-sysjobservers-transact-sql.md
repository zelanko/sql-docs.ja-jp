---
title: dbo.sysjobservers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 635c71efaeed6d41a9b9e62ef3e8c79b4e9aae95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607280"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のジョブと 1 つ以上の対象サーバーとの関連付けまたはリレーションシップを格納します。このテーブルは、msdb データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|ジョブ識別番号。|  
|server_id|**int**|サーバーの識別番号。|  
|last_run_outcome|**tinyint**|前回のジョブの実行結果。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **3** = キャンセル|  
|last_outcome_ message|**nvarchar(1024)**|last_run_outcome 列に関連付けられているメッセージ (存在する場合)。|  
|last_run_date|**int**|ジョブの前回の実行日付。|  
|last_run_time|**int**|ジョブの前回の実行時刻。|  
|last_run_duration|**int**|ジョブが実行された期間を時間、分、および秒単位で表したもの。 数式を使用して計算: (*時間*\*10000) + (*分*\*100) +*秒*します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
