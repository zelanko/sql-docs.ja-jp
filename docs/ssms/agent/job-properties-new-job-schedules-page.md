---
title: ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cd9d5a33ff433204cd066eef3d17f9ec7dfd10ff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782996"
---
# <a name="job-properties---new-job-schedules-page"></a>ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエージェント ジョブのスケジュールを表示したり、調整したりできます。  
  
## <a name="options"></a>オプション  
**[スケジュールの一覧]**  
このジョブのスケジュールの一覧を表示します。  
  
**[新規作成]**  
新しいスケジュールを作成します。 スケジュールを作成すると、そのスケジュールはジョブに追加されます。  
  
**[選択]**  
既存のスケジュールを選択します。 ジョブとスケジュールの所有者は同じである必要があるため、このオプションを使用しても自分が所有するスケジュールしか選択できません。  
  
**[編集]**  
選択したスケジュールを編集し、ジョブのスケジュールのプロパティを変更します。  
  
**Remove**  
選択されているスケジュールをジョブから削除します。 このスケジュールを使用するジョブが他にない場合、スケジュールはデータベースから削除されます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
  
