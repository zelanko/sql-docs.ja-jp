---
title: dbo.systargetservers (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: c8297c02d66671ea41b8a2dae4462514d4ef2fe4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783520"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マルチサーバー操作ドメインに現在参加しているターゲット サーバーを記録します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|サーバー id。|  
|**server_name**|**sysname**|サーバー名。|  
|**location**|**nvarchar(200)**|指定したターゲット サーバーの場所。|  
|**time_zone_adjustment**|**int**|グリニッジ標準時 (GMT) との時差 (時間数単位)。|  
|**enlist_date**|**datetime**|指定したターゲット サーバーが参加した日付と時刻。|  
|**last_poll_date**|**datetime**|日付と時刻の指定した対象サーバーでは、マルチ サーバーの最後を呼び出した**sysdownloadlist**のジョブを実行するシステム テーブル。|  
|**status**|**int**|ターゲット サーバーの状態。<br /><br /> **1** = 標準<br /><br /> **2** = 保留中の再同期<br /><br /> **4** = オフラインの疑い|  
|**local_time_at_last_poll**|**datetime**|ジョブ操作について、ターゲット サーバーがポーリングされた前回の日付と時刻。|  
|**enlisted_by_nt_user**|**nvarchar(100)**|実行しているユーザーのユーザー名**sp_msx_enlist**ターゲット サーバー上。|  
|**poll_internal**|**int**|ターゲット サーバーが、新規のダウンロード命令についてマスター サーバーをポーリングするまでに経過した秒数。|  
  
  
