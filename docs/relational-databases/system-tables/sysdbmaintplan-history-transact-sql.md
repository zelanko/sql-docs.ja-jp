---
title: sysdbmaintplan_history (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: a51e2ea16ab7cc34ade122284a7162707c4d8f7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732670"
---
# <a name="sysdbmaintplanhistory-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルに格納されます、 **msdb**データベース。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|列名|データ型|説明|  
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
|**message**|**nvarchar(512)**|によって生成されたメッセージ**sqlmaint**します。|  
  
  
