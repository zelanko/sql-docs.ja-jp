---
title: では (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d055e9b76d248319bddb37241b1b79428ee5f3b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470810"
---
# <a name="dbosysjobschedules-transact-sql"></a>では (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  によって実行されるジョブのスケジュール情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。 このテーブルに格納されます、 **msdb**データベース。  
  
> **注:** **Sysjobschedules**テーブル更新 20 分ごと、によって返される値に影響する可能性があります、 **sp_help_jobschedule**ストアド プロシージャ。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|スケジュールの ID。|  
|**job_id**|**uniqueidentifier**|ジョブの ID。|  
|**next_run_date**|**int**|実行するジョブがスケジュールされている次の日。 日付の書式設定 yyyymmdd 形式で指定します。|  
|**next_run_time**|**int**|ジョブが実行するスケジュールされた時刻。 時間は、HHMMSS の形式し、24 時間制を使用します。|  
  
## <a name="see-also"></a>参照  
 [dbo.sysschedules &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
