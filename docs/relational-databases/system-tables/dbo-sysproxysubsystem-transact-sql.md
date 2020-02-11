---
title: dbo. sysproxysubsystem (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxysubsystem_TSQL
- dbo.sysproxysubsystem
- sysproxysubsystem_TSQL
- sysproxysubsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxysubsystem system table
ms.assetid: 6d7713f5-1253-4a19-b1fb-635c377c95c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3a140a4cf1c82deda3b9d6a15b419b33b411974
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097017"
---
# <a name="dbosysproxysubsystem-transact-sql"></a>dbo. sysproxysubsystem (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各プロキシ アカウントで、どの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサブシステムが使用されているかを記録します。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|サブシステムの ID。 この値は、 **syssubsystems システム**テーブルの**subsystem_id**列に対応しています。|  
|**proxy_id**|**int**|プロキシアカウントの ID。 この値は、 **sysproxies**テーブルの**proxy_id**列に対応しています。|  
  
## <a name="remarks"></a>解説  
 このテーブルにアクセスできるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [dbo. syssubsystems システム &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)   
 [dbo .SQL プロキシ &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
