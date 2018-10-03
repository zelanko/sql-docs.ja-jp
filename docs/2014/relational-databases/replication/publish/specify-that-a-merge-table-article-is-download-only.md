---
title: マージ テーブル アーティクルをダウンロード専用に指定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 694644e51b134c0063c0162b163b83e94e53354a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145002"
---
# <a name="specify-that-a-merge-table-article-is-download-only"></a>マージ テーブル アーティクルをダウンロード専用に指定する
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ テーブル アーティクルをダウンロード専用に指定する方法について説明します。 ダウンロード専用のアーティクルは、サブスクライバーで更新されないデータを含むアプリケーション用に設計されています。 詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **新しいマージ テーブル アーティクルをダウンロード専用に指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   サブスクリプションが初期化された後でアーティクルをダウンロードのみに指定する場合は、そのアーティクルを受信したすべてのクライアント サブスクリプションを再初期化する必要があります。 サーバー サブスクリプションは再初期化する必要はありません。 プロパティ変更の影響の詳細については、「[パブリケーションおよびアーティクルのプロパティの変更](change-publication-and-article-properties.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 アーティクルをダウンロードのみに指定するには、パブリケーションの新規作成ウィザードの **[アーティクル]** ページまたは **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブを使用します。 このダイアログ ボックスは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-articles-page"></a>[アーティクル] ページでアーティクルをダウンロードのみに指定するには  
  
-   パブリケーションの新規作成ウィザードの **[アーティクル]** ページでテーブルを選択し、 **[反転表示されたテーブルはダウンロードのみである]** チェック ボックスをオンにします。  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-properties-tab-of-the-article-properties---article-dialog-box"></a>[アーティクルのプロパティ - \<Article>] ダイアログ ボックスの [プロパティ] タブでアーティクルをダウンロードのみに指定するには  
  
1.  パブリケーションの新規作成ウィザードの **[アーティクル]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでテーブルを選択し、**[アーティクルのプロパティ]** をクリックします。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]** をクリックします。  
  
3.  **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブの **[対象オブジェクト]** セクションで、**[同期の方向]** に対して以下のいずれかの値を指定します。  
  
    -   **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を禁止する]**  
  
    -   **[サブスクライバーへのダウンロードのみを実行し、サブスクライバーの変更を許可する]**  
  
4.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、**[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-specify-that-a-new-merge-table-article-is-download-only"></a>新しいマージ テーブル アーティクルをダウンロード専用に指定するには  
  
1.  パラメーター [@subscriber_upload_options](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)に **1** または **2** を指定し、 **@subscriber_upload_options**を使用して、マージ テーブル アーティクルをダウンロード専用に指定する方法について説明します。 各数値は次の動作に対応します。  
  
    -   **0** - 制限なし (既定)。 サブスクライバー側で行われた変更は、パブリッシャーにアップロードされます。  
  
    -   **1** - サブスクライバーでの変更は許可されますが、パブリッシャーにはアップロードされません。  
  
    -   **2** - サブスクライバーでの変更は許可されません。  
  
        > [!NOTE]  
        >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、 **@subscriber_upload_options** の値は、両方のアーティクルで同じであることが必要です。  
  
#### <a name="to-modify-an-existing-merge-table-article-to-be-download-only"></a>既存のマージ テーブル アーティクルをダウンロード専用に変更するには  
  
1.  アーティクルがダウンロード専用であるかどうかを確認するには、 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)を実行します。 結果セットのアーティクルの **upload_options** の値を確認します。  
  
2.  手順 1. で返された値が **0**である場合は、 [@property](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)に **subscriber_upload_options** を、 **@property**および **1** を、 **@force_invalidate_snapshot** 」および「 **@force_reinit_subscription**には次の動作に対応する **1** または **2** を、 **@value**を実行します。  
  
    -   **1** - サブスクライバーでの変更は許可されますが、パブリッシャーにはアップロードされません。  
  
    -   **2** - サブスクライバーでの変更は許可されません。  
  
        > [!NOTE]  
        >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、ダウンロード専用の動作は、両方のアーティクルで同じであることが必要です。  
  
## <a name="see-also"></a>関連項目  
 [ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](define-an-article.md)   
 [アーティクルのプロパティの表示および変更](view-and-modify-article-properties.md)  
  
  
