---
title: チューニング推奨設定の表示 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: e4e690c9-434f-4b01-b4de-0b905323ddd6
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 634534fb9fa7f97e61431a481ab847bd87e2806a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-1-2---viewing-tuning-recommendations"></a>レッスン 1、2、チューニングの推奨設定を表示します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このタスクで作成したチューニング セッションを使用して[ワークロードのチューニング](../../tools/dta/lesson-1-1-tuning-a-workload.md)です。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] スクリプト MyScript.sql を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] データベースをチューニングすると、その結果が [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーの **[推奨設定]** タブに表示されます。次の作業では、 **チューニング アドバイザーのグラフィカル ユーザー インターフェイス (GUI) の** [推奨設定] [!INCLUDE[ssDE](../../includes/ssde-md.md)] タブについて学習し、このタブに表示されるチューニング セッションの結果について検証します。  
  
### <a name="view-tuning-recommendations"></a>チューニング推奨設定の表示  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーを起動します。 「 [データベース エンジン チューニング アドバイザーの起動](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md)」を参照してください。 「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ワークロードのチューニング [」の実習で使用した](../../tools/dta/lesson-1-1-tuning-a-workload.md)インスタンスに接続していることを確認します。  
  
2.  **[セッション モニター]** ペインの **[MySession]** をダブルクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]チューニング アドバイザーの以前のチューニング セッションからセッション情報を読み込み、表示、**の推奨事項**タブです。チューニング オプションをすべて既定値に設定しており、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [チューニング オプション] **タブで** [パーティション分割なし] **を選択しているため、** チューニング アドバイザーの **[推奨パーティション]** には何も表示されません。  
  
3.  **[推奨設定]** タブで、 **[推奨インデックス]** のすべての列を表示するには、このページの下部にあるスクロール バーを使用します。 各行は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーによって削除または作成が推奨されているデータベース オブジェクト (インデックスまたはインデックス ビュー) です。 右端の列までスクロールし、 **[定義]**をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]チューニング アドバイザーが表示されます、 **SQL スクリプトのプレビュー**ウィンドウを表示することができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトを作成するか、その行に、データベース オブジェクトを削除します。 **[閉じる]** をクリックし、プレビュー ウィンドウを閉じます。  
  
    リンクを含む **[定義]** を見つけにくい場合は、タブ付きページの下部にある **[既存のオブジェクトを表示する]** チェック ボックスをオフにすると、表示される行数が少なくなり、 推奨設定が生成されたオブジェクトのみが [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーに表示されます。 **[既存のオブジェクトを表示する]** チェック ボックスをオンにすると、現在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに存在するすべてのデータベース オブジェクトが表示されます。 タブ ページ右側のスクロール バーを使用し、すべてのオブジェクトを表示します。  
  
4.  **[推奨インデックス]** ペインのグリッドを右クリックします。 このとき表示されるメニューでは、推奨設定を選択または選択解除できます。 また、グリッド テキストのフォントも変更できます。  
  
5.  **[アクション]** メニューの **[推奨設定の保存]** をクリックし、すべての推奨設定を 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトに保存します。 このスクリプトの名前として、「 **MySessionRecommendations.sql**」と入力します。  
  
    [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターで MySessionRecommendations.sql を開き、スクリプトを表示します。 クエリ エディターでこのスクリプトを実行すれば、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースに推奨設定を適用することができますが、ここでは実行しません。 クエリ エディターのスクリプトを実行せずに閉じます。  
  
    また、 **チューニング アドバイザーの** [アクション] **メニューで** [推奨設定の適用] [!INCLUDE[ssDE](../../includes/ssde-md.md)] をクリックし、推奨設定を適用することもできます。しかし、この演習ではこれらの推奨設定は適用しません。  
  
6.  **[推奨設定]** タブに複数の推奨が存在する場合は、 **[推奨インデックス]** グリッドにデータベース オブジェクトが一覧表示されます。この中のいくつかの行をオフにします。  
  
7.  **[アクション]** メニューの **[推奨設定の評価]**をクリックします。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 新しいチューニング セッションが作成されます。ここで、MySession の元の推奨設定の一部を評価することができます。  
  
8.  新しいセッションの **[セッション名]** に「 **EvaluateMySession**」と入力し、ツール バーの **[分析の開始]** ボタンをクリックします。 この新しいセッションに対して手順 2. ～ 3. を繰り返し、推奨設定を表示します。  
  
## <a name="summary"></a>概要  
MySession チューニング セッションの内容を **[推奨設定]** タブに表示し、新しい EvaluateMySession チューニング セッションでその推奨設定の一部を評価しました。  
  
チューニング セッションを実行した後で、チューニング オプションを変更する必要があるとわかった場合は、チューニング推奨設定の一部を評価することができます。 たとえば、最初は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーでインデックス付きビューを考慮するようにチューニング オプションを指定したものの、推奨設定を生成した後で、やはりインデックス付きビューを使用しないことにしたとします。 このような場合、 **[アクション]** メニューの **[推奨設定の評価]** を使用すれば、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザーでインデックス付きビューを考慮せずにセッションを再評価することができます。 **[推奨設定の評価]** を実行すると、以前に生成した推奨設定が現在の物理構造に仮想的に適用され、その状態から次のチューニング セッションを実行できるようになります。  
  
チューニング結果の詳細な情報は、このレッスンの次の作業で説明する **[レポート]** タブに表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[チューニング レポートの表示](../../tools/dta/lesson-1-3-viewing-tuning-reports.md)  
  
  
  
