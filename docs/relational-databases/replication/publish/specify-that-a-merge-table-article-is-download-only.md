---
title: "マージ テーブル アーティクルをダウンロード専用に指定する | Microsoft Docs"
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
  - "merge replication [SQL Server replication], download-only articles"
  - "articles [SQL Server replication], download-only"
  - "ダウンロード専用アーティクル"
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# マージ テーブル アーティクルをダウンロード専用に指定する
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、マージ テーブル アーティクルをダウンロード専用に指定する方法について説明します。 ダウンロード専用のアーティクルは、サブスクライバーで更新されないデータを含むアプリケーション用に設計されています。 詳細については、次を参照してください。 [Download-Only アーティクルを使用したマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)です。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **新しいマージ テーブル アーティクルをダウンロード専用に指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   サブスクリプションが初期化された後でアーティクルをダウンロードのみに指定する場合は、そのアーティクルを受信したすべてのクライアント サブスクリプションを再初期化する必要があります。 サーバー サブスクリプションは再初期化する必要はありません。 プロパティの変更の影響の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 アーティクルは、ダウンロード専用に指定、 **記事** パブリケーションの新規作成ウィザードのページまたは **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックス。 このダイアログ ボックスはパブリケーションの新規作成ウィザードで使用できる、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### [アーティクル] ページでアーティクルをダウンロードのみに指定するには  
  
-    **記事** 、テーブル、パブリケーションの新規作成ウィザードを選択し、チェック ボックスを選択のページ **反転表示されたテーブルはダウンロードのみ**します。  
  
#### アーティクルがダウンロード専用のアーティクルのプロパティ - [プロパティ] タブのことを指定する \< 記事> ] ダイアログ ボックス  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、テーブルを選択し、をクリックして **アーティクルのプロパティ**します。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **対象オブジェクト** のセクションで、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックスで、次の値のいずれかを指定 **同期の方向**:  
  
    -   **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を禁止する]**  
  
    -   **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を許可する]**  
  
4.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 新しいマージ テーブル アーティクルをダウンロード専用に指定するには  
  
1.  実行 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), の値を指定する **1** または **2** パラメーター **@subscriber_upload_options**します。 各数値は次の動作に対応します。  
  
    -   **0** -制限なし (既定)。 サブスクライバー側で行われた変更は、パブリッシャーにアップロードされます。  
  
    -   **1** - 変更は、サブスクライバーで許可されても、パブリッシャーにアップロードされません。  
  
    -   **2** -サブスクライバーの変更は許可されません。  
  
        > [!NOTE]  
        >  アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合 **@subscriber_upload_options** の両方のアーティクルで同じである必要があります。  
  
#### 既存のマージ テーブル アーティクルをダウンロード専用に変更するには  
  
1.  アーティクルをダウンロード専用のかどうかを確認するのには、実行 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)です。 値に注意してください **upload_options** 結果内のアーティクルに対して設定します。  
  
2.  手順 1 ではの値が返された場合 **0**, 、実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), の値を指定する **subscriber_upload_options** の **@property**, の値 **1** の **@force_invalidate_snapshot** と **@force_reinit_subscription**, の値との **1** または **2** の **@value**, 、次の動作に対応します。  
  
    -   **1** - 変更は、サブスクライバーで許可されても、パブリッシャーにアップロードされません。  
  
    -   **2** -サブスクライバーの変更は許可されません。  
  
        > [!NOTE]  
        >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、ダウンロード専用の動作は、両方のアーティクルで同じであることが必要です。  
  
## 参照  
 [ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [アーティクルのプロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  