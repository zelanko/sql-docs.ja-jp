---
description: sysdbmaintplan_history (Transact-SQL)
title: sysdbmaintplan_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5871f6acc8e4df58223e1568b0a253a7e62c42d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473156"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  このテーブルは、 **msdb** データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|データベース メンテナンス プランで実行された履歴のシーケンス|  
|**plan_id**|**uniqueidentifier**|データベースメンテナンスプランの ID。|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**database_name**|**sysname**|データベースメンテナンスプランに関連付けられているデータベースの名前。|  
|**server_name**|**sysname**|システム名|  
|**activity**|**nvarchar(128)**|データベースメンテナンスプラン (バックアップトランザクションログなど) によって実行されるアクティビティ。|  
|**succeeded**|**bit**|**0** = 成功 **1** = 失敗|  
|**end_time**|**datetime**|操作が完了した時刻|  
|**duration**|**int**|データベース メンテナンス プラン操作が完了するまでの所用時間|  
|**start_time**|**datetime**|アクションが開始した時刻。|  
|**error_number**|**int**|エラーが発生した場合に報告されるエラー番号。|  
|**message**|**nvarchar(512)**|**Sqlmaint**によって生成されたメッセージ。|  
  
  
