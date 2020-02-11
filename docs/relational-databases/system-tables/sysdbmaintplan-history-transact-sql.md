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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130450"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、 **msdb**データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|データベース メンテナンス プランで実行された履歴のシーケンス|  
|**plan_id**|**UNIQUEIDENTIFIER**|データベースメンテナンスプランの ID。|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**database_name**|**sysname**|データベースメンテナンスプランに関連付けられているデータベースの名前。|  
|**server_name**|**sysname**|システム名|  
|**演習**|**nvarchar(128**|データベースメンテナンスプラン (バックアップトランザクションログなど) によって実行されるアクティビティ。|  
|**succeeded**|**bit**|**0** = 成功**1** = 失敗|  
|**end_time**|**DATETIME**|操作が完了した時刻|  
|**全**|**int**|データベース メンテナンス プラン操作が完了するまでの所用時間|  
|**start_time**|**DATETIME**|アクションが開始した時刻。|  
|**error_number**|**int**|エラーが発生した場合に報告されるエラー番号。|  
|**メッセージ**|**nvarchar(512)**|**Sqlmaint**によって生成されたメッセージ。|  
  
  
