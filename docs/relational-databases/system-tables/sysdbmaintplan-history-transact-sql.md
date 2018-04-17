---
title: sysdbmaintplan_history (TRANSACT-SQL) |Microsoft ドキュメント
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
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0c42b7c455c0bcbb08913bbe5ae88422e7cace7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  次の表は、 **msdb**データベース。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|データベース メンテナンス プランで実行された履歴のシーケンス|  
|**plan_id**|**uniqueidentifier**|データベース メンテナンス プランの ID|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**database_name**|**sysname**|このデータベース メンテナンス プランが関連付けられているデータベースの名前|  
|**server_name**|**sysname**|システム名|  
|**activity**|**nvarchar(128)**|データベース メンテナンス プランで実行された操作 (トランザクション ログのバックアップなど)|  
|**succeeded**|**bit**|**0** = 成功**1** = 失敗|  
|**end_time**|**datetime**|操作が完了した時刻|  
|**duration**|**int**|データベース メンテナンス プラン操作が完了するまでの所用時間|  
|**start_time**|**datetime**|操作が開始された時刻|  
|**error_number**|**int**|失敗時に報告されたエラー番号|  
|**message**|**nvarchar(512)**|によって生成されたメッセージ**sqlmaint**です。|  
  
  
