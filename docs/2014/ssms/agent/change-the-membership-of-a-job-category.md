---
title: ジョブ カテゴリのメンバーシップを変更する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3e8497e4f5a8b5e74b7bb0b5d9c01cef78e275d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017170"
---
# <a name="change-the-membership-of-a-job-category"></a>Change the Membership of a Job Category
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でジョブ カテゴリのメンバーシップを変更する方法について説明します。  
  
 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 ジョブ カテゴリは、独自に作成できます。 さらに、ジョブ カテゴリの Microsoft SQL Server エージェント ジョブのメンバーシップを変更することもできます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ジョブ カテゴリのメンバーシップを変更する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>ジョブ カテゴリのメンバーシップを変更するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを編集するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。  
  
4.  **server_name**__ ダイアログ ボックスで、編集するジョブ カテゴリを選択し、 **ジョブの表示**をクリックします。  
  
5.  **[すべてのジョブを表示]** チェック ボックスをオンにします。  
  
6.  カテゴリにジョブを追加するには、メイン グリッドで、ジョブに対応する **[選択]** 列のチェック ボックスをオンにします。 カテゴリからジョブを削除するには、チェック ボックスをオフにします。 完了したら、 **[OK]** をクリックします。  
  
7.  **&lt;server_name&gt;**__ ダイアログ ボックスを閉じます。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>ジョブ カテゴリのメンバーシップを変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_update_job &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)します。  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブ カテゴリのメンバーシップを変更するには**  
  
 使用して、 `JobCategory` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス。  
  
  
