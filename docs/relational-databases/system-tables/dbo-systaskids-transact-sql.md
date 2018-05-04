---
title: dbo.systaskids (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
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
- systaskids_TSQL
- dbo.systaskids
- systaskids
- dbo.systaskids_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systaskids system table
ms.assetid: 45c56d89-4160-4d84-80bf-a7a05488792d
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7770d270d229bb27554a4d0d64905e80901dc15f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dbosystaskids-transact-sql"></a>dbo.systaskids (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  以前のバージョンで作成されたタスクのマッピングを格納[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ジョブ、現在のバージョン。 次の表は、 **msdb**データベース。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**task_id**|**int**|タスクの ID|  
|**job_id**|**uniqueidentifier**|タスクがマップされるジョブの ID|  
  
  
