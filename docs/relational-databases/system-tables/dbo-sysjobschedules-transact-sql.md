---
title: dbo. sysjobschedules (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: a7f2dfc6196bfba6c274eb45a45745159447cc39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061177"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo. sysjobschedules (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エージェントによって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行されるジョブのスケジュール情報を格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
> **注:****Sysjobschedules**テーブルは20分ごとに更新され、 **sp_help_jobschedule**ストアドプロシージャによって返される値に影響を与える可能性があります。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|スケジュールの ID。|  
|**job_id**|**UNIQUEIDENTIFIER**|ジョブの ID。|  
|**next_run_date**|**int**|ジョブの次回の実行予定日。 日付の形式は YYYYMMDD です。|  
|**next_run_time**|**int**|ジョブの実行がスケジュールされている時刻。 時刻は HHMMSS 形式で、24時間制を使用します。|  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の dbo の sysschedules](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
