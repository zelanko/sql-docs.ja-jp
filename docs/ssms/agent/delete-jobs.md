---
title: "ジョブの削除 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f5e08e59ade5619787882695f6183bf1526dc557
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="delete-jobs"></a>ジョブの削除
ジョブとは、SQL Server エージェントによって順番に実行される一連の操作です。 既定では、ジョブは実行の終了時に削除されません。 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブは、ジョブの成否にかかわらず削除できます。 ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを構成することもできます。  
  
既定では、 **sp_delete_job (Transact-SQL)** システム ストアド プロシージャを実行してジョブを削除できるのは、 [sysadmin](http://msdn.microsoft.com/en-us/b85db6e4-623c-41f1-9643-07e5ea38db09) 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
**sp_delete_job** を実行して任意のジョブを削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 **sysadmin** 固定サーバー ロールのメンバーでないユーザーは、自分が所有するジョブのみを削除できます。  
  
## <a name="related-tasks"></a>関連タスク  
  
|||  
|-|-|  
|**Description**|**トピック**|  
|1 つまたは複数の [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブを削除する方法について説明します。|[1 つまたは複数のジョブの削除](../../ssms/agent/delete-one-or-more-jobs.md)|  
|ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを構成する方法について説明します。|[Automatically Delete a Job](../../ssms/agent/automatically-delete-a-job.md)|  
  

