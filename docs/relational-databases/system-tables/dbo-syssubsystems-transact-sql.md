---
title: "dbo.syssubsystems (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs: TSQL
helpviewer_keywords: syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac5beab5a0c45bc14155d241af7884274a4606ba
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用可能なすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのプロキシ サブシステムに関する情報を格納します。 **Syssubsystems**でテーブルが格納されている、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|サブシステムの ID。|  
|**サブシステム**|**nvarchar (40)**|サブシステムの名前。|  
|**description_id**|**int**|メッセージ内の行の ID、 **sys.messages**をサブシステムの説明を格納するカタログ ビューです。|  
|**よう**|**nvarchar (255)**|サブシステム DLL の場所。|  
|**agent_exe**|**nvarchar (255)**|サブシステムを使用する実行可能ファイルのフル パス。|  
|**start_entry_point**|**nvarchar (30)**|サブシステムが初期化されるときに呼び出される関数。|  
|**event_entry_point**|**nvarchar (30)**|サブシステム ステップが実行されるときに呼び出される関数。|  
|**stop_entry_point**|**nvarchar (30)**|サブシステムが実行を終了するときに呼び出される関数。|  
|**max_worker_threads**|**int**|サブシステムの同時ステップの最大数。|  
  
## <a name="remarks"></a>解説  
 メンバーにのみ、 **sysadmin**固定サーバー ロールがこのテーブルにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [dbo.sysproxysubsystem &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysproxies &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40; です。TRANSACT-SQL と&#41; です。](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
