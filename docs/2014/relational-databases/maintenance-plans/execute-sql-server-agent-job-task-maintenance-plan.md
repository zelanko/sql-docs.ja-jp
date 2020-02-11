---
title: '[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 33f037f4d82cbf5bbdebde01a5c4492128ecc8ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206023"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a>[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン)
  [ **SQL Server エージェントジョブの実行タスク**] ダイアログを使用すると、メンテナンスプラン内で Microsoft SQL Server エージェントジョブを実行できます。 選択されている接続に SQL Server エージェント ジョブが存在しない場合は、このオプションを利用できません。  
  
 このタスクでは、 **.sp_start_job** ステートメントを使用します。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **接続**  
 このタスクを実行するときに使用するサーバー接続を選択します。  
  
 **[新規作成]**  
 このタスクを実行するときに使用する新しいサーバー接続を作成します。 
  **[新しい接続]** ダイアログ ボックスについては、後で説明します。  
  
 **利用可能な SQL エージェントジョブ**  
 実行するジョブを選択します。 グリッドには、ジョブを識別するための **[ジョブ名]** と **[説明]** があります。  
  
 **T-sql の表示**  
 選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。  
  
> [!NOTE]  
>  影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。  
  
## <a name="new-connection-dialog-box"></a>[新しい接続] ダイアログ ボックス  
 **接続名**  
 新しい接続の名前を入力します。  
  
 **サーバー名の選択または入力**  
 このタスクを実行するときに接続するサーバーを選択します。  
  
 **[更新]**  
 使用できるサーバーの一覧を表示します。  
  
 **サーバーにログオンするための情報を入力します**  
 サーバーの認証情報を指定します。  
  
 **Windows 統合セキュリティを使用する**  
 Microsoft Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。  
  
 **特定のユーザー名とパスワードを使用する**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。 このオプションは利用できません。  
  
 **ユーザー名**  
 認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。 このオプションは利用できません。  
  
 **パスワード**  
 認証に使用するパスワードを指定します。 このオプションは利用できません。  
  
## <a name="see-also"></a>参照  
 [sp_add_job &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [ジョブを作成する](../../ssms/agent/create-a-job.md)   
 [sp_start_job &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)  
  
  
