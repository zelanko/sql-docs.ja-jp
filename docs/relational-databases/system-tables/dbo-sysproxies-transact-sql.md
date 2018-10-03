---
title: dbo.sysproxies (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a37300ad1bf16ac76fbcbd0c6e77870077f7f631
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846410"
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  属性を定義、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ アカウント。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|プロキシ アカウントの ID。|  
|**name**|**sysname**|プロキシ アカウントの名前。|  
|**credential_id**|**int**|プロキシ アカウントで使用される資格情報の ID。|  
|**enabled**|**tinyint**|プロキシ アカウントの状態。<br /><br /> **0** = 無効になっています。 **1** = 有効にします。|  
|**description**|**nvarchar(512)**|プロキシ アカウントを作成したときにユーザーが入力した説明。|  
|**user_sid**|**varbinary(85)**|Microsoft Windows *security_identifier*ユーザーまたはグループがプロキシ資格情報に関連付けられているのです。|  
|**credential_date_created**|**datetime**|資格情報を作成した日付と時刻。|  
  
## <a name="remarks"></a>コメント  
 メンバーのみ、 **sysadmin**固定サーバー ロールがアクセスできる、 **sysproxies**テーブル。  
  
## <a name="see-also"></a>参照  
 [dbo.sysproxylogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
