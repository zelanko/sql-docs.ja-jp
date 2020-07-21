---
title: ジョブ カテゴリの作成 | Microsoft Docs
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
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f6daeeca6253861e8a9dcbb72faa2bd55eb2761
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056639"
---
# <a name="create-a-job-category"></a>ジョブ カテゴリの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクトを使用して、ジョブ カテゴリを作成する方法について説明します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントには、ジョブを割り当てることができる組み込みのジョブ カテゴリが用意されています。また、ジョブ カテゴリを作成してジョブを割り当てることができます。 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。 ジョブ カテゴリは、独自に作成することもできます。  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 マルチサーバー カテゴリは、マスター サーバー上だけに存在します。 マスター サーバー上で使用できるのは、**[未カテゴリ化 (マルチサーバー)]** という既定のジョブ カテゴリだけです。 マルチサーバー ジョブがダウンロードされると、ターゲット サーバー上ではそのカテゴリが **[MSX からのジョブ]** に変更されます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-job-category"></a>ジョブ カテゴリを作成するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを作成するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。  
  
4.  [**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、[**追加**] をクリックします。  
  
5.  新しいダイアログ ボックスで、 **[名前]** ボックスに新しいジョブ カテゴリの名前を入力します。  
  
6.  **[すべてのジョブを表示]** チェック ボックスをオンにします。 ジョブに対応するチェック ボックスをオンにして、新しいカテゴリのジョブを 1 つ以上選択します。  
  
7.  **[OK]** をクリックします。  
  
8.  [**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、[最新の状態に**更新**] をクリックして、新しいジョブカテゴリが [アクティブ] になっていることを確認します。 すべての設定が適切であることを確認したら、このダイアログ ボックスを閉じます。  
  
 これらのダイアログボックスの詳細については、「[ジョブカテゴリ:](job-categories-manage-job-categories.md)ジョブカテゴリの管理」および「ジョブカテゴリのプロパティ」、[および「新しいジョブカテゴリ](job-categories-properties-new-job-category.md)」を参照してください。  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-job-category"></a>ジョブ カテゴリを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 詳細については、「 [sp_add_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql)」を参照してください。  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 管理オブジェクトの使用  
 **ジョブ カテゴリを作成するには**  
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `JobCategory` クラスを呼び出します。 コード例については、「 [SQL Server エージェントでの自動管理タスクのスケジュール設定](sql-server-agent.md)」を参照してください。  
