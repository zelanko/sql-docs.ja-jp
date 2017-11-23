---
title: "dbo.sysproxies (TRANSACT-SQL) |Microsoft ドキュメント"
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
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs: TSQL
helpviewer_keywords: sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b28fdf8c7cee40fa088ee0d7634e4ea17aba91c8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  属性を定義、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ アカウント。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|プロキシ アカウントの ID。|  
|**name**|**sysname**|プロキシ アカウントの名前。|  
|**credential_id**|**int**|プロキシ アカウントで使用される資格情報の ID。|  
|**有効になっています。**|**tinyint**|プロキシ アカウントの状態。<br /><br /> **0**無効になっています。 **1** = 有効にします。|  
|**説明**|**nvarchar(512)**|プロキシ アカウントを作成したときにユーザーが入力した説明。|  
|**user_sid**|**varbinary (85)**|Microsoft Windows *security_identifier*ユーザーまたはグループがプロキシ資格情報に関連付けられているのです。|  
|**credential_date_created**|**datetime**|資格情報を作成した日付と時刻。|  
  
## <a name="remarks"></a>解説  
 メンバーにのみ、 **sysadmin**固定サーバー ロールがアクセスできる、 **sysproxies**テーブル。  
  
## <a name="see-also"></a>参照  
 [dbo.sysproxylogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
