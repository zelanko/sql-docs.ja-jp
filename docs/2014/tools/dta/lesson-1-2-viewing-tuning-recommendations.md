---
title: チューニングに関する推奨事項の表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d0ab03b5152b0fe3f12de5e31b091b49d86cd4d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048359"
---
# <a name="viewing-tuning-recommendations"></a>チューニング推奨設定の表示
   ここでは、「[ワークロードのチューニング](lesson-1-1-tuning-a-workload.md)」で作成したチューニング セッションを使用します。 Myscript.sql スクリプトを使用してデータベースをチューニングすると、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] チューニングアドバイザーの [ [!INCLUDE[ssDE](../../includes/ssde-md.md)] **推奨**設定] タブに結果が表示されます。次のタスクでは**Recommendations** 、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニングアドバイザーのグラフィカルユーザーインターフェイス (GUI) の [推奨設定] タブについて説明し、チューニングセッションの結果について説明している情報を紹介します。  
  
### <a name="view-tuning-recommendations"></a>チューニング推奨設定の表示  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーを起動します。 「 [データベース エンジン チューニング アドバイザーの起動](../../relational-databases/performance/database-engine-tuning-advisor.md)」を参照してください。 「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ワークロードのチューニング [」の実習で使用した](lesson-1-1-tuning-a-workload.md)インスタンスに接続していることを確認します。  
  
2.  **[セッション モニター]** ペインの **[MySession]** をダブルクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]チューニングアドバイザーによって、前のチューニングセッションからセッション情報が読み込まれ、[**推奨**設定] タブが表示されます。チューニングアドバイザーでは、チューニング [!INCLUDE[ssDE](../../includes/ssde-md.md)] オプションの既定値をすべて受け入れ、[**チューニングオプション**] タブでパーティション分割が選択されて**い**ないため、**パーティションの推奨事項**はありません。  
  
3.  **[推奨設定]** タブで、 **[推奨インデックス]** のすべての列を表示するには、このページの下部にあるスクロール バーを使用します。 各行は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーによって削除または作成が推奨されているデータベース オブジェクト (インデックスまたはインデックス ビュー) です。 右端の列までスクロールし、 **[定義]** をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]**[SQL スクリプトのプレビュー]** ウィンドウが表示されます。このウィンドウには、その行のデータベース オブジェクトを作成または削除する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトが表示されます。 **[閉じる]** をクリックし、プレビュー ウィンドウを閉じます。  
  
     リンクを含む **[定義]** を見つけにくい場合は、タブ付きページの下部にある **[既存のオブジェクトを表示する]** チェック ボックスをオフにすると、表示される行数が少なくなり、 推奨設定が生成されたオブジェクトのみが [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーに表示されます。 **[既存のオブジェクトを表示する]** チェック ボックスをオンにすると、現在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに存在するすべてのデータベース オブジェクトが表示されます。 タブ ページ右側のスクロール バーを使用し、すべてのオブジェクトを表示します。  
  
4.  **[推奨インデックス]** ペインのグリッドを右クリックします。 このとき表示されるメニューでは、推奨設定を選択または選択解除できます。 また、グリッド テキストのフォントも変更できます。  
  
5.  **[アクション]** メニューの **[推奨設定の保存]** をクリックし、すべての推奨設定を 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトに保存します。 スクリプトに `MySessionRecommendations.sql` という名前を付けます。  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターで MySessionRecommendations.sql を開き、スクリプトを表示します。 クエリ エディターでこのスクリプトを実行すれば、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースに推奨設定を適用することができますが、ここでは実行しません。 クエリ エディターのスクリプトを実行せずに閉じます。  
  
     また、 **チューニング アドバイザーの** [アクション] **メニューで** [推奨設定の適用] [!INCLUDE[ssDE](../../includes/ssde-md.md)] をクリックし、推奨設定を適用することもできます。しかし、この演習ではこれらの推奨設定は適用しません。  
  
6.  **[推奨設定]** タブに複数の推奨が存在する場合は、 **[推奨インデックス]** グリッドにデータベース オブジェクトが一覧表示されます。この中のいくつかの行をオフにします。  
  
7.  **[アクション]** メニューの **[推奨設定の評価]** をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 新しいチューニング セッションが作成されます。ここで、MySession の元の推奨設定の一部を評価することができます。  
  
8.  `EvaluateMySession`新しい**セッション名**として「」と入力し、ツールバーの [**分析の開始**] ボタンをクリックします。 この新しいセッションに対して手順 2. ～ 3. を繰り返し、推奨設定を表示します。  
  
## <a name="summary"></a>まとめ  
 MySession チューニング セッションの内容を **[推奨設定]** タブに表示し、新しい EvaluateMySession チューニング セッションでその推奨設定の一部を評価しました。  
  
 チューニング セッションを実行した後で、チューニング オプションを変更する必要があるとわかった場合は、チューニング推奨設定の一部を評価することができます。 たとえば、最初は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーでインデックス付きビューを考慮するようにチューニング オプションを指定したものの、推奨設定を生成した後で、やはりインデックス付きビューを使用しないことにしたとします。 次に、[**アクション**] メニューの [推奨設定の**評価**] オプションを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インデックス付きビューを考慮せずに、チューニングアドバイザーでセッションを再評価することができます。 **[推奨設定の評価]** を実行すると、以前に生成した推奨設定が現在の物理構造に仮想的に適用され、その状態から次のチューニング セッションを実行できるようになります。  
  
 チューニング結果の詳細な情報は、このレッスンの次の作業で説明する **[レポート]** タブに表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [チューニング レポートの表示](lesson-1-3-viewing-tuning-reports.md)  
  
  
