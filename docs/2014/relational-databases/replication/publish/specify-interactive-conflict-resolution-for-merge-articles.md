---
title: マージ アーティクルのインタラクティブな競合回避の指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], interactive resolvers
- interactive conflict resolution [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 80f3817de3ff8242d24dfc0e1ca507f186e05508
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205302"
---
# <a name="specify-interactive-conflict-resolution-for-merge-articles"></a>マージ アーティクルのインタラクティブな競合回避の指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクルにインタラクティブな競合回避を指定する方法について説明します。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションでは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーでの要求時同期中に、手動で競合を解決できるインタラクティブ競合回避モジュールを利用できます。 インタラクティブな競合解決を有効にすると、インタラクティブ競合回避モジュールを使用して、同期実行時に競合がインタラクティブに解決されます。 インタラクティブ競合回避モジュールは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 同期マネージャーで利用できます。 詳しくは、「[Windows 同期マネージャーを使用したサブスクリプションの同期 &#40;Windows 同期マネージャー&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md)」をご覧ください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **マージ アーティクルにインタラクティブな競合回避を指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   同期が Windows 同期マネージャーの外部で (スケジュールされた同期、または SQL Server Management Studio かレプリケーション モニターでの要求時同期として) 実行される場合、アーティクルに指定された既定の競合回避を使用して、ユーザーの介入なしに自動的に競合が解決されます。 詳細については、「 [Interactive Conflict Resolution](../merge/advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-enable-interactive-conflict-resolution-for-an-article"></a>アーティクルに対してインタラクティブな競合解決を有効にするには  
  
1.  パブリケーションの新規作成ウィザードの **[アーティクル]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、テーブルを選択します。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
2.  **[アーティクルのプロパティ]** をクリックし、次に **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]** をクリックします。  
  
3.  **[アーティクルのプロパティ - \<Article>]** または **[アーティクルのプロパティ - \<ArticleType>]** ページで、**[競合回避モジュール]** タブをクリックします。  
  
4.  **[要求時同期中にサブスクライバーが対話的に競合を解決することを許可する]** を選択します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、**[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
#### <a name="to-specify-that-a-subscription-should-use-interactive-conflict-resolution"></a>サブスクリプションでインタラクティブな競合解決を使用するように指定するには  
  
1.  **[サブスクリプションのプロパティ - \<Subscriber>: \<SubscriptionDatabase>]** ダイアログ ボックスで、**[競合を対話的に解決]** オプションに対して **[True]** の値を指定します。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](../view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 マージ パブリケーションに対するプル サブスクリプションが作成されるときに、サブスクライバーがこのグラフィカル インターフェイスを使用してアーティクルの競合を回避するように、プログラムで指定できます。 このオプションをサポートするアーティクル内の競合のみが、インタラクティブ競合回避モジュールに表示されます。  
  
#### <a name="to-create-a-merge-pull-subscription-that-uses-the-interactive-resolver"></a>インタラクティブ競合回避モジュールを使用するマージ プル サブスクリプションを作成するには  
  
1.  パブリッシャー側のパブリケーション データベースに対し、 [@publication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)を指定して **@publication**を使用して、マージ アーティクルにインタラクティブな競合回避を指定する方法について説明します。 インタラクティブ競合回避モジュールが使用される結果セット内の各アーティクルに対する **allow_interactive_resolver** の値を確認します。  
  
    -   この値が **1**の場合、インタラクティブ競合回避モジュールが使用されます。  
  
    -   この値が **0**の場合は、最初に、各アーティクルに対してインタラクティブ競合回避モジュールを有効にする必要があります。 そのためには、 [@publication](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を指定して **@publication**を指定し、 **@article**に **allow_interactive_resolver** を、 **@property**に **true** を、 **@value**を使用して、マージ アーティクルにインタラクティブな競合回避を指定する方法について説明します。  
  
2.  サブスクライバー側のサブスクリプション データベースに対して、 [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)を実行します。 詳細については、「 [プル サブスクリプションの作成](../create-a-pull-subscription.md)」をご覧ください。  
  
3.  サブスクライバー側のサブスクリプション データベースに対し、次のパラメーターを指定して [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)を実行します。  
  
    -   **@publisher**を指定し、 **@publisher_db** (パブリッシュされるデータベース)、および **@publication**を使用して、マージ アーティクルにインタラクティブな競合回避を指定する方法について説明します。  
  
    -   **@enabled_for_syncmgr** には値 **true**。  
  
    -   **@use_interactive_resolver** には値 **true**。  
  
    -   マージ エージェントが必要とするセキュリティ アカウント情報。 詳細については、「 [Create a Pull Subscription](../create-a-pull-subscription.md)」を参照してください。  
  
4.  パブリッシャー側のパブリケーション データベースに対し、 [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql)を実行します。  
  
#### <a name="to-define-an-article-that-supports-the-interactive-resolver"></a>インタラクティブ競合回避モジュールをサポートするアーティクルを定義するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。 アーティクルが属しているパブリケーションの名前を **@publication** に、アーティクルの名前を **@article** に、パブリッシュされるデータベース オブジェクトを **@source_object** に、値 **true** を **@allow_interactive_resolver** に指定します。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](../view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Interactive Conflict Resolution](../merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
  
