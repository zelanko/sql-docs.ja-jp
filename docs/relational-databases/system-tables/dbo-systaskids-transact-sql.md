---
title: systaskids (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ed9ac8e81abaf6367d3a9c5518f1f18cb94ef8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990400"
---
# <a name="dbosystaskids-transact-sql"></a>systaskids (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成されたタスクと、現在のバージョンの [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ジョブとのマッピングを格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**task_id**|**int**|タスクの ID|  
|**job_id**|**UNIQUEIDENTIFIER**|タスクがマップされているジョブの ID|  
  
  
