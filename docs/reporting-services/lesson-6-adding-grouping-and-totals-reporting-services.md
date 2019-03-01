---
title: 'レッスン 6: グループと合計の追加 (Reporting Services) | Microsoft Docs'
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 24d21ae735b44a7068ca929515b66e8a33aade8d
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290080"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>レッスン 6: グループと合計の追加 (Reporting Services)
このチュートリアルのレッスンでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートにグループ化と合計を追加して、データを整理して要約します。  
  
  
## <a name="bkmk_groupdata"></a>レポート内のデータをグループ化するには  
  
1.  **[デザイン]** タブをクリックします。  
  
2.  **行グループ** ペインが表示されていない場合は、デザイン画面を右クリックして **[表示]** をクリックし、 **[グループ化]** をクリックします。  
  
3.  **レポート データ** ペインから **行グループ** ペインに **[Date]** フィールドをドラッグします。 **(詳細)** 行の上に配置します。
  
    グループを示す角かっこが行ハンドルに表示されます。 テーブルにも 2 つの日付列が表示されます (点線の両側に 1 つずつ)。  
  
    ![日付グループの追加](../reporting-services/media/rs-basictablegroups1design.png "日付グループの追加")  
  
4.  **レポート データ** ペインから **行グループ** ペインに **[Order]** フィールドをドラッグします。 **詳細**の上、日付の下に配置します。

    ![ssrs_ssdt_addorderfield](../reporting-services/media/ssrs-ssdt-addorderfield.png)   
  
    2 つのグループを示す場合、行ハンドルには 2 個の角かっこ ![ssrs_ssdt_rowgroupdoublehandles](../reporting-services/media/ssrs-ssdt-rowgroupdoublehandles.png) が表示されることに注意してください。 テーブルにも 2 つの **Order** 列が表示されます。  
  
5.  二重線の **右側** にある元の **Date** 列と **Order** 列を削除します。 これにより、この個別のレコード値が削除されるので、グループ値のみが表示されます。 2 つの列の列ハンドルを選択し、右クリックして **[列の削除]** をクリックします。  
  
    ![削除する列を選択する](../reporting-services/media/rs-basictablegroupsdeletecols.gif "削除する列を選択する")  
  
6.  新しい日付列の書式を設定するには、 `[Date]` フィールド式が入力されているセルを右クリックし、 **[テキスト ボックスのプロパティ]** をクリックします。  
  
7.  **[数値]** をクリックし、 **[カテゴリ]** フィールドで **[日付]** を選択します。  
  
8.  **[型]** ボックスで **[2000 年 1 月 31 日]** を選択します。  
  
9.  [!INCLUDE[clickOK](../includes/clickok-md.md)]をクリックします。  
  
10.  **[プレビュー]** タブに切り替えて、レポートをプレビューします。 この画面は次の図のようになります。  
    ![rs_BasicTableGroupsPreview](../reporting-services/media/rs-basictablegroupspreview.png) 
  
## <a name="bkmk_addtotals"></a>レポートに合計を追加するには  
  
1.  デザイン ビューに切り替えます。  
  
2.  `[LineTotal]`フィールドが含まれるデータ領域セルを右クリックし、 **[合計の追加]** をクリックします。  
  
    各注文の合計金額を示す行が追加されます。  
  
3.  `[Qty]`フィールドが含まれるセルを右クリックし、 **[合計の追加]** をクリックします。  
  
    各注文の合計数量が合計行に追加されます。  
  
4.  `Sum[Qty]`の左側にある空のセルに、ラベルを「**注文合計**」と入力します。  
  
5.  合計行に背景色を追加できます。 2 つの合計セルとラベル セルを選択します。  
  
6.  **[書式]** メニューの **[背景色]** をクリックし、 **[淡い灰色]** をクリックして、 **[OK]** をクリックします。  
  
    ![デザイン ビュー:注文合計がある基本的なテーブル](../reporting-services/media/rs-basictablesumlinetotaldesign.gif ":デザイン ビュー:注文合計がある基本的なテーブル")  
  
## <a name="bkmk_adddailytotal"></a>レポートに毎日の合計を追加するには  
  
1.  **Order** セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。  
  
    毎日の数量と金額の合計が含まれた新しい行と、"**合計**" ラベルが注文列の一番下に追加されます。  
  
2.  同じセルで **「合計」** の前に **「毎日の」** と入力し、 **[毎日の合計]** と表示します。  
  
3.  **[毎日の合計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  **[書式]** メニューの **[背景色]** をクリックし、 **[オレンジ]** をクリックして、 **[OK]** をクリックします。  
  
    ![背景色をオレンジ色に設定する](../reporting-services/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
## <a name="bkmk_addgrandtotal"></a>レポートに総計を追加するには  
  
1.  Date セルを右クリックし、 **[合計の追加]** をポイントして、 **[後]** をクリックします。  
  
    レポート全体の数量と金額の合計が含まれた新しい行と、 **[合計]** ラベルが **\[Date\]** 列に追加されます。  
  
2.  同じセルで **「合計」** の代わりに **「総計」** と入力し、 **[総計]** と表示します。  
  
3.  **[総計]** セル、2 個の **[合計]** セル、およびその間にある空のセルを選択します。  
  
4.  **[書式]** メニューの **[背景色]** をクリックし、 **[薄い青]** をクリックして、 **[OK]** をクリックします。  
  
    ![デザイン ビュー:基本的なテーブルの総計](../reporting-services/media/rs-basictablesumgrandtotaldesign.gif "デザイン ビュー:基本的なテーブルの総計")  
  
5.  **[プレビュー]** をクリックします。  
  
    最後のページは次の図のようになります。 ツール バーの [最終ページ] ![ssrs_ssdt_viewertoolbar_lastpage](../reporting-services/media/ssrs-ssdt-viewertoolbar-lastpage.png)ボタンをクリックします。   
  
    ![プレビュー:総計がある基本的なテーブル](../reporting-services/media/rs-basictablesumgrandtotalpreview.gif "プレビュー:総計がある基本的なテーブル")  
  
## <a name="bkmk_publishreport"></a>レポートをレポート サーバーにパブリッシュするには (オプション)  
  
1.  オプションの手順では、完成したレポートをネイティブ モードのレポート サーバーにパブリッシュして、Web ポータルでレポートを表示できるようにします。  
  
2.  **[プロジェクト]** メニューの **[Tutorial のプロパティ...]** をクリックします。  
  
3.  **TargetServerURL** に、レポート サーバーの名前を入力します。たとえば、次のように入力します。   
    - `http:/<servername>/reportserver`  
   
    - `https://localhost/reportserver` は、レポート サーバーでレポートを設計している場合に動作します。  
  
  
4. TargetReportFolder がチュートリアルのプロジェクトの名前であることに注意してください。  これは、次のステップでレポートが配置されるフォルダーの名前です。  
5. **[OK]** をクリックします。  
  
6.  **[ビルド]** メニューの **[Tutorial の配置]** をクリックします。  
  
    出力ウィンドウに次のようなメッセージが表示されていれば、正常に展開されたことを示しています。  
  
    > ------ ビルド開始:プロジェクト: tutorial、構成:デバッグ ------  
    > 'Sales Orders.rdl' をスキップしています。 アイテムは最新の状態です。  
    > ビルドの完了 -- エラー 0 個、警告 0 個  
    > ------ 配置開始:プロジェクト: tutorial、構成:デバッグ ------  
    > https://[server name]/reportserver に配置しています  
    > レポート '/tutorial/Sales Orders' を配置しています。  
    > 配置完了 -- エラー 0 個、警告 0 個  
    > ========== ビルド:1 正常終了または最新の状態、0 失敗、0 スキップ ==========  
    > ========== 配置:1 正常終了、0 失敗、0 スキップ ==========  
  
    次のようなメッセージが表示されている場合は、レポート サーバーに対する権限があることと、管理者特権を使用して [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を開始したことを確認してください。  
  
    > "ユーザー 'XXXXXXXX\\&lt;ユーザー名&gt;' には、この操作を行うのに必要な権限が許可されていません。"  
  
7.  管理者特権を使用して Web ポータルを参照します。たとえば、Internet Explorer アイコンを右クリックして **[管理者として実行]** をクリックします。  
  
    [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] Web ポータルの URL を参照します。   
    **注:** *ポータル* URL は "Reports" です。Report *Server* の URL "Reportserver" ではありません。  例 :   
    `https://<server name>/reports`  
    `https://localhost/reports` は、レポート サーバーでレポートを設計している場合に動作します。  
  
8.  レポートが含まれているフォルダーを参照します。 既定の名前の *tutorial*、プロジェクトの名前、またはプロジェクトのプロパティで TargetReportFolder フィールドに入力した名前です。   
レポートの名前 **Sales Orders** をクリックして、表示レポートをブラウザーで表示します。  
  
    ![ssrs_tutorial_tutorialfolder](../reporting-services/media/ssrs-tutorial-tutorialfolder.png)  
 
これで、「基本的なテーブル レポートの作成」チュートリアルを終了します。  
  
## <a name="see-also"></a>参照  
[データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
  

