---
title: "レッスン 2 : マージ パブリケーションへのサブスクリプションの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 423ad3b42e75c70e6826e04a298c5eac4e590291
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>レッスン 2 : マージ パブリケーションへのサブスクリプションの作成
このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。 次に、サブスクリプション データベースに権限を設定し、新しいサブスクリプション用のフィルター選択データのスナップショットを手動で作成します。 このレッスンを進めるには、前のレッスン「 [レッスン 1: マージ レプリケーションを使用したデータのパブリッシュ](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)」を完了している必要があります。  
  
### <a name="to-create-the-subscription"></a>サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノード、 **[レプリケーション]** フォルダーの順に展開して、 **[ローカル サブスクリプション]** フォルダーを右クリックし、 **[新しいサブスクリプション]**をクリックします。  
  
    サブスクリプションの新規作成ウィザードが起動します。  
  
2.  **[パブリケーション]** ページで、 **[パブリッシャー]** ボックスの一覧の **[SQL Server パブリッシャーの検索]** をクリックします。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、 **[サーバー名]** ボックスにパブリッシャー インスタンスの名前を入力し、 **[接続]**をクリックします。  
  
4.  **[AdvWorksSalesOrdersMerge]**をクリックし、 **[次へ]**をクリックします。  
  
5.  [マージ エージェントの場所] ページで、**[サブスクライバーで各エージェントを実行する]** をクリックし、**[次へ]** をクリックします。  
  
6.  [サブスクライバー] ページで、サブスクライバー サーバーのインスタンス名を選択し、**[サブスクリプション データベース]** の一覧で **[<New Database>]** を選択します。  
  
7.  **[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **SalesOrdersReplica** 」と入力し、 **[OK]**をクリックして **[次へ]**をクリックします。  
  
8.  [マージ エージェント セキュリティ] ページで参照ボタン (**[…]**) をクリックし、**[プロセス アカウント]** ボックスに「\<*コンピューター名>***\repl_merge**」と入力して、このアカウントのパスワードを入力します。次に、**[OK]** をクリックし、**[次へ]**をクリックし、**[次へ]**もう一度です。  
  
9. [サブスクリプションの初期化] ページで、**[次の場合に初期化]** ボックスの一覧から **[初回同期時]** を選択し、**[次へ]**をクリックし、**[次へ]**もう一度です。  
  
10. [HOST_NAME 値] ページで、**[HOST_NAME 値]** ボックスに値「**adventure-works\pamela0**」と入力して、**[完了]** をクリックします。  
  
11. もう一度 **[完了]** をクリックし、サブスクリプションが作成されたら **[閉じる]**をクリックします。  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>サブスクライバー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、 **[データベース]**、 **[SalesOrdersReplica]**、 **[セキュリティ]**の順に展開して、 **[ユーザー]**を右クリックし、 **[新しいユーザー]**を選択します。  
  
2.  **[全般]** ページで、**[ユーザー名]** ボックスに「\<*コンピューター名>***\repl_merge**」と入力します。参照ボタン (**[…]**) をクリックし、**[参照]** をクリックして [\<*コンピューター名>***\repl_merge**] を選択します。次に、**[OK]** をクリックし、**[名前の確認]** をクリックして、**[OK]** をクリックします。  
  
3.  **[データベース ロールのメンバーシップ]**で **[db_owner]**を選択し、 **[OK]** をクリックしてユーザーを作成します。  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>サブスクリプション用のフィルター選択データのスナップショットを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、 **[プロパティ]**をクリックします。  
  
    **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[データ パーティション]** ページを選択して、 **[追加]**をクリックします。  
  
4.  **[データ パーティションの追加]** ダイアログ ボックスで、 **[HOST_NAME 値]** ボックスに「 **adventure-works\pamela0** 」と入力し、 **[OK]**をクリックします。  
  
5.  新しく追加したパーティションを選択して、 **[今すぐ選択したスナップショットを生成する]**をクリックし、 **[OK]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
ここでは、マージ パブリケーションへのサブスクリプションを作成し、新しいサブスクリプションのデータ パーティション用のフィルター選択スナップショットを生成して、サブスクリプション初期化時に使用できるようにしました。 次は、サブスクリプション データベースのマージ エージェントに権限を付与します。さらに、マージ エージェントを実行して、同期の開始とサブスクリプションの初期化を行います。 「 [レッスン 3:マージ パブリケーションへのサブスクリプションの同期](../../relational-databases/replication/lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
[Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
[パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  

