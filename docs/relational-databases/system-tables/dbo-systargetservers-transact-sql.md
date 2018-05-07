---
title: dbo.systargetservers (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f425fb530d10abb4a3285f664b8bed8b083197b8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マルチサーバー操作ドメインに現在参加している対象サーバーを記録します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|サーバー id。|  
|**server_name**|**sysname**|サーバー名。|  
|**location**|**nvarchar(200)**|指定した対象サーバーの場所。|  
|**time_zone_adjustment**|**int**|グリニッジ標準時 (GMT) との時差 (時間数単位)。|  
|**enlist_date**|**datetime**|指定した対象サーバーが参加した日付と時刻。|  
|**last_poll_date**|**datetime**|日付と時刻の指定した対象サーバーではマルチ サーバーの最後を呼び出した**sysdownloadlist**システム テーブルのジョブを実行します。|  
|**ステータス**|**int**|対象サーバーの状態。<br /><br /> **1** = 標準<br /><br /> **2** = 保留中の再同期<br /><br /> **4** = オフラインの疑いがあります。|  
|**local_time_at_last_poll**|**datetime**|ジョブ操作について、対象サーバーがポーリングされた前回の日付と時刻。|  
|**enlisted_by_nt_user**|**nvarchar(100)**|実行しているユーザーのユーザー名**sp_msx_enlist**対象サーバーにします。|  
|**poll_internal**|**int**|対象サーバーが、新規のダウンロード命令についてマスター サーバーをポーリングするまでに経過した秒数。|  
  
  
