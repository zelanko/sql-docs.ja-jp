---
title: "マージ アーティクルのインタラクティブな競合回避の指定 | Microsoft Docs"
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
  - "マージ レプリケーションの競合解決 [SQL Server レプリケーション]、インタラクティブ競合回避"
  - "インタラクティブな競合解決 [SQL Server レプリケーション]"
  - "アーティクル [SQL Server レプリケーション], 競合回避"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# マージ アーティクルのインタラクティブな競合回避の指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクルにインタラクティブな競合回避を指定する方法について説明します。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションでは、インタラクティブ競合回避モジュールでの要求時同期中に競合を手動で解決できる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャー。 インタラクティブな競合解決を有効にすると、インタラクティブ競合回避モジュールを使用して、同期実行時に競合がインタラクティブに解決されます。 インタラクティブ競合回避モジュールは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーで利用できます。 詳細については、次を参照してください [サブスクリプションを使用して Windows 同期マネージャーと #40; の同期。Windows 同期マネージャーと #41;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md)します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **マージ アーティクルにインタラクティブな競合回避を指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   同期が Windows 同期マネージャーの外部で (スケジュールされた同期、または SQL Server Management Studio かレプリケーション モニターでの要求時同期として) 実行される場合、アーティクルに指定された既定の競合回避を使用して、ユーザーの介入なしに自動的に競合が解決されます。 詳細については、「 [Interactive Conflict Resolution](../../../relational-databases/replication/merge/interactive-conflict-resolution.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### アーティクルに対してインタラクティブな競合解決を有効にするには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでテーブルを選択します。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
2.  **[アーティクルのプロパティ]**をクリックし、次に **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **アーティクルのプロパティ - \< 記事>** または **アーティクルのプロパティ - \< ArticleType>** ] ページで、をクリックして、 **リゾルバー** ] タブをクリックします。  
  
4.  選択 **の要求時同期中に競合を対話的に解決するを許可するサブスクライバー**します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### サブスクリプションでインタラクティブな競合解決を使用するように指定するには  
  
1.   **サブスクリプションのプロパティ - \< サブスクライバー>: \< SubscriptionDatabase>** ] ダイアログ ボックスの値を指定 **True** の **の競合を解決するには、対話形式で** オプション。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 マージ パブリケーションに対するプル サブスクリプションが作成されるときに、サブスクライバーがこのグラフィカル インターフェイスを使用してアーティクルの競合を回避するように、プログラムで指定できます。 このオプションをサポートするアーティクル内の競合のみが、インタラクティブ競合回避モジュールに表示されます。  
  
#### インタラクティブ競合回避モジュールを使用するマージ プル サブスクリプションを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), を指定して **@publication**します。 値に注意してください **allow_interactive_resolver** インタラクティブ競合回避モジュールを使用する場合に結果セット内の各アーティクルです。  
  
    -   この値が **1**の場合、インタラクティブ競合回避モジュールが使用されます。  
  
    -   この値が **0**の場合は、最初に、各アーティクルに対してインタラクティブ競合回避モジュールを有効にする必要があります。 これを行うには、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), を指定して **@publication**, 、**@article**, 、の値 **allow_interactive_resolver** の **@property**, 、の値との **true** の **@value**します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
3.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md), 、次のパラメーターを指定します。  
  
    -   **@publisher**, 、**@publisher_db** (パブリッシュされたデータベース) と **@publication**します。  
  
    -   値 **true** の **@enabled_for_syncmgr**します。  
  
    -   値 **true** の **@use_interactive_resolver**します。  
  
    -   マージ エージェントが必要とするセキュリティ アカウント情報。 詳細については、「 [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)します。  
  
#### インタラクティブ競合回避モジュールをサポートするアーティクルを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, の値との **true** の **@allow_interactive_resolver**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
## 参照  
 [表示してマージ パブリケーションおよび #40; のデータの競合を解決します。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)   
 [インタラクティブな競合解決](../../../relational-databases/replication/merge/interactive-conflict-resolution.md)  
  
  