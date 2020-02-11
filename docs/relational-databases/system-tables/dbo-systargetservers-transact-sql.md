---
title: systargetservers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c6304b108d75d6fe9ba00ccccdae322bf7cedde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68095839"
---
# <a name="dbosystargetservers-transact-sql"></a>systargetservers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マルチサーバー操作ドメインに現在参加しているターゲット サーバーを記録します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|サーバー ID。|  
|**server_name**|**sysname**|サーバー名。|  
|**設置**|**nvarchar(200)**|指定したターゲット サーバーの場所。|  
|**time_zone_adjustment**|**int**|グリニッジ標準時 (GMT) との時差 (時間数単位)。|  
|**enlist_date**|**DATETIME**|指定したターゲット サーバーが参加した日付と時刻。|  
|**last_poll_date**|**DATETIME**|ジョブを実行するために、指定された対象サーバーがマルチサーバーの**sysdownloadlist**システムテーブルを最後に呼び出した日時。|  
|**オンライン**|**int**|対象サーバーの状態:<br /><br /> **1** = 通常<br /><br /> **2** = 再同期の保留中<br /><br /> **4** = オフラインの疑いあり|  
|**local_time_at_last_poll**|**DATETIME**|対象サーバーがジョブ操作のために最後にポーリングされた日付と時刻。|  
|**enlisted_by_nt_user**|**nvarchar (100)**|対象サーバーで**sp_msx_enlist**を実行しているユーザーのユーザー名。|  
|**poll_internal**|**int**|対象サーバーがマスターサーバーをポーリングして新しいダウンロード命令を行うまでの秒数。|  
  
  
