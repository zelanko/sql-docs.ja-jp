---
title: "更新可能トランザクション サブスクリプションの更新モードの切り替え | Microsoft Docs"
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
  - "トランザクション レプリケーション、更新可能なサブスクリプション"
  - "更新可能なサブスクリプション、更新モード"
  - "サブスクリプション [SQL Server レプリケーション]、更新可能"
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# 更新可能トランザクション サブスクリプションの更新モードの切り替え
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、更新可能トランザクション サブスクリプションの更新モードを切り替える方法について説明します。 サブスクリプションの新規作成ウィザードを使用して、更新可能サブスクリプションのモードを指定します。 このウィザードを使用する場合、モードを設定する方法については、次を参照してください。 [ビューとプル サブスクリプションのプロパティの変更](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **更新可能トランザクション サブスクリプションの更新モードを切り替えるために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   即時更新からキュー更新に、いつでもフェールオーバーできます。 ただしそれ以降、サブスクライバーとパブリッシャーが接続され、キュー リーダー エージェントによってキュー内の保留中メッセージがすべてパブリッシャーに適用されるまで、即時更新に戻すことはできません。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   トランザクション パブリケーションへの更新サブスクリプションで更新モード間のフェールオーバーがサポートされている場合、接続が短時間で変化する状況に対応するために、更新モードをプログラムで変更することができます。 更新モードはレプリケーション ストアド プロシージャを使用して、プログラムから設定することも、要求時に設定することもできます。 詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
> [!NOTE]  
>  サブスクリプションを作成した後、更新モードを変更する、 **update_mode** にプロパティを設定する必要があります **フェールオーバー** (即時更新を切り替えキュー更新) または **フェイル オーバーをキューに置かれた** (これにより、即時更新にキューに置かれた更新からの切り替え) サブスクリプションを作成するとします。 これらのプロパティは、サブスクリプションの新規作成ウィザードで自動的に設定されます。  
  
#### プッシュ サブスクリプションの更新モードを設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  更新モードを設定し、クリックするサブスクリプションを右クリックして **[更新方法の**です。  
  
4.   **更新方法の設定 - \< サブスクライバー>: \< SubscriptionDatabase>** ダイアログ ボックスで、 **即時更新** または **キュー更新**します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### プル サブスクリプションの更新モードを設定するには  
  
1.   **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** ] ダイアログ ボックスでの値を選択 **すぐに変更をレプリケート** または **の変更をキュー** の **サブスクライバーの更新方法** オプション。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 アクセスの詳細については、 **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** ダイアログ ボックスを参照してください [ビューとプル サブスクリプションのプロパティの変更](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 更新モードを切り替えるには  
  
1.  サブスクリプションが実行することによって、フェールオーバーをサポートしていることを確認 [sp_helppullsubscription](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md) プル サブスクリプションの場合、または [sp_helpsubscription](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) プッシュ サブスクリプションの場合。 場合の値 **更新モード** 結果セットが **3** または **4**, 、フェールオーバーがサポートされています。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_setreplfailovermode](../../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、次のいずれかの値と **@failover_mode**:  
  
    -   **キューに置かれた** -接続が一時的に失われた場合、キュー更新にフェールオーバーします。  
  
    -   **イミディ エイト** -接続が復元された場合、即時更新にフェールオーバーします。  
  
## 参照  
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  