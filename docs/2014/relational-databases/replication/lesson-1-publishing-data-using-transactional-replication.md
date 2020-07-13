---
title: 'レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
author: rothja
ms.author: jroth
ms.openlocfilehash: ff715b51a7fa84a462d1439e78627d648e20472d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065955"
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a>レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ
   このレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してトランザクション パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Product** テーブルからフィルター選択したサブセットをパブリッシュします。 また、ディストリビューション エージェントにより使用される SQL Server ログインをパブリケーション アクセス リスト (PAL) に追加します。 このチュートリアルを行うには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
### <a name="to-create-a-publication-and-define-articles"></a>パブリケーションを作成し、アーティクルを定義するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを右クリックして、 **[新しいパブリケーション]** をクリックします。  
  
     パブリケーションの新規作成ウィザードが起動します。  
  
3.  [パブリケーション データベース] ページで [ [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、 **[次へ]** をクリックします。  
  
4.  [パブリケーションの種類] ページで **[トランザクション パブリケーション]** を選択し、 **[次へ]** をクリックします。  
  
5.  [アーティクル] ページで、 **[テーブル]** ノードを展開して **[Product]** チェック ボックスをオンにします。次に、 **[Product]** を展開して、 **[ListPrice]** チェック ボックスと **[StandardCost]** チェック ボックスをオフにします。 **[次へ]** をクリックします。  
  
6.  [テーブル行のフィルター選択] ページで、 **[追加]** をクリックします。  
  
7.  **[フィルターの追加]** ダイアログ ボックスで **[SafetyStockLevel]** 列をクリックし、右矢印をクリックして、フィルター選択クエリの Filter ステートメントの WHERE 句にこの列を追加します。さらに、WHERE 句を次のように変更します。  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  [**OK**] をクリックし、[**次へ**] をクリックします。  
  
9. **[スナップショットをすぐに作成し、サブスクリプションを初期化できるようにそのスナップショットを保持する]** チェック ボックスをオンにして、 **[次へ]** をクリックします。  
  
10. [エージェント セキュリティ] ページで、 **[スナップショット エージェントのセキュリティ設定を使用する]** チェック ボックスをオフにします。  
  
11. スナップショットエージェントの [**セキュリティの設定**] をクリックし、[ \<_Machine_Name> **プロセスアカウント**] ボックスに「_**\ repl_snapshot** 」と入力して、このアカウントのパスワードを入力し、[ **OK]** をクリックします。  
  
12. 同様に、ログ リーダー エージェントのプロセス アカウントとして repl_logreader を設定し、 **[完了]** をクリックします。  
  
13. [ウィザードの完了] ページで、 **[パブリケーション名]** ボックスに「 **AdvWorksProductTrans** 」と入力し、 **[完了]** をクリックします。  
  
14. パブリケーションが作成されたら、 **[閉じる]** をクリックしてウィザードを閉じます。  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>スナップショット生成の状態を表示するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** を右クリックして、 **[スナップショット エージェントの状態の表示]** をクリックします。  
  
3.  パブリケーションのスナップショット エージェントの現在の状態が表示されるので、 スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>ディストリビューション エージェントのログインを PAL に追加するには  
  
1.  でパブリッシャーに接続し、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーノードを展開して、[**レプリケーション**] フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、 **[AdvWorksProductTrans]** パブリケーションを右クリックして、 **[プロパティ]** をクリックします。  
  
     **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[パブリケーション アクセス リスト]** ページを選択して、 **[追加]** をクリックします。  
  
4.  **[パブリケーション アクセスの追加]** ダイアログ ボックスで、_<コンピューター名>_**\repl_distribution** を選択して **[OK]** をクリックし、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、トランザクション パブリケーションを作成しました。 次は、このパブリケーションをサブスクライブします。 「 [レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成](lesson-2-creating-a-subscription-to-the-transactional-publication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パブリッシュされたデータのフィルター処理](publish/filter-published-data.md)   
 [アーティクルの定義](publish/define-an-article.md)   
 [スナップショットの作成および適用](create-and-apply-the-snapshot.md)  
  
  
