---
title: 'レッスン 2 : マージ パブリケーションへのサブスクリプションの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ad258c2be4e7df3ff353a9fd1a1f9e7c083991d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084292"
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>レッスン 2 : マージ パブリケーションへのサブスクリプションの作成
  このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。 次に、サブスクリプション データベースに権限を設定し、新しいサブスクリプション用のフィルター選択データのスナップショットを手動で作成します。 このレッスンを進めるには、前のレッスン「 [レッスン 1: マージ レプリケーションを使用したデータのパブリッシュ](lesson-1-publishing-data-using-merge-replication.md)」を完了している必要があります。  
  
### <a name="to-create-the-subscription"></a>サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノード、 **[レプリケーション]** フォルダーの順に展開して、 **[ローカル サブスクリプション]** フォルダーを右クリックし、 **[新しいサブスクリプション]** をクリックします。  
  
     サブスクリプションの新規作成ウィザードが起動します。  
  
2.  **[パブリケーション]** ページで、 **[パブリッシャー]** ボックスの一覧の **[SQL Server パブリッシャーの検索]** をクリックします。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで、 **[サーバー名]** ボックスにパブリッシャー インスタンスの名前を入力し、 **[接続]** をクリックします。  
  
4.  **[AdvWorksSalesOrdersMerge]** をクリックし、 **[次へ]** をクリックします。  
  
5.  [マージ エージェントの場所] ページで、 **[サブスクライバーで各エージェントを実行する]** をクリックし、 **[次へ]** をクリックします。  
  
6.  サブスクライバー ページで、サブスクライバー サーバーのインスタンス名を選択**サブスクリプション データベース** **\<新しいデータベース >** 一覧からです。  
  
7.  **[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **SalesOrdersReplica** 」と入力し、 **[OK]** をクリックして **[次へ]** をクリックします。  
  
8.  [マージ エージェント セキュリティ] ページで参照ボタン (**[…]**) をクリックし、**[プロセス アカウント]** ボックスに「\<*コンピューター名>***\repl_merge**」と入力して、このアカウントのパスワードを入力します。次に **[OK]** をクリックし、**[次へ]** をクリックし、もう一度 **[次へ]** をクリックします。  
  
9. [サブスクリプションの初期化] ページで、**[次の場合に初期化]** ボックスの一覧から **[初回同期時]** を選択し、**[次へ]** をクリックし、**[次へ]** もう一度です。  
  
10. [HOST_NAME 値] ページの値を入力してください。`adventure-works\pamela0`で、 **HOST_NAME 値**ボックスと [] をクリック**完了**です。  
  
11. もう一度 **[完了]** をクリックし、サブスクリプションが作成されたら **[閉じる]** をクリックします。  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>サブスクライバー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、 **[データベース]**、 **[SalesOrdersReplica]**、 **[セキュリティ]** の順に展開して、 **[ユーザー]** を右クリックし、 **[新しいユーザー]** を選択します。  
  
2.  **[全般]** ページで、**[ユーザー名]** ボックスに「\<*コンピューター名>***\repl_merge**」と入力します。参照ボタン (**[…]**) をクリックし、**[参照]** をクリックして [\<*コンピューター名>***\repl_merge**] を選択します。次に **[OK]** をクリックし、**[名前の確認]** をクリックし、**[OK]** をクリックします。  
  
3.  **[データベース ロールのメンバーシップ]** で **[db_owner]** を選択し、 **[OK]** をクリックしてユーザーを作成します。  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>サブスクリプション用のフィルター選択データのスナップショットを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。  
  
     **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[データ パーティション]** ページを選択して、 **[追加]** をクリックします。  
  
4.  **データ パーティションの追加** ダイアログ ボックスで、「`adventure-works\pamela0`で、 **HOST_NAME 値**ボックスし、 をクリックして**OK**です。  
  
5.  新しく追加したパーティションを選択して、 **[今すぐ選択したスナップショットを生成する]** をクリックし、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、マージ パブリケーションへのサブスクリプションを作成し、新しいサブスクリプションのデータ パーティション用のフィルター選択スナップショットを生成して、サブスクリプション初期化時に使用できるようにしました。 次は、サブスクリプション データベースのマージ エージェントに権限を付与します。さらに、マージ エージェントを実行して、同期の開始とサブスクリプションの初期化を行います。 「 [レッスン 3:マージ パブリケーションへのサブスクリプションの同期](lesson-3-synchronizing-the-subscription-to-the-merge-publication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  