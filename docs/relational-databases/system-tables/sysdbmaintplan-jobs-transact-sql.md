---
title: sysdbmaintplan_jobs (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_jobs
- sysdbmaintplan_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_jobs system table
ms.assetid: bc65cd70-6ef2-4c17-be11-877ecf4efe50
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be7e3d6cc12f84c9dd85c664cfd5195310ffae26
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdbmaintplanjobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードされたインスタンスの情報を保持するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属されたものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このテーブルの内容は変更されません。 次の表は、 **msdb**データベース。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|データベース メンテナンス プランの ID|  
|**job_id**|**uniqueidentifier**|データベース メンテナンス プランに関連付けられているジョブの ID|  
  
  
