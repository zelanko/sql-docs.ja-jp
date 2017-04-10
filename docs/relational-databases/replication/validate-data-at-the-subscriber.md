---
title: "サブスクライバーでのデータの検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Subscribers [SQL Server replication], data validation"
  - "replication [SQL Server], validating data"
  - "transactional replication, validating data"
  - "validating data"
  - "マージ レプリケーションのデータ検証 [SQL Server レプリケーション]、SQL Server Management Studio"
ms.assetid: 215b4c9a-0ce9-4c00-ac0b-43b54151dfa3
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# サブスクライバーでのデータの検証
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、サブスクライバーでデータを検証する方法について説明します。  
  
 データの検証は、3 つの部分で構成されるプロセスです。  
  
1.  パブリケーションの単一のサブスクリプションまたはすべてのサブスクリプションが検証対象として *マーク* されます。 **の**[ローカル パブリケーション] **フォルダーと**[ローカル サブスクリプション] **フォルダーから使用できる、** [サブスクリプションの検証] **ダイアログ ボックス、** [サブスクリプションの検証] **ダイアログ ボックス、** [すべてのサブスクリプションの検証] [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスで検証対象のサブスクリプションにマークを付けます。 また、 **[すべてのサブスクリプション]** タブ、 **[サブスクリプション ウォッチ リスト]** タブ、およびレプリケーション モニターのパブリケーション ノードでもサブスクリプションにマークを付けることができます。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
2.  サブスクリプションは、ディストリビューション エージェント (トランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) による次回の同期時に検証されます。 ディストリビューション エージェントは、通常は連続して実行されるので、検証はすぐに実行されます。マージ エージェントは、通常は要求時に実行されるので、エージェントを実行した後で検証が実行されます。  
  
3.  検証結果は次の場所で表示できます。  
  
    -   レプリケーション モニターの詳細ウィンドウ : トランザクション レプリケーションの場合は **[ディストリビューターからサブスクライバーまでの履歴]** タブ、およびマージ レプリケーションの場合は **[同期の履歴]** タブ  
  
    -   **の** [同期の状態の表示] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]ダイアログ ボックス  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **サブスクライバーでデータを検証するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   レプリケーション モニターの手順は、プッシュ サブスクリプションにのみ適用されます。プル サブスクリプションはレプリケーション モニターでは同期できないからです。 ただし、レプリケーション モニターで、サブスクリプションに検証対象のマークを付けたり、プル サブスクリプションの検証結果を表示することはできます。  
  
-   検証結果には、検証が成功したかどうかが示されますが、失敗した場合、検証に失敗した行は示されません。 パブリッシャーとサブスクライバーのデータを比較するには、 [tablediff Utility](../../tools/tablediff-utility.md)を使用します。 レプリケートされたデータでこのユーティリティを使用する方法の詳細については、次を参照してください [相違点と #40; のレプリケートされたテーブルの比較。レプリケーション プログラミングと #41;](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### トランザクション パブリケーションのサブスクリプションのデータを検証するには (Management Studio)  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、サブスクリプションを検証するパブリケーションを右クリックして **のサブスクリプションの検証**します。  
  
4.  **[サブスクリプションの検証]** ダイアログ ボックスで、次のように検証するサブスクリプションを選択します。  
  
    -   **[すべての SQL Server サブスクリプションを検証する]**を選択する。  
  
    -   **[以下のサブスクリプションを検証する]**を選択し、1 つ以上のサブスクリプションを選択する。  
  
5.  (行の数または行数とチェックサム) を実行する検証の種類を指定するクリックして **検証オプション**, のオプションを指定し、 **サブスクリプションの検証オプション** ] ダイアログ ボックス。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  レプリケーション モニターまたは **[同期の状態の表示]** ダイアログ ボックスで検証結果を表示します。 サブスクリプションごとに、次の手順を実行します。  
  
    1.  パブリケーションを展開をサブスクリプションを右クリックし、をクリックして **[同期の状態**します。  
  
    2.  エージェントが実行されていない場合は、 **[同期の状態の表示]** ダイアログ ボックスの **[開始]** をクリックします。 ダイアログ ボックスには、検証に関する情報メッセージが表示されます。  
  
     検証に関するメッセージが表示されない場合、エージェントは既にその後のメッセージを記録しています。 この場合は、検証結果をレプリケーション モニターに表示します。 詳細については、このトピックのレプリケーション モニターの実行手順を参照してください。  
  
#### マージ パブリケーションの単一のサブスクリプションのデータを検証するには (Management Studio)  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  サブスクリプションの検証をサブスクリプションを右クリックし、をクリックするパブリケーションを展開 **サブスクリプションの検証**します。  
  
4.  **[サブスクリプションの検証]** ダイアログ ボックスで、 **[このサブスクリプションを検証する]**を選択します。  
  
5.  (行の数または行数とチェックサム) を実行する検証の種類を指定するクリックして **オプション**, のオプションを指定し、 **サブスクリプションの検証オプション** ] ダイアログ ボックス。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  レプリケーション モニターまたは **[同期の状態の表示]** ダイアログ ボックスで検証結果を表示します。  
  
    1.  パブリケーションを展開をサブスクリプションを右クリックし、をクリックして **[同期の状態**します。  
  
    2.  エージェントが実行されていない場合は、 **[同期の状態の表示]** ダイアログ ボックスの **[開始]** をクリックします。 ダイアログ ボックスには、検証に関する情報メッセージが表示されます。  
  
     検証に関するメッセージが表示されない場合、エージェントは既にその後のメッセージを記録しています。 この場合は、検証結果をレプリケーション モニターに表示します。 詳細については、このトピックのレプリケーション モニターの実行手順を参照してください。  
  
#### マージ パブリケーションのすべてのサブスクリプションのデータを検証するには (Management Studio)  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、サブスクリプションを検証するパブリケーションを右クリックして **すべてのサブスクリプションの検証**します。  
  
4.   **すべてのサブスクリプションの検証** ] ダイアログ ボックスで、(行の数または行数とチェックサム) を実行する検証の種類を指定します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  レプリケーション モニターまたは **[同期の状態の表示]** ダイアログ ボックスで検証結果を表示します。 サブスクリプションごとに、次の手順を実行します。  
  
    1.  パブリケーションを展開をサブスクリプションを右クリックし、をクリックして **[同期の状態**します。  
  
    2.  エージェントが実行されていない場合は、 **[同期の状態の表示]** ダイアログ ボックスの **[開始]** をクリックします。 ダイアログ ボックスには、検証に関する情報メッセージが表示されます。  
  
     検証に関するメッセージが表示されない場合、エージェントは既にその後のメッセージを記録しています。 この場合は、検証結果をレプリケーション モニターに表示します。 詳細については、このトピックのレプリケーション モニターの実行手順を参照してください。  
  
#### トランザクション パブリケーションのすべてのプッシュ サブスクリプションのデータを検証するには (レプリケーション モニター)  
  
1.  レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。  
  
2.  クリックして、サブスクリプションを検証するパブリケーションを右クリックして **のサブスクリプションの検証**します。  
  
3.  **[サブスクリプションの検証]** ダイアログ ボックスで、次のように検証するサブスクリプションを選択します。  
  
    -   **[すべての SQL Server サブスクリプションを検証する]**を選択する。  
  
    -   **[以下のサブスクリプションを検証する]**を選択し、1 つ以上のサブスクリプションを選択する。  
  
4.  (行の数または行数とチェックサム) を実行する検証の種類を指定するクリックして **検証オプション**, のオプションを指定し、 **サブスクリプションの検証オプション** ] ダイアログ ボックス。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  **[すべてのサブスクリプション]** タブをクリックします。  
  
7.  検証結果を表示します。 プッシュ サブスクリプションごとに、次の手順を実行します。  
  
    1.  エージェントが実行されていない場合、サブスクリプションを右クリックし、をクリックして **同期の開始**します。  
  
    2.  サブスクリプションの場合を右クリックし、をクリックし、 **の詳細の表示**します。  
  
    3.  **[ディストリビューターからサブスクライバーまでの履歴]** タブの **[選択されたセッションのアクション]** テキスト領域に情報が表示されます。  
  
#### マージ パブリケーションの単一のプッシュ サブスクリプションのデータを検証するには (レプリケーション モニター)  
  
1.  レプリケーション モニターで、左ペインのパブリッシャー グループを展開し、パブリッシャーを展開してパブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  クリックして、検証するサブスクリプションを右クリックして **サブスクリプションの検証**します。  
  
4.  **[サブスクリプションの検証]** ダイアログ ボックスで、 **[このサブスクリプションを検証する]**を選択します。  
  
5.  (行の数または行数とチェックサム) を実行する検証の種類を指定するクリックして **オプション**, のオプションを指定し、 **サブスクリプションの検証オプション** ] ダイアログ ボックス。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  **[すべてのサブスクリプション]** タブをクリックします。  
  
8.  検証結果を表示します。  
  
    1.  エージェントが実行されていない場合、サブスクリプションを右クリックし、をクリックして **同期の開始**します。  
  
    2.  サブスクリプションの場合を右クリックし、をクリックし、 **の詳細の表示**します。  
  
    3.  **[同期の履歴]** タブの **[選択されたセッションの最終メッセージ]** テキスト領域に情報が表示されます。  
  
#### マージ パブリケーションのすべてのプッシュ サブスクリプションのデータを検証するには (レプリケーション モニター)  
  
1.  レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。  
  
2.  クリックして、サブスクリプションを検証するパブリケーションを右クリックして **すべてのサブスクリプションの検証**します。  
  
3.   **すべてのサブスクリプションの検証** ] ダイアログ ボックスで、(行の数または行数とチェックサム) を実行する検証の種類を指定します。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  **[すべてのサブスクリプション]** タブをクリックします。  
  
6.  検証結果を表示します。 プッシュ サブスクリプションごとに、次の手順を実行します。  
  
    1.  エージェントが実行されていない場合、サブスクリプションを右クリックし、をクリックして **同期の開始**します。  
  
    2.  サブスクリプションの場合を右クリックし、をクリックし、 **の詳細の表示**します。  
  
    3.  **[同期の履歴]** タブの **[選択されたセッションの最終メッセージ]** テキスト領域に情報が表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### トランザクション パブリケーションのすべてのアーティクルについてデータを検証するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_publication_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)します。 指定 **@publication** し、次のいずれかの値を **@rowcount_only**:  
  
    -   **1** -行数チェックのみ (既定値)  
  
    -   **2** -行数とバイナリ チェックサム。  
  
    > [!NOTE]  
    >  実行すると [sp_publication_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), 、[sp_article_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) パブリケーション内の各アーティクルに対して実行されます。 正常に実行する [sp_publication_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md), 、パブリッシュされたベース テーブル内のすべての列に対する SELECT 権限が必要です。  
  
2.  (省略可) ディストリビューション エージェントがまだ実行されていない場合は、各サブスクリプションについてディストリビューション エージェントを開始します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
3.  エージェントの出力で検証結果を確認します。 詳細については、次を参照してください。 [レプリケート データの検証](../../relational-databases/replication/validate-replicated-data.md)します。  
  
#### トランザクション パブリケーションの単一のアーティクルについてデータを検証するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_article_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)します。 指定 **@publication**, 、アーティクルの名前 **@article**, 、次のいずれかの値 **@rowcount_only**:  
  
    -   **1** -行数チェックのみ (既定値)  
  
    -   **2** -行数とバイナリ チェックサム。  
  
    > [!NOTE]  
    >  正常に実行する [sp_article_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), 、パブリッシュされたベース テーブルのすべての列に対する SELECT 権限が必要です。  
  
2.  (省略可) ディストリビューション エージェントがまだ実行されていない場合は、各サブスクリプションについてディストリビューション エージェントを開始します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
3.  エージェントの出力で検証結果を確認します。 詳細については、次を参照してください。 [レプリケート データの検証](../../relational-databases/replication/validate-replicated-data.md)します。  
  
#### トランザクション パブリケーションの単一のサブスクライバーについてデータを検証するには  
  
1.  パブリッシャー、パブリケーション データベースで、開く明示的なトランザクションを使用して、 [BEGIN TRANSACTION と #40 です。Transact SQL と #41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_marksubscriptionvalidation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)です。 パブリケーションを指定 **@publication**, のサブスクライバーの名前 **@subscriber**, 、およびサブスクリプション データベースの名前 **@destination_db**です。  
  
3.  (省略可) 検証の対象となる各サブスクリプションについて、手順 2. を繰り返します。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_article_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)します。 指定 **@publication**, 、アーティクルの名前 **@article**, 、次のいずれかの値 **@rowcount_only**:  
  
    -   **1** -行数チェックのみ (既定値)  
  
    -   **2** -行数とバイナリ チェックサム。  
  
    > [!NOTE]  
    >  正常に実行する [sp_article_validation & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md), 、パブリッシュされたベース テーブルのすべての列に対する SELECT 権限が必要です。  
  
5.  パブリッシャー側でパブリケーション データベースでコミット トランザクションを使用して、 [トランザクションをコミットする (&) #40 です。Transact SQL と #41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)します。  
  
6.  (省略可) 検証の対象となる各アーティクルについて、手順 1. から手順 5. を繰り返します。  
  
7.  (省略可) ディストリビューション エージェントがまだ実行されていない場合は、開始します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
8.  エージェントの出力で検証結果を確認します。 詳しくは、「 [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md)」をご覧ください。  
  
#### マージ パブリケーションのすべてのサブスクリプションについてデータを検証するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_validatemergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-validatemergepublication-transact-sql.md)します。 **@publication** を指定し、次のいずれかの値を **@level**に指定します。  
  
    -   **1** の行数のみの検証。  
  
    -   **3** -行数バイナリ チェックサム検証します。  
  
     これにより、すべてのサブスクリプションが検証対象としてマークされます。  
  
2.  各サブスクリプションのマージ エージェントを開始します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
3.  エージェントの出力で検証結果を確認します。 詳しくは、「 [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md)」をご覧ください。  
  
#### マージ パブリケーションの選択したサブスクリプションについてデータを検証するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_validatemergesubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md)します。 指定 **@publication**, 、サブスクライバーの名前 **@subscriber**, のサブスクリプション データベースの名前 **@subscriber_db**, 、次のいずれかの値 **@level**:  
  
    -   **1** の行数のみの検証。  
  
    -   **3** -行数バイナリ チェックサム検証します。  
  
     これにより、選択されたサブスクリプションが検証対象としてマークされます。  
  
2.  各サブスクリプションのマージ エージェントを開始します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
3.  エージェントの出力で検証結果を確認します。  
  
4.  検証の対象となる各サブスクリプションについて、手順 1. から手順 3. を繰り返します。  
  
> [!NOTE]  
>  指定して、マージ パブリケーションに対するサブスクリプションの同期の最後の検証することも、 **-検証** を実行している場合に、パラメーター、 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)します。  
  
#### マージ エージェントのパラメーターを使用してサブスクリプションのデータを検証するには  
  
1.  サブスクライバー (プル サブスクリプションの場合) またはディストリビューター (プッシュ サブスクリプションの場合) で、次のいずれかの方法でコマンド プロンプトからマージ エージェントを開始します。  
  
    -   値を指定する **1** (行数) または **3** (行数とバイナリ チェックサム) に対して、 **-検証** パラメーター。  
  
    -   指定する **行数検証** または **行数とチェックサム検証** の **- ProfileName** パラメーター。  
  
     詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」または「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーションでは、サブスクライバーのデータがパブリッシャーのデータと一致するかどうかを、レプリケーション管理オブジェクト (RMO) を使用してプログラムから検証できます。 使用するオブジェクトは、レプリケーション トポロジの種類によって異なります。 トランザクション レプリケーションでは、パブリケーションのサブスクリプションをすべて検証する必要があります。  
  
> [!NOTE]  
>  例については、次を参照してください。 [例 (RMO)](#RMOExample), は、このセクションで後述します。  
  
#### トランザクション パブリケーションのすべてのアーティクルについてデータを検証するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> パブリケーションのプロパティです。 設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトの残りのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.TransPublication.ValidatePublication%2A> メソッドです。 次のパラメーターを指定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationOption>  
  
    -   <xref:Microsoft.SqlServer.Replication.ValidationMethod>  
  
    -   検証が終了した後、ディストリビューション エージェントを停止するかどうかを示すブール値  
  
     これにより、アーティクルが検証対象としてマークされます。  
  
5.  まだディストリビューション エージェントを実行していない場合は、ディストリビューション エージェントを起動して、各サブスクリプションを同期します。 詳細については、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md) 」または「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」を参照してください。 検証操作の結果は、エージェントの履歴に出力されます。 詳しくは、「 [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)」をご覧ください。  
  
#### マージ パブリケーションのすべてのサブスクリプションについてデータを検証するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> パブリケーションのプロパティです。 設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトの残りのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.ValidatePublication%2A> メソッドです。 必要な通過 <xref:Microsoft.SqlServer.Replication.ValidationOption>します。  
  
5.  各サブスクリプションについてマージ エージェントを実行して検証を開始するか、次回予定されているエージェントの実行を待ちます。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。 検証操作の結果は、エージェントの履歴に出力されます。この履歴は、レプリケーション モニターを使って表示できます。 詳しくは、「 [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)」をご覧ください。  
  
#### マージ パブリケーションの単一のサブスクリプションについてデータを検証するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> パブリケーションのプロパティです。 設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトの残りのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.ValidateSubscription%2A> メソッドです。 検証対象のサブスクライバーとサブスクリプション データベースの名前と必要なを渡す <xref:Microsoft.SqlServer.Replication.ValidationOption>します。  
  
5.  目的のサブスクリプションについてマージ エージェントを実行して検証を開始するか、次回予定されているエージェントの実行を待ちます。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」および「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。 検証操作の結果は、エージェントの履歴に出力されます。この履歴は、レプリケーション モニターを使って表示できます。 詳しくは、「 [Monitoring Replication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)」をご覧ください。  
  
###  <a name="RMOExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションのすべてのサブスクリプションを、行数検証の対象としてマークします。  
  
 [!code-csharp[HowTo#rmo_ValidateTranPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatetranpub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateTranPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatetranpub)]  
  
 次の例では、マージ パブリケーションの特定のサブスクリプションを、行数検証の対象としてマークします。  
  
 [!code-csharp[HowTo#rmo_ValidateMergeSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_validatemergesub)]  
  
 [!code-vb[HowTo#rmo_vb_ValidateMergeSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_validatemergesub)]  
  
  