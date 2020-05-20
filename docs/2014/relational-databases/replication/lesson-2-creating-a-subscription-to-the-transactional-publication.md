---
title: 'レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9dc9824efb3f962d97f786835fa2367be18b55f7
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000416"
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成
  このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してサブスクリプションを作成します。 このレッスンを薦めるには、前のレッスンである「 [レッスン 1: トランザクション レプリケーションを使用したデータのパブリッシュ](lesson-1-publishing-data-using-transactional-replication.md)」を完了している必要があります。  
  
### <a name="to-create-the-subscription"></a>サブスクリプションを作成するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** パブリケーションを右クリックして、 **[新しいサブスクリプション]** をクリックします。  
  
     サブスクリプションの新規作成ウィザードが起動します。  
  
3.  [パブリケーション] ページで **[AdvWorksProductTrans]** を選択し、 **[次へ]** をクリックします。  
  
4.  [ディストリビューション エージェントの場所] ページで、 **[ディストリビューターですべてのエージェントを実行する]** を選択し、 **[次へ]** をクリックします。  
  
5.  [サブスクライバー] ページにサブスクライバー インスタンスの名前が表示されない場合は、 **[サブスクライバーの追加]**、 **[SQL Server サブスクライバーの追加]** の順にクリックし、 **[サーバーの接続]** ダイアログ ボックスにサブスクライバー インスタンス名を入力して、 **[接続]** をクリックします。  
  
6.  [サブスクライバー] ページで、サブスクライバーサーバーのインスタンス名を選択し、[**サブスクリプションデータベース**] の [ ** \< 新しいデータベース>** ] を選択します。  
  
7.  **[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに「 **ProductReplica** 」と入力し、 **[OK]** をクリックして **[次へ]** をクリックします。  
  
8.  [**セキュリティのディストリビューションエージェント**] ダイアログボックスで、省略記号ボタン ([**..**.]) をクリックし、[ \< **プロセスアカウント**] ボックスに「 _Machine_Name>_ **\ repl_distribution** 」と入力します。このアカウントのパスワードを入力し、[ **OK**] をクリックして、[**次へ**] をクリックします。  
  
9. 以降のページでは既定値をそのまま採用し、 **[完了]** をクリックしてウィザードを終了します。  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>サブスクライバー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続します。次に、 **[データベース]**、 **[ProductReplica]**、 **[セキュリティ]** の順に展開し、 **[ユーザー]** を右クリックして、 **[新しいユーザー]** をクリックします。  
  
2.  **[全般]** ページの **[ユーザーの種類]** ボックスの一覧の **[Windows ユーザー]** をクリックします。  
  
3.  [**ユーザー名**] ボックスを選択し、省略記号ボタン ([...]) をクリックします。 [**選択するオブジェクト名を入力**してください] ボックスに <Machine_Name>**\ repl_distribution**] を入力し、[**名前の確認**] をクリックして、[ **OK**] をクリックします。  
  
4.  **[メンバーシップ]** ページの **[データベース ロールのメンバーシップ]** 領域で、 **[db_owner]** を選択し、 **[OK]** をクリックしてユーザーを作成します。  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>サブスクリプションの同期状態を表示するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーで、 **AdvWorksProductTrans** パブリケーションを展開し、 **ProductReplica** データベースのサブスクリプションを右クリックして、 **[同期の状態の表示]** をクリックします。  
  
     サブスクリプションの現在の同期状態が表示されます。  
  
3.  **[AdvWorksProductTrans]** の下にサブスクリプションが表示されない場合は、F5 キーを押して一覧を更新します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、トランザクション パブリケーションへのサブスクリプションを作成しました。 このサブスクリプションのディストリビューション エージェントは常時動作しているので、サブスクリプションの作成時に初期化も行われます。 次は、トレーサー トークンを使って、変更内容がサブスクライバーにレプリケートされているかどうかを確認し、待機時間を決定します。 「 [レッスン 3: サブスクリプションの検証と待機時間の計測](lesson-3-validating-the-subscription-and-measuring-latency.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)   
 [プッシュサブスクリプションを作成する](create-a-push-subscription.md)   
 [Subscribe to Publications](subscribe-to-publications.md)  
  
  
