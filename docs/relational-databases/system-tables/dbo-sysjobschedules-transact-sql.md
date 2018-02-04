---
title: "では (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 272a950b77f541172b3c76ce4b5d597b9e908dee
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  によって実行されるジョブのスケジュール情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントです。 次の表は、 **msdb**データベース。  
  
> **注:** 、 **sysjobschedules**テーブル更新 20 分ごと、によって返される値に影響する可能性があります、 **sp_help_jobschedule**ストアド プロシージャです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|スケジュールの ID。|  
|**job_id**|**uniqueidentifier**|ジョブの ID です。|  
|**next_run_date**|**int**|ジョブの次回実行予定日。 日付の形式は YYYYMMDD です。|  
|**next_run_time**|**int**|ジョブの実行予定時刻。 時間は、書式設定 hhmmss で、24 時間制を使用しています。|  
  
## <a name="see-also"></a>参照  
 [dbo.sysschedules &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
