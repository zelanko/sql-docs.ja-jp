---
title: ジョブの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 986e38ef42fe1af2aba8ba1625225a336f29158d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63162465"
---
# <a name="create-jobs"></a>ジョブの作成
  ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって順番に実行される一連の操作です。 ジョブは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、コマンド プロンプト アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services コマンドおよびクエリ、レプリケーション タスクの実行など、広範な操作を実行できます。 ジョブは、反復的なタスクやスケジュール可能なタスクを実行でき、警告を発生させてジョブのステータスをユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理が非常に簡単になります。  
  
 ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。 **sysadmin** ロールのメンバーは、別のユーザーにジョブの所有権を割り当てることができ、そのユーザーはジョブの所有者とは無関係にジョブを実行できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 ジョブは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスまたは企業全体の複数のインスタンスで実行するように記述できます。 複数のサーバーでジョブを実行するには、最低 1 つのマスター サーバーと 1 つ以上のターゲット サーバーをセットアップする必要があります。 マスター サーバーとターゲット サーバーの詳細については、「[エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md)」をご覧ください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントにより、ジョブとジョブ ステップの情報がジョブ履歴に記録されます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**説明**|**トピック**|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを作成する方法について説明します。|[ジョブの作成](create-a-job.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブの所有権を他のユーザーに再割り当てする方法について説明します。|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ履歴ログをセットアップする方法について説明します。|[Set Up the Job History Log](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>参照  
 [ジョブステップの管理](manage-job-steps.md)   
 [企業全体の管理の自動化](automated-administration-across-an-enterprise.md)   
 [スケジュールを作成してジョブにアタッチする](create-and-attach-schedules-to-jobs.md)   
 [ジョブの実行](run-jobs.md)   
 [ジョブの表示または変更](view-or-modify-jobs.md)  
  
  
