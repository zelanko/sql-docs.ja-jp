---
title: "データの変更をトランザクション アーティクルに反映する方法の設定 | Microsoft Docs"
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
  - "transactional replication, propagation methods"
  - "データ変更の反映 [SQL Server レプリケーション]"
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# データの変更をトランザクション アーティクルに反映する方法の設定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、トランザクション アーティクルへのデータの変更の反映方法を設定する方法について説明します。  
  
 既定では、トランザクション レプリケーションは、各アーティクルのストアド プロシージャ セットを使用して変更内容をサブスクライバーに反映します。 これらのプロシージャはカスタム プロシージャに置換することができます。 詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **データの変更をトランザクション アーティクルに反映する方法を設定するために、使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   レプリケーションによって生成されたスナップショット ファイルを編集する場合には注意が必要です。 カスタム ストアド プロシージャのカスタム ロジックをテストしてサポートする必要があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ではカスタム ロジックをサポートしていません。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 反映する方法を指定、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** パブリケーションの新規作成ウィザードで使用可能なダイアログ ボックスおよび **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 反映方法を指定するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、テーブルを選択し、をクリックして **アーティクルのプロパティ**します。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ダイアログ ボックスで、 **ステートメントの配信** セクションで、各操作を使用する伝達方法を指定、 **INSERT 配信形式**, 、**UPDATE 配信形式**, 、および **DELETE 配信形式** メニュー。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### カスタム ストアド プロシージャを生成して使用するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、テーブルを選択し、をクリックして **アーティクルのプロパティ**します。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
      **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ダイアログ ボックスで、 **ステートメントの配信** セクションで、適切な配信形式] メニューから、呼び出しの構文を選択 (**INSERT 配信形式**, 、**UPDATE 配信形式**, 、または **DELETE 配信形式**) で使用するプロシージャの名前を入力し、 **INSERT ストアド プロシージャ**, 、**ストアド プロシージャを削除**, 、または **更新ストアド プロシージャ**します。 呼び出し構文の詳細については、「ストアド プロシージャの呼び出し構文」セクションを参照してください [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
5.  パブリケーションのスナップショットが生成されると、そのスナップショットには前の手順で指定したプロシージャが含まれています。 このプロシージャは指定した CALL 構文を使用しますが、レプリケーションが使用する既定のロジックを含んでいます。  
  
     スナップショットが生成された後、このアーティクルが属するパブリケーションのスナップショット フォルダーに移動し、アーティクルと同じ名前の **.sch** ファイルを見つけます。 メモ帳などのテキスト エディターでこのファイルを開き、挿入、更新、または削除の各ストアド プロシージャで CREATE PROCEDURE コマンドを検索し、プロシージャ定義を編集してデータの変更を反映するためのカスタム ロジックを指定します。 スナップショットが再生成された場合は、カスタム プロシージャを再作成する必要があります。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 トランザクション レプリケーションでは、パブリッシャーからサブスクライバーへの変更の反映方法を制御できます。この反映メソッドは、アーティクルの作成時やその後の変更時に、レプリケーションのストアド プロシージャを使用してプログラムから設定できます。  
  
> [!NOTE]  
>  パブリッシュされたデータ行に適用される DML (データ操作言語) 操作には、挿入、更新、削除などがありますが、各種の操作に対して異なる反映メソッドを指定できます。  
  
 詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
#### データ変更を Transact-SQL コマンドを使って反映するアーティクルを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, の値との **SQL** 少なくとも 1 つで、次のパラメーター。  
  
    -   **@ins_cmd** -のレプリケーションを制御 [挿入](../../../t-sql/statements/insert-transact-sql.md) コマンドです。  
  
    -   **@upd_cmd** -のレプリケーションを制御 [更新](../../../t-sql/queries/update-transact-sql.md) コマンドです。  
  
    -   **@del_cmd** -のレプリケーションを制御 [削除](../../../t-sql/statements/delete-transact-sql.md) コマンドです。  
  
    > [!NOTE]  
    >  値を指定するときに **SQL** これらのパラメーターのいずれにも、その型のコマンドを適切なとしてサブスクライバーにレプリケートされます [!INCLUDE[tsql](../../../includes/tsql-md.md)] コマンドです。  
  
     詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### データ変更を反映しないアーティクルを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, の値との **NONE** 少なくとも 1 つで、次のパラメーター。  
  
    -   **@ins_cmd** -のレプリケーションを制御 [挿入](../../../t-sql/statements/insert-transact-sql.md) コマンドです。  
  
    -   **@upd_cmd** -のレプリケーションを制御 [更新](../../../t-sql/queries/update-transact-sql.md) コマンドです。  
  
    -   **@del_cmd** -のレプリケーションを制御 [削除](../../../t-sql/statements/delete-transact-sql.md) コマンドです。  
  
    > [!NOTE]  
    >  値を指定するときに **NONE** これらのパラメーターのいずれにも、その型のコマンドがレプリケートされないサブスクライバーにします。  
  
     詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### ユーザーが変更したカスタム ストアド プロシージャを含むアーティクルを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, の値、 **@schema_option** 値を含むビットマスク **0x02** (カスタム ストアド プロシージャの自動生成をにより) と、次のパラメーターの 1 つ以上。  
  
    -   **@ins_cmd** -の値を指定して **CALL sp_msins _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    -   **@del_cmd** -の値を指定して **呼び出し sp_msdel _*article_name*** または **XCALL sp_msdel _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    -   **@upd_cmd** -の値を指定して **SCALL sp_msupd _*article_name***, 、**呼び出し sp_msupd _*article_name***, 、**XCALL sp_msupd _*article_name***, 、または **MCALL sp_msupd _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    > [!NOTE]  
    >  上記コマンド パラメーターのそれぞれについて、レプリケーションによって生成されるストアド プロシージャに独自の名前を指定できます。  
  
    > [!NOTE]  
    >  呼び出し、SCALL、XCALL、MCALL 構文の詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
     詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  スナップショットが生成された後、このアーティクルが属するパブリケーションのスナップショット フォルダーに移動し、アーティクルと同じ名前の **.sch** ファイルを見つけます。 このファイルを Notepad.exe で開き、挿入、更新、削除のストアド プロシージャに対応する CREATE PROCEDURE コマンドを見つけ、そのプロシージャ定義を編集して、データ変更を反映するためのカスタム ロジックを指定します。 詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
#### カスタム ストアド プロシージャにデータ変更を反映するカスタム スクリプトを含むアーティクルを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, の値、 **@schema_option** 値を含むビットマスク **0x02** (カスタム ストアド プロシージャの自動生成をにより) と、次のパラメーターの 1 つ以上。  
  
    -   **@ins_cmd** -の値を指定して **CALL sp_msins _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    -   **@del_cmd** -の値を指定して **呼び出し sp_msdel _*article_name*** または **XCALL sp_msdel _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    -   **@upd_cmd** -の値を指定して **SCALL sp_msupd _*article_name***, 、**呼び出し sp_msupd _*article_name***, 、**XCALL sp_msupd _*article_name***, 、**MCALL sp_msupd _*article_name***, ここで、 ***article_name*** の値が指定 **@article** します。  
  
    > [!NOTE]  
    >  上記コマンド パラメーターのそれぞれについて、レプリケーションによって生成されるストアド プロシージャに独自の名前を指定できます。  
  
    > [!NOTE]  
    >  呼び出し、SCALL、XCALL、MCALL 構文の詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
     詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  パブリッシャー、パブリケーション データベースを使用して、 [ALTER PROCEDURE](../../../t-sql/statements/alter-procedure-transact-sql.md) ステートメントを編集する [sp_scriptpublicationcustomprocs](../../../relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql.md) を返すように、 [CREATE PROCEDURE](../../../t-sql/statements/create-procedure-transact-sql.md) insert、update、および削除のカスタム ストアド プロシージャのスクリプトです。 詳細については、次を参照してください。 [トランザクション アーティクルに変更を反映する方法を指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)します。  
  
#### 既存のアーティクルの変更反映メソッドを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)します。 指定 **@publication**, 、**@article**, の値 **ins_cmd**, 、**upd_cmd**, 、または **del_cmd** の **@property**, と適切な伝達方法 **@value**します。  
  
2.  変更対象の各反映メソッドについて、手順 1. を繰り返します。  
  
## 参照  
 [トランザクション アーティクルに変更を反映する方法の指定](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [作成、変更、およびパブリケーションおよびアーティクル & #40; を削除レプリケーションと #41 です。](../../../relational-databases/replication/publish/create-modify-and-delete-publications-and-articles-replication.md)  
  
  