---
title: '[ジョブのプロパティ] - [新しいジョブ]([通知] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47bbd070ce658140270adb6bbfbd63e71c22fc6c
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="job-properties---new-job-notifications-page"></a>[ジョブのプロパティ] - [新しいジョブ] ([通知] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、ジョブの完了時に [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが実行するアクションを設定します。  
  
## <a name="options"></a>および  
**[電子メール]**  
このオプションを選択すると、ジョブの完了時に電子メールが送信されます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]**の中から選択します。  
  
**ページ**  
このオプションを選択すると、ジョブの完了時にオペレーターのポケットベルに電子メールが送信されます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]**の中から指定します。  
  
**[Net Send]**  
このオプションを選択すると、ジョブの完了時に Net Send を使用してオペレーターに通知が送られます。 このオプションを選択した後、通知先のオペレーターを指定し、通知を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]**の中から指定します。  
  
**[Windows アプリケーション イベント ログに書き込む]**  
このオプションを選択すると、ジョブの完了時にアプリケーション イベント ログにエントリが書き込まれます。 このオプションを選択した後、エントリの書き込みを実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]**の中から選択します。  
  
**[自動的にジョブを削除]**  
このオプションを選択すると、ジョブの完了時にジョブが削除されます。 このオプションを選択した後、ジョブの削除を実行する条件を **[ジョブ成功時]**、 **[ジョブ失敗時]**、 **[ジョブ完了時]**の中から選択します。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
[データベース メールを使用するように SQL Server エージェント メールを構成する方法 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  
