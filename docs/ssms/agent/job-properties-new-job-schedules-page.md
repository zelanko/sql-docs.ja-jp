---
title: ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e97c52943b2f6d6092c40d121ee88ea8d6b814c8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38064809"
---
# <a name="job-properties---new-job-schedules-page"></a>ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 
  [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のエージェント ジョブのスケジュールを表示したり、調整したりできます。  
  
## <a name="options"></a>[変数]  
**[スケジュールの一覧]**  
このジョブのスケジュールの一覧を表示します。  
  
**[新規作成]**  
新しいスケジュールを作成します。 スケジュールを作成すると、そのスケジュールはジョブに追加されます。  
  
**[選択]**  
既存のスケジュールを選択します。 ジョブとスケジュールの所有者は同じである必要があるため、このオプションを使用しても自分が所有するスケジュールしか選択できません。  
  
**[編集]**  
選択したスケジュールを編集し、ジョブのスケジュールのプロパティを変更します。  
  
**[削除]**  
選択されているスケジュールをジョブから削除します。 このスケジュールを使用するジョブが他にない場合、スケジュールはデータベースから削除されます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
  
