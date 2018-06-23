---
title: ジョブの所有権を他のユーザーに割り当てる | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], owners
- owners [SQL Server], jobs
- SQL Server Agent jobs, owners
ms.assetid: 2ded5e9c-4251-4fb1-a047-99f13d150b61
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7e2190d04d8a03a2f6c46ca8fbd193555cee221f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175074"
---
# <a name="give-others-ownership-of-a-job"></a>Give Others Ownership of a Job
  このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブの所有権を他のユーザーに割り当てる方法を説明します。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Restrictions)、 [セキュリティ](#Security)  
  
-   **ジョブの所有権を他のユーザーに割り当てる方法:**  
  
     [SQL Server Management Studio](#SSMSProc2)  
  
     [Transact-SQL](#TsqlProc2)  
  
     [SQL Server 管理オブジェクト](#SMOProc2)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 ジョブを作成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールか **sysadmin** 固定サーバー ロールのメンバーである必要があります。 ジョブの編集は、ジョブの所有者または **sysadmin** ロールのメンバーのみが行うことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント固定データベース ロールの詳細については、「 [SQL Server エージェントの固定データベース ロール](sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 ジョブの所有者を変更するには、システム管理者でなければなりません。  
  
 別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティを確保するため、ジョブの所有者または **sysadmin** ロールのメンバーだけがジョブの定義を変更できます。 **sysadmin** 固定サーバー ロールのメンバーのみが別のユーザーにジョブの所有権を割り当てることができ、ジョブの所有者とは無関係にジョブを実行できます。  
  
> [!NOTE]  
>  ジョブの所有権を **sysadmin** 固定サーバー ロールのメンバーでないユーザーに変更し、そのジョブがプロキシ アカウントを必要とするジョブ ステップを実行する ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの実行など) 場合は、ユーザーがそのプロキシ アカウントにアクセスできることを確認してください。アクセスできない場合、ジョブは失敗します。  
  
####  <a name="Permissions"></a> Permissions  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMSProc2"></a> SQL Server Management Studio の使用  
 **ジョブの所有権を他のユーザーに割り当てるには**  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、ジョブを右クリックして **[プロパティ]** をクリックします。  
  
3.  **[所有者]** ボックスの一覧で、ログインを選択します。 ジョブの所有者を変更するには、システム管理者でなければなりません。  
  
     別のログインにジョブを割り当てた場合に、新しい所有者がそのジョブを正常に実行できる十分な権限を持っていないこともあります。  
  
##  <a name="TsqlProc2"></a> Transact-SQL の使用  
 **ジョブの所有権を他のユーザーに割り当てるには**  
  
1.  オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  使用して、次のステートメントを入力してクエリ ウィンドウで、 [sp_manage_jobs_by_login &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-manage-jobs-by-login-transact-sql)システム ストアド プロシージャです。 次の例では、 `danw` からのすべてのジョブを `françoisa`に再割り当てします。  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_manage_jobs_by_login  
        @action = N'REASSIGN',  
        @current_owner_login_name = N'danw',  
        @new_owner_login_name = N'françoisa' ;  
    GO  
    ```  
  
##  <a name="SMOProc2"></a> SQL Server 管理オブジェクトを使用します。  
 **ジョブの所有権を他のユーザーに割り当てるには**  
  
1.  呼び出す、 `Job` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラスです。 コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ジョブの実装](implement-jobs.md)   
 [ジョブの作成](create-jobs.md)  
  
  
