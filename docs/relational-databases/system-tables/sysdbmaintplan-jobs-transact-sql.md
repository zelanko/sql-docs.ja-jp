---
title: sysdbmaintplan_jobs (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_jobs
- sysdbmaintplan_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_jobs system table
ms.assetid: bc65cd70-6ef2-4c17-be11-877ecf4efe50
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8ea1dea0b8846d5c307650fab56527edfac251c1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825851"
---
# <a name="sysdbmaintplan_jobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードされたインスタンスの情報を保持するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属されたものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、このテーブルの内容は変更されません。 このテーブルは、 **msdb**データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|データベースメンテナンスプランの ID。|  
|**job_id**|**uniqueidentifier**|データベースメンテナンスプランに関連付けられているジョブの ID。|  
  
  
