---
title: 'レッスン 6: グループと合計の追加 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5a372f230cfc2fc63e59787b8f9b674928f72368
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095299"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Lesson 6: Adding Grouping and Totals (Reporting Services)
  レポートにグループと合計を追加すると、データを整理して要約できます。  
  
 レポートを実行中の合計を追加する方法については、curah.microsoft.com のキュレーションを参照してください: [Reporting Services (SSRS) レポートに合計を追加](http://go.microsoft.com/fwlink/p/?LinkId=403698)します。  
  
 **このトピックの内容:**  
  
-   [レポートのデータをグループ化](#bkmk_groupdata)  
  
-   [レポートに合計を追加するには](#bkmk_addtotals)  
  
-   [レポートに毎日の合計を追加するには](#bkmk_adddailytotal)  
  
-   [レポートに総計を追加するには](#bkmk_addgrandtotal)  
  
-   [(省略可能) レポート サーバーにレポートをパブリッシュするには](#bkmk_publishreport)  
  
##  <a name="bkmk_groupdata"></a> レポートのデータをグループ化  
  
1.  **[デザイン]** タブをクリックします。  
  
2.  表示されない場合、**行グループ**ウィンドウがデザイン サーフェイスを右クリックし、クリックして**ビュー**順にクリックします**グループ化**します。  
  
3.  **レポート データ**ウィンドウで、ドラッグ、`Date`フィールドを**行グループ**ウィンドウ。 **(詳細)** 行の上に配置します。  
  
     グループを示す角かっこが行ハンドルに表示されます。 テーブルにも 2 つの日付列が表示されます (点線の両側に 1 つずつ)。  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  **レポート データ**ウィンドウで、ドラッグ、`Order`フィールドを**行グループ**ウィンドウ。 **詳細**の上、日付の下に配置します。  
  
     2 つのグループを示す 2 個の角かっこが行ハンドルに表示されます。 テーブルに 2 つ`Order`列、すぎます。  
  
5.  元の日付と注文列を削除、**右**二重線の。 これにより、この個別のレコード値が削除されるので、グループ値のみが表示されます。 2 つの列の列ハンドルを選択し、右クリックして **[列の削除]** をクリックします。  
  
     ![削除する列を選択する](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "削除する列を選択する")  
  
     列ヘッダーと日付の書式をもう一度設定できます。  
  
6.  **[プレビュー]** タブに切り替えて、レポートをプレビューします。 この画面は次の図のようになります。  
  
     ![Date、次に Order でグループ化されたテーブル](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Date、次に Order でグループ化されたテーブル")  
  
##  <a name="bkmk_addtotals"></a> レポートに合計を追加するには  
  
1.  デザイン ビューに切り替えます。  
  
2.  `[LineTotal]`フィールドが含まれるデータ領域セルを右クリックし、 **[合計の追加]** をクリックします。  
  
     各注文の合計金額を示す行が追加されます。  
  
3.  `[Qty]`フィールドが含まれるセルを右クリックし、 **[合計の追加]** をクリックします。  
  
     各注文の合計数量が合計行に追加されます。  
  
4.  `Sum[Qty]`の左側にある空のセルに、ラベルを「**注文合計**」と入力します。  
  
5.  合計行に背景色を追加できます。 2 つの合計セルとラベル セルを選択します。  
  
6.  **[書式]** メニューの **[背景色]** をクリックし、 **[淡い灰色]** をクリックして、 **[OK]** をクリックします。  
  
     ![デザイン ビュー: 注文合計がある基本的なテーブル](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "デザイン ビュー: 注文合計がある基本的なテーブル")  
  
##  <a name="bkmk_adddailytotal"></a> レポートに毎日の合計を追加するには  
  
1.  注文セルを右クリックし、[**合計の追加**、] をクリック**後**します。  
  
     この、1 日におよび、ラベル、数量と金額の合計が含まれた新しい行を追加します"**合計**"が注文列。  
  
2.  同じセルで **「合計」** の前に **「毎日の」** と入力し、 **[毎日の合計]** と表示します。  
  
3.  **[毎日の合計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  **[書式]** メニューの **[背景色]** をクリックし、 **[オレンジ]** をクリックして、 **[OK]** をクリックします。  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="bkmk_addgrandtotal"></a> レポートに総計を追加するには  
  
1.  日付セルを右クリックし、 **[合計の追加]** をポイントして、 **[指定日付より後]** をクリックします。  
  
     レポート全体の数量と金額の合計が含まれた新しい行が追加されます、**合計**でラベル付け、`Date`列。  
  
2.  同じセルで **「合計」** の代わりに **「総計」** と入力し、 **[総計]** と表示します。  
  
3.  **[総計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  **[書式]** メニューの **[背景色]** をクリックし、 **[薄い青]** をクリックして、 **[OK]** をクリックします。  
  
     ![デザイン ビュー: 基本的なテーブルの総計](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "デザイン ビュー: 基本的なテーブルの総計")  
  
5.  [プレビュー] をクリックします。  
  
     最終的なページは次のようになります。  
  
     ![プレビュー: 総計がある基本的なテーブルの](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "プレビュー: 総計がある基本的なテーブル")  
  
##  <a name="bkmk_publishreport"></a> (省略可能) レポート サーバーにレポートをパブリッシュするには  
  
1.  オプションの手順では、完成したレポートをネイティブ モードのレポート サーバーにパブリッシュして、レポート マネージャーでレポートを表示できるようにします。  
  
2.  ツール バーの **[プロジェクト]** をクリックし、 **[チュートリアルのプロパティ]** をクリックします。  
  
3.  **TargetServerURL**など、レポート サーバーの名前の名前を入力**http://\<servername >/reportserver**  
  
4.  **[OK]** をクリックします。  
  
5.  ツール バーの **[ビルド]** をクリックし、 **[チュートリアルの配置]** をクリックします。  
  
     出力ウィンドウに次のようなメッセージが表示されていれば、正常に展開されたことを示しています。  
  
    > ------ ビルド開始: プロジェクト: tutorial、構成: デバッグ ------'Sales Orders.rdl' をスキップしています。 項目が最新の状態です。ビルドの完了--エラー 0、0 件の警告---配置開始: プロジェクト: tutorial、構成: デバッグ--- http:// へのデプロイ\<サーバー名 >/reportserverDeploying 報告 ' チュートリアル/Sales Orders'。配置完了--エラー 0、0 件の警告ステージ ビルド: 1 正常終了または最新、0 失敗、0 スキップ ステージの展開: 1 正常終了、0 失敗、0 スキップ ステージ  
  
     次のようなメッセージが表示されている場合は、レポート さーばーに対する権限があることと、管理者特権を使用して [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を開始したことを確認してください。  
  
    > "ユーザーに付与されるアクセス許可 'XXXXXXXX\\< ユーザー名\>' 不十分なため、この操作を実行する"  
  
6.  たとえば、管理者特権を持つレポート マネージャーを起動、Internet Explorer のアイコンを右クリックしておよびクリックして**管理者として実行**します。  
  
     レポート マネージャーの URL (たとえば `http://<server name>/reports`) を参照します。  
  
7.  レポートを含むフォルダーを参照して、レポートの名前をクリックします。 `Sales Orders` 、ブラウザーでレンダリングされたレポートを表示します。  
  
## <a name="next-steps"></a>次の手順  
 これで、「基本的なテーブル レポートの作成」チュートリアルを終了します。  
  
## <a name="see-also"></a>参照  
 [フィルター、グループ、およびデータの並べ替え&#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
