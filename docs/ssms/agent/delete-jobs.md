---
title: ジョブの削除
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 038ce655c054a52388efbe6853c28c95edb57895
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87237871"
---
# <a name="delete-jobs"></a>ジョブの削除
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

ジョブとは、SQL Server エージェントによって順番に実行される一連の操作です。 既定では、ジョブは実行の終了時に削除されません。 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、ジョブの成否にかかわらず削除できます。 ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成することもできます。  
  
既定では、 **sp_delete_job (Transact-SQL)** システム ストアド プロシージャを実行してジョブを削除できるのは、 [sysadmin](https://msdn.microsoft.com/b85db6e4-623c-41f1-9643-07e5ea38db09) 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
**sp_delete_job** を実行して任意のジョブを削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 **sysadmin** 固定サーバー ロールのメンバーでないユーザーは、自分が所有するジョブのみを削除できます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|説明|トピック|  
|-|-|   
|1 つまたは複数の [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを削除する方法について説明します。|[1 つまたは複数のジョブの削除](../../ssms/agent/delete-one-or-more-jobs.md)|  
|ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成する方法について説明します。|[Automatically Delete a Job](../../ssms/agent/automatically-delete-a-job.md)|  
  
