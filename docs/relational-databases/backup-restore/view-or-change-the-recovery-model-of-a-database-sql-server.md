---
title: "データベースの復旧モデルの表示または変更 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベースのバックアップ [SQL Server], 復旧モデル"
  - "復旧 [SQL Server], 復旧モデル"
  - "データベースのバックアップ [SQL Server], 復旧モデル"
  - "復旧モデル [SQL Server], 切り替え"
  - "復旧モデル [SQL Server], 表示"
  - "データベースの復元 [SQL Server], 復旧モデル"
  - "データベースの復旧モデルの変更"
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# データベースの復旧モデルの表示または変更 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を利用してデータベースを表示または変更する方法について説明します。 
  
  *復旧モデル*は、トランザクションをログに記録する方法、トランザクション ログのバックアップを必須 (および可能) にするかどうか、利用できる復元操作の種類などを制御するデータベース プロパティです。 復旧モデルの種類は、単純、完全、および一括ログの 3 種類です。 通常、データベースには完全復旧モデルまたは単純復旧モデルが使用されます。 データベースは、任意の時点で別の復旧モデルに切り替えることができます。 **model** データベースは、新しいデータベースの既定の復旧モデルを設定します。  
  
  [復旧モデル](https://msdn.microsoft.com/library/ms189275.aspx)についての詳細な説明は、[MSSQLTips!](https://www.mssqltips.com/) の提供する「[SQL Server Recovery Models](https://www.mssqltips.com/sqlservertutorial/2/sql-server-recovery-models/)」 (SQL Server 復旧モデル) を参照してください。
  
  
##  <a name="BeforeYouBegin"></a> アンインストールの準備  
  

-   [完全復旧モデルまたは一括ログ復旧モデル](https://msdn.microsoft.com/library/ms189275.aspx)から切り替える**前**に、[トランザクション ログをバックアップ](https://msdn.microsoft.com/library/ms179478.aspx)してください。  
  
-   一括ログ復旧モデルでは特定の時点に復旧できません。 一括ログ復旧モデルでトランザクション ログの復元を必要とするトランザクションを実行すると、データが失われる可能性があります。 障害復旧シナリオでデータをより確実に復旧するには、次の条件下でのみ一括ログ復旧モデルに切り替えることをお勧めします。  
  
    -   ユーザーが現在データベースで許可されていない場合。  
  
    -   一括処理中に行われたすべての変更が、ログ バックアップを行うかどうかに関係なく復旧可能な場合 (一括処理の再実行など)。  
  
     この 2 つの条件を満たす場合は、一括ログ復旧モデルでバックアップされたトランザクション ログの復元中に、データが失われることはありません。  
  
**メモ** 一括操作中に完全復旧モデルに切り替える場合は、一括操作のログ記録が最小ログ記録から完全ログ記録に変わり、また、その逆も同様です。  
  
###  <a name="Security"></a> 必要な権限  
   データベースに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### 復旧モデルを表示または変更するには  
  
1.  適切な [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスへの接続後、オブジェクト エクスプローラーでサーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[データベース]**を展開します。さらに、そのデータベースに応じて、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。  
  
3.  データベースを右クリックし、**[プロパティ]** をクリックすると、**[データベースのプロパティ]** ダイアログ ボックスが開きます。  
  
4.  **[ページの選択]** ペインの **[オプション]**をクリックします。  
  
5.  **[復旧モデル]** ボックスの一覧に現在の復旧モデルが表示されています。  
  
6.  復旧モデルを変更する必要がある場合は、別のモデルをこの一覧で選択します。 選択できるのは、**[完全]**、**[一括ログ]**、**[単純]** のいずれかです。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 復旧モデルを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューにクエリを実行して、 **model** データベースの復旧モデルを確認する方法を示します。  
  
```tsql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### 復旧モデルを変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 `model` ALTER DATABASE `FULL` ステートメントの `SET RECOVERY` オプションを使用して、 [データベース内の復旧モデルを](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) に変更する方法を示します。  
  
```tsql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="FollowUp"></a> 推奨事項: 復旧モデルを変更した後  
  
-   **完全復旧モデルと一括ログ復旧モデルの切り替え後の処理**  
  
    -   一括操作の完了後、すぐに完全復旧モードに戻してください。  
  
    -   一括ログ復旧モデルから完全復旧モデルに戻した後に、ログをバックアップしてください。  
  
        >**注:** バックアップ ストラテジは変更されません。つまり、データベースのバックアップ、ログ バックアップ、および差分バックアップが引き続き定期的に実行されます。  
  
-   **単純復旧モデルからの切り替え後の処理**  
  
    -   完全復旧モデルまたは一括ログ復旧モデルに切り替えた直後に、データベースの完全バックアップまたはデータベースの差分バックアップを作成し、ログ チェーンを開始します。  
  
        >**注:** 完全復旧モデルまたは一括ログ復旧モデルへの切り替えは、最初のデータ バックアップ後に有効になります。  
  
    -   定期的なログ バックアップをスケジュールし、それに応じて復元プランを更新します。  
  
        > **重要!!!!** ログをバックアップしてください!! ログのバックアップ頻度が不十分な場合、トランザクション ログが拡大し、領域不足になる可能性があります!  
  
-   **単純復旧モデルへの切り替え後の処理**  
  
    -   トランザクション ログをバックアップするためのスケジュールが設定されたすべてのジョブを停止します。  
  
    -   定期的なデータベースのバックアップがスケジュールされていることを確認します。 データの保護と、トランザクション ログのアクティブでない部分の切り捨ての両方にとって、データベースのバックアップは重要です。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [ジョブの作成](../../ssms/agent/create-a-job.md)  
  
-   [ジョブの有効化または無効化](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [メンテナンス プラン](http://msdn.microsoft.com/library/ms187658.aspx) ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] オンライン ブック)  
  
## 参照  
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  