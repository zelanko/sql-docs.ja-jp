---
title: "ジョブ カテゴリの作成 | Microsoft Docs"
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
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 960865a8bb263a2089dc51a75304e3e6e40b85bf
ms.lasthandoff: 04/11/2017

---
# <a name="create-a-job-category"></a>ジョブ カテゴリの作成
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、 [!INCLUDE[tsql](../../includes/tsql_md.md)] 、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 管理オブジェクトを使用して、ジョブ カテゴリを作成する方法について説明します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントには、ジョブを割り当てることができる組み込みのジョブ カテゴリが用意されています。また、ジョブ カテゴリを作成してジョブを割り当てることができます。 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。 ジョブ カテゴリは、独自に作成することもできます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **ジョブ カテゴリを作成する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
マルチサーバー カテゴリは、マスター サーバー上だけに存在します。 マスター サーバー上で使用できるのは、**[未カテゴリ化 (マルチサーバー)]**という既定のジョブ カテゴリだけです。 マルチサーバー ジョブがダウンロードされると、対象サーバー上ではそのカテゴリが **[MSX からのジョブ]** に変更されます。  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-create-a-job-category"></a>ジョブ カテゴリを作成するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを作成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]**をクリックします。  
  
4.  **&lt;server_name&gt;**** ダイアログ ボックスで、 **追加**をクリックします。  
  
5.  新しいダイアログ ボックスで、 **[名前]** ボックスに新しいジョブ カテゴリの名前を入力します。  
  
6.  **[すべてのジョブを表示]** チェック ボックスをオンにします。 ジョブに対応するチェック ボックスをオンにして、新しいカテゴリのジョブを 1 つ以上選択します。  
  
7.  **[OK]**をクリックします。  
  
8.  **&lt;server_name&gt;**** ダイアログ ボックスで、 **最新の情報に更新** をクリックして、新しいジョブ カテゴリをアクティブにします。 すべての設定が適切であることを確認したら、このダイアログ ボックスを閉じます。  
  
これらのダイアログ ボックスの詳細については、「 [[ジョブ カテゴリ] - [ジョブ カテゴリの管理]](../../ssms/agent/job-categories-manage-job-categories.md) 」および「 [ジョブ カテゴリのプロパティ - [新しいジョブ カテゴリ]](../../ssms/agent/job-categories-properties-new-job-category.md)」をご覧ください。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-create-a-job-category"></a>ジョブ カテゴリを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
詳細については、「 [sp_add_category (Transact-SQL)](http://msdn.microsoft.com/en-us/6cca32cd-d941-4378-aed6-a7c90cb7520a)」をご覧ください。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ カテゴリを作成するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **JobCategory** クラスを呼び出します。 コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](http://msdn.microsoft.com/en-us/900242ad-d6a2-48e9-8a1b-f0eea4413c16)」を参照してください。  
  

