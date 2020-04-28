---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4470b6b5d1b30f5698bf588a04066c50bb4c7197
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130450"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、 **msdb**データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|データベース メンテナンス プランで実行された履歴のシーケンス|  
|**plan_id**|**uniqueidentifier**|データベースメンテナンスプランの ID。|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**database_name**|**sysname**|データベースメンテナンスプランに関連付けられているデータベースの名前。|  
|**server_name**|**sysname**|システム名|  
|**activity**|**nvarchar(128)**|データベースメンテナンスプラン (バックアップトランザクションログなど) によって実行されるアクティビティ。|  
|**行わ**|**bit**|**0** = 成功**1** = 失敗|  
|**end_time**|**datetime**|操作が完了した時刻|  
|**duration**|**int**|データベース メンテナンス プラン操作が完了するまでの所用時間|  
|**start_time**|**datetime**|アクションが開始した時刻。|  
|**error_number**|**int**|エラーが発生した場合に報告されるエラー番号。|  
|**message**|**nvarchar(512)**|**Sqlmaint**によって生成されたメッセージ。|  
  
  
