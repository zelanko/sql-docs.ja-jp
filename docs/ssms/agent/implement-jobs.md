---
title: "ジョブの実装 | Microsoft Docs"
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
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 30b61e4aa32828763d4531c53cb7f308a926798b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="implement-jobs"></a>ジョブの実装
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブを使用すると、定型的な管理作業を自動化して定期的に実行し、管理を効率化できます。  
  
ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって順番に実行される一連の操作です。 ジョブで実行できる操作は多岐にわたり、 [!INCLUDE[tsql](../../includes/tsql_md.md)] スクリプト、コマンド ライン アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services のコマンドおよびクエリ、レプリケーション タスクなどを実行できます。 ジョブでは、繰り返し行う作業や、スケジュールに設定できる作業を実行できます。また、警告を生成してジョブの状態をユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の管理を大幅に簡素化できます。  
  
ジョブは手動で実行することも、スケジュールや警告に応じて実行されるように構成することもできます。  
  
## <a name="related-tasks"></a>関連タスク  
  
|||  
|-|-|  
|**Description**|**トピック**|  
|ジョブの作成と所有権の割り当てについて説明します。|[ジョブの作成](../../ssms/agent/create-jobs.md)|  
|ジョブをカテゴリごとに編成するための情報を記載しています。|[ジョブの整理](../../ssms/agent/organize-jobs.md)|  
|ユーザーが作成できるさまざまな種類のジョブ ステップおよびそれらの管理方法について説明します。|[ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)|  
|ジョブの実行開始時刻および実行頻度を定義する方法について説明します。|[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)|  
|(スケジュールを設定せずに) ジョブを手動で実行するための情報を記載しています。|[ジョブの実行](../../ssms/agent/run-jobs.md)|  
|ジョブに応答できるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを構成する方法について説明します。 たとえば、ジョブが完了したら管理者に通知するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを構成できます。|[ジョブ応答の指定](../../ssms/agent/specify-job-responses.md)|  
|既存のジョブおよびその実行履歴を参照する方法と、既存のジョブを変更する方法について説明します。|[ジョブの表示または変更](../../ssms/agent/view-or-modify-jobs.md)|  
|ジョブを削除する方法について説明します。|[ジョブの削除](../../ssms/agent/delete-jobs.md)|  
  
## <a name="see-also"></a>参照  
[SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md)  
  

