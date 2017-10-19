---
title: "ジョブ カテゴリのメンバーシップを変更する | Microsoft Docs"
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
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 60a46ce2fd6a12645870d9a025b82e4ab23762a9
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="change-the-membership-of-a-job-category"></a>Change the Membership of a Job Category
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql_md.md)]でジョブ カテゴリのメンバーシップを変更する方法について説明します。  
  
ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 ジョブ カテゴリは、独自に作成できます。 さらに、ジョブ カテゴリの Microsoft SQL Server エージェント ジョブのメンバーシップを変更することもできます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ カテゴリのメンバーシップを変更する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>ジョブ カテゴリのメンバーシップを変更するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを編集するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]**をクリックします。  
  
4.  [**ジョブ カテゴリの管理***server_name*] ダイアログ ボックスで、編集するジョブ カテゴリを選択し、**[ジョブの表示]** をクリックします。  
  
5.  **[すべてのジョブを表示]** チェック ボックスをオンにします。  
  
6.  カテゴリにジョブを追加するには、メイン グリッドで、ジョブに対応する **[選択]** 列のチェック ボックスをオンにします。 カテゴリからジョブを削除するには、チェック ボックスをオフにします。 完了したら、 **[OK]**をクリックします。  
  
7.  [**ジョブ カテゴリの管理***server_name*] ダイアログ ボックスを閉じます。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>ジョブ カテゴリのメンバーシップを変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
詳細については、「 [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623)」を参照してください。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ カテゴリのメンバーシップを変更するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **JobCategory** クラスを使用します。  
  

