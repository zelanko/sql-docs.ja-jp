---
title: "dbo.sysproxylogin (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs: TSQL
helpviewer_keywords: sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5301ed0231793f50be14f536cd36ff2f5010df78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各 SQL Server エージェント プロキシ アカウントに関連付けられている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログインを記録します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシ アカウントの ID。 この値に対応、 **proxy_id**内の列、 **sysproxies**テーブル。|  
|**sid**|**varbinary (85)**|Microsoft Windows *security_identifier* SQL Server ログインします。|  
|**principal_id**|**int**|指定したサブシステム ステップのプロキシ アカウントを使用する権限を持つユーザーまたはグループの ID。|  
|**フラグ**|**int**|ログインの種類です。<br /><br /> **0** = Windows ユーザーまたはグループ、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定システム ロール<br /><br /> **2** = **msdb**データベース ロール|  
  
## <a name="remarks"></a>解説  
 メンバーにのみ、 **sysadmin**固定サーバー ロールがこのテーブルにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [dbo.sysproxies &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
