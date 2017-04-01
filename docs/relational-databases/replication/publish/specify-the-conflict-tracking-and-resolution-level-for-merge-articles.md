---
title: "Specify the Conflict Tracking and Resolution Level for Merge Articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "merge replication conflict resolution [SQL Server replication], levels"
  - "articles [SQL Server replication], conflict resolution"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 81e9ecb6-1d31-4a78-b32a-96f7f4d67077
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Specify the Conflict Tracking and Resolution Level for Merge Articles
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクルの競合追跡と回避のレベルを指定する方法について説明します。  
  
 マージ パブリケーションへのサブスクリプションを同期する際、パブリッシャーとサブスクライバーの同じデータに加えられた変更によって、競合が発生していないかどうかがレプリケーション時に確認されます。 競合を行レベルで検出するか (行に加えられたすべての変更が競合と見なされます)、列レベルで検出するか (同じ行と列に対する変更のみが競合と見なされます) を指定できます。 アーティクルの競合解決は行レベルで実行されます。 論理レコードが使用される場合の競合の検出と解決の詳細については、「 [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **マージ アーティクルに対して競合の追跡と競合解決のレベルを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   サブスクリプションを初期化した後で追跡レベルを変更した場合は、サブスクリプションを再初期化する必要があります。 プロパティの変更の影響に関する詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
-   行レベルおよび列レベルの追跡では、行レベルでの競合回避は常に実行されます。優先されなかった行が優先された行で上書きされます。 マージ レプリケーションでは、論理レコード レベルでの競合の追跡と回避も指定できますが、このオプションは [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]にはありません。 レプリケーション ストアド プロシージャからこのオプションを設定する方法については、「 [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 行または列レベルでマージ アーティクルに追跡を指定、 **プロパティ** のタブ、 **アーティクルのプロパティ** パブリケーションの新規作成ウィザードで使用可能なダイアログ ボックスおよび **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 行レベルまたは列レベルの追跡を指定するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでテーブルを選択します。  
  
2.  **[アーティクルのプロパティ]**をクリックし、次に **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **プロパティ** のタブ、 **アーティクルのプロパティ \< 記事>** ダイアログ ボックスで、次のいずれかの値、 **追跡レベル** プロパティ: **行レベルの追跡** または **列レベルの追跡**します。  
  
4.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 新しいマージ アーティクルの競合追跡オプションを指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) の次の値のいずれかを指定して **@column_tracking**:。  
  
    -   **true** -アーティクルの列レベルの追跡を使用します。  
  
    -   **false** -既定値は、使用して行レベルの追跡します。  
  
#### マージ アーティクルの競合追跡オプションを変更するには  
  
1.  追跡オプションは、マージ アーティクルの競合を確認するのには、実行 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)します。 値に注意してください、 **column_tracking** 、記事の結果セットのオプションです。 値 **1** 列レベルの追跡が使用されていることを意味し、値 **0** 行レベルの追跡が使用されていることを意味します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **column_tracking** の **@property** し、次のいずれかの値を **@value**:  
  
    -   **true** -アーティクルの列レベルの追跡を使用します。  
  
    -   **false** -既定値は、使用して行レベルの追跡します。  
  
     値を指定して **1** 両方の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [論理レコードの競合の検出および解決](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [マージ レプリケーションの競合の検出と解決](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)  
  
  