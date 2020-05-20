---
title: sysdbmaintplans (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b787b62f1f4f68c279449aa9bf4bc905898ec66d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82803120"
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このテーブルは、以前のバージョンの [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードされたインスタンスの情報を保持するために、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属されたものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、このテーブルの内容は変更されません。 このテーブルは、 **msdb**データベースに格納されます。  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|データベースメンテナンスプランの ID。|  
|**plan_name**|**sysname**|データベース メンテナンス プランの名前。|  
|**date_created**|**datetime**|データベース メンテナンス プランが作成された日付。|  
|**責任**|**sysname**|データベースメンテナンスプランの所有者。|  
|**max_history_rows**|**int**|システム テーブル内で、データベース メンテナンス プランの履歴の記録用に割り当てられる行数の最大値。|  
|**remote_history_server**|**sysname**|履歴レポートが書き込まれるリモートサーバーの名前。|  
|**max_remote_history_rows**|**int**|履歴レポートが書き込まれるリモートサーバー上のシステムテーブルに割り当てられる最大行数。|  
|**user_defined_1**|**int**|既定値は NULL です。|  
|**user_defined_2**|**nvarchar (100)**|既定値は NULL です。|  
|**user_defined_3**|**datetime**|既定値は NULL です。|  
|**user_defined_4**|**uniqueidentifier**|既定値は NULL です。|  
|**log_shipping**|**bit**|ログ配布の状態。<br /><br /> **0** = 無効**1** = 有効|  
  
  
