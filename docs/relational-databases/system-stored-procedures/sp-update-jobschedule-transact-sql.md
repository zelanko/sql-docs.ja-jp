---
title: sp_update_jobschedule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_jobschedule_TSQL
- sp_update_jobschedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobschedule
ms.assetid: 4df02594-4cd1-49a9-8d97-37c44e4d5423
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 21a93aac42dcbbf29d3e5a4a3bb2d4ab2196380c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spupdatejobschedule-transact-sql"></a>sp_update_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したジョブのスケジュール設定を変更します。  
  
 **sp_update_jobschedule**は旧バージョンとの互換性を保つのために提供します。  
  
> [!IMPORTANT]  
>  Microsoft SQL Server の以前のバージョンで使用される構文の詳細については、TRANSACT-SQL Referencefor Microsoft SQL Server 2000 を参照してください。*です。*  
  
## <a name="remarks"></a>解説  
 ジョブ スケジュールはジョブとは別々に管理できます。 更新するには、スケジュールを使用して**sp_update_schedule**です。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバーだけ**sysadmin**を他のユーザーによって所有されているジョブのスケジュールを更新するこのストアド プロシージャを使用することができます。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_update_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)  
  
  
