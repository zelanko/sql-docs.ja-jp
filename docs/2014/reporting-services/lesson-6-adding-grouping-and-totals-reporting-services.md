---
title: 'レッスン 6: グループと合計の追加 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5607dfb046e7f50eb3a015e1f4f13711256435a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108412"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>レッスン 6: グループと合計の追加 (Reporting Services)
  レポートにグループと合計を追加すると、データを整理して要約できます。  
  
 累計をレポートに追加する方法の詳細については、「 [Reporting Services (SSRS) レポートへの合計の追加](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/)」を参照してください。  
  
 **このトピックの内容:**  
  
-   [レポートのデータをグループ化するには](#bkmk_groupdata)  
  
-   [レポートに合計を追加するには](#bkmk_addtotals)  
  
-   [レポートに日単位の合計を追加するには](#bkmk_adddailytotal)  
  
-   [レポートに総計を追加するには](#bkmk_addgrandtotal)  
  
-   [レポートをレポートサーバーにパブリッシュするには (省略可能)](#bkmk_publishreport)  
  
##  <a name="bkmk_groupdata"></a>レポートのデータをグループ化するには  
  
1.  
  **[デザイン]** タブをクリックします。  
  
2.  **行グループ**ペインが表示されない場合は、デザイン画面を右クリックして [**表示**] をクリックし、[**グループ化**] をクリックします。  
  
3.  
  **[レポート データ]** ウィンドウから、`Date` フィールドを **[行グループ]** ウィンドウにドラッグします。 
  **(詳細)** 行の上に配置します。  
  
     グループを示す角かっこが行ハンドルに表示されます。 テーブルにも 2 つの日付列が表示されます (点線の両側に 1 つずつ)。  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  
  **[レポート データ]** ウィンドウから、`Order` フィールドを **[行グループ]** ウィンドウにドラッグします。 
  **(詳細)** の上、Date の下に配置します。  
  
     2 つのグループを示す 2 個の角かっこが行ハンドルに表示されます。 テーブルにも2つ`Order`の列があります。  
  
5.  二重線の 右側 にある元の Date 列と **Order** 列を削除します。 これにより、この個別のレコード値が削除されるので、グループ値のみが表示されます。 2 つの列の列ハンドルを選択し、右クリックして **[列の削除]** をクリックします。  
  
     ![削除する列の選択](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "削除する列の選択")  
  
     列ヘッダーと日付の書式をもう一度設定できます。  
  
6.  
  **[プレビュー]** タブに切り替えて、レポートをプレビューします。 この画面は次の図のようになります。  
  
     ![Date、次に Order でグループ化されたテーブル](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Date、次に Order でグループ化されたテーブル")  
  
##  <a name="bkmk_addtotals"></a>レポートに合計を追加するには  
  
1.  デザイン ビューに切り替えます。  
  
2.  
  `[LineTotal]`フィールドが含まれるデータ領域セルを右クリックし、 **[合計の追加]** をクリックします。  
  
     各注文の合計金額を示す行が追加されます。  
  
3.  
  `[Qty]`フィールドが含まれるセルを右クリックし、 **[合計の追加]** をクリックします。  
  
     各注文の合計数量が合計行に追加されます。  
  
4.  
  `Sum[Qty]`の左側にある空のセルに、ラベルを「**注文合計**」と入力します。  
  
5.  合計行に背景色を追加できます。 2 つの合計セルとラベル セルを選択します。  
  
6.  
  **[書式]** メニューの **[背景色]** をクリックし、 **[淡い灰色]** をクリックして、 **[OK]** をクリックします。  
  
     ![[デザイン] ビュー: 注文合計がある基本的なテーブル](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "[デザイン] ビュー: 注文合計がある基本的なテーブル")  
  
##  <a name="bkmk_adddailytotal"></a>レポートに日単位の合計を追加するには  
  
1.  
  Order セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。  
  
     これにより、各日の数量と金額の合計を含む新しい行と、[Order] 列に "**Total**" というラベルが追加されます。  
  
2.  同じセルで「**合計**」の前に「**毎日**」と入力し、[**毎日の合計**] を読み取ります。  
  
3.  
  **[毎日の合計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  
  **[書式]** メニューの **[背景色]** をクリックし、 **[オレンジ]** をクリックして、 **[OK]** をクリックします。  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="bkmk_addgrandtotal"></a>レポートに総計を追加するには  
  
1.  Date セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。  
  
     これにより、レポート全体の数量と金額の合計と、 `Date`列の**合計**ラベルを含む新しい行が追加されます。  
  
2.  同じセルで **「合計」** の代わりに **「総計」** と入力し、 **[総計]** と表示します。  
  
3.  
  **[総計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  
  **[書式]** メニューの **[背景色]** をクリックし、 **[薄い青]** をクリックして、 **[OK]** をクリックします。  
  
     ![[デザイン] ビュー: 基本的なテーブルの総計](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "[デザイン] ビュー: 基本的なテーブルの総計")  
  
5.  [プレビュー] をクリックします。  
  
     最終的なページは次のようになります。  
  
     ![プレビュー: 総計がある基本的なテーブル](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "プレビュー: 総計がある基本的なテーブル")  
  
##  <a name="bkmk_publishreport"></a>レポートをレポートサーバーにパブリッシュするには (省略可能)  
  
1.  オプションの手順では、完成したレポートをネイティブ モードのレポート サーバーにパブリッシュして、レポート マネージャーでレポートを表示できるようにします。  
  
2.  ツール バーの **[プロジェクト]** をクリックし、 **[チュートリアルのプロパティ]** をクリックします。  
  
3.  **TargetServerURL**に、レポートサーバーの名前を入力します。たとえば、 **http://\<servername>/reportserver**のように入力します。  
  
4.  [**OK**] をクリックします。  
  
5.  ツール バーの **[ビルド]** をクリックし、 **[Tutorial の配置]** をクリックします。  
  
     出力ウィンドウに次のようなメッセージが表示されていれば、正常に展開されたことを示しています。  
  
    > ------ ビルド開始: プロジェクト: tutorial、構成: デバッグ ------'Sales Orders.rdl' をスキップしています。 項目は最新です。ビルド完了--0 エラー、0警告------配置開始: プロジェクト: チュートリアル、構成: デバッグ------http://\<サーバー名に配置する>、レポート '/tutorial/Sales Orders ' を配置します。配置完了--0 エラー、0個の警告 = = = = = = = = = = ビルド: 1 成功または最新の状態、0失敗、0スキップ = = = = = = = = = = =、1成功、0失敗、0スキップ = = = = = = = = = = = = = = = = =  
  
     次のようなメッセージが表示されている場合は、レポート サーバーに対する権限があることと、管理者特権を使用して [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を開始したことを確認してください。  
  
    > "ユーザー ' XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX\\<ユーザー名\>' に付与されたアクセス許可は、この操作を実行するのに十分ではありません"  
  
6.  管理者特権を使用してレポートマネージャーを開始します。たとえば、Internet Explorer のアイコンを右クリックし、[**管理者として実行**] をクリックします。  
  
     レポート マネージャーの URL (たとえば `http://<server name>/reports`) を参照します。  
  
7.  レポートを含むフォルダーを参照し、レポート `Sales Orders` の名前をクリックして、表示レポートをブラウザーで表示します。  
  
## <a name="next-steps"></a>次の手順  
 これで、「基本的なテーブル レポートの作成」チュートリアルを終了します。  
  
## <a name="see-also"></a>参照  
 [データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
