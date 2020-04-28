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
author: stevestein
ms.author: sstein
ms.openlocfilehash: f780199361d9e5741187dd4e5346abb2df98b9cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130441"
---
# <a name="sysdbmaintplan_jobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードされたインスタンスの情報を保持するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属されたものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、このテーブルの内容は変更されません。 このテーブルは、 **msdb**データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|データベースメンテナンスプランの ID。|  
|**job_id**|**uniqueidentifier**|データベースメンテナンスプランに関連付けられているジョブの ID。|  
  
  
