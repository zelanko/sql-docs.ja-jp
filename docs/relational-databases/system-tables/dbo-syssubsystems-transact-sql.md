---
title: dbo. syssubsystems システム (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff13af62635273773551ded6df3175bc80157a45
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806603"
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo. syssubsystems システム (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用可能なすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのプロキシ サブシステムに関する情報を格納します。 **Syssubsystems システム**テーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|サブシステムの ID。|  
|**サブ**|**nvarchar(40)**|サブシステムの名前。|  
|**description_id**|**int**|サブシステムの説明を含む、 **sys. messages**カタログビュー内の行のメッセージ ID。|  
|**subsystem_dll**|**nvarchar(255)**|サブシステム DLL の場所。|  
|**agent_exe**|**nvarchar(255)**|サブシステムを使用する実行可能ファイルへの完全パスです。|  
|**start_entry_point**|**nvarchar(30)**|サブシステムが初期化されるときに呼び出される関数。|  
|**event_entry_point**|**nvarchar(30)**|サブシステムステップが実行されるときに呼び出される関数です。|  
|**stop_entry_point**|**nvarchar(30)**|サブシステムが実行を終了するときに呼び出される関数。|  
|**max_worker_threads**|**int**|サブシステムの同時ステップの最大数。|  
  
## <a name="remarks"></a>Remarks  
 このテーブルにアクセスできるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [dbo. sysproxysubsystem &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo .SQL プロキシ &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
