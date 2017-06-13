---
title: "レッスン 4: レポート (Reporting Services) をテーブルの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
caps.latest.revision: 64
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 76224139b629d797735b88bfcc692a1e8abce336
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a>レッスン 4 : レポートへのテーブルの追加 (Reporting Services)
データセットを定義したら、レポートのデザインを開始できます。 レポートのレイアウトを作成するには、データ領域、テキスト ボックス、画像、およびレポートに含めるその他のアイテムを、デザイン画面にドラッグ アンド ドロップします。  
  
基になるデータセットからデータ行を繰り返し表示するアイテムを *データ領域*と呼びます。 基本的なレポートのデータ領域は 1 つだけですが、表形式のレポートにグラフを追加する場合には、データ領域を追加できます。 データ領域を追加したら、そのデータ領域にフィールドを追加できます。  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a>[テーブル] データ領域とフィールドをレポート レイアウトに追加するには  
  
1.  **[ツールボックス]**で **[テーブル]**をクリックし、デザイン画面内をクリックして、マウスをドラッグします。 デザイン画面の中央に 3 列のテーブル データ領域が作成されます。 **[レポート データ]** ペインの左側に **[ツールボックス]** タブが表示されます。 **[ツールボックス]**を開くには、ポインターを **[ツールボックス]** タブの上に移動させます。 **[ツールボックス]** が表示されない場合は、 **[表示]** メニューの **[ツールボックス]**をクリックします。
  
     ![ssrs_ssdt_addtable](../reporting-services/media/ssrs-ssdt-addtable.png) 
  
  デザイン画面からレポートにテーブルを追加することもできます。  デザイン画面を右クリックし、 **[挿入]** 、 **[テーブル]**の順にクリックします。
2.  **[レポート データ]** ペインで、 **AdventureWorksDataset** データセットを展開してフィールドを表示します。  
  
3.  *[Date]* フィールドを、 **[レポート データ]** ペインからテーブルの最初の列にドラッグします。  
  
    フィールドを最初の列にドラッグすると、2 つの処理が行われます。 1 つは、 *フィールド式*と呼ばれるフィールド名が `[Date]`のように角かっこで囲まれてデータ セルに表示されます。 2 つ目は、列ヘッダー値が [ヘッダー] 行 (フィールド式のすぐ上) に自動的に追加されます。 既定では、この列がフィールド名になります。 ヘッダー行のテキストを選択し、新しい名前を入力することができます。  
  
4.  *[Order]* フィールドを、 **[レポート データ]** ペインからテーブルの 2 番目の列にドラッグします。  
  
5.  *[Product]* フィールドを、 **[レポート データ]** ペインからテーブルの 3 番目の列にドラッグします。  
  
6.  [Qty] フィールドを、3 番目の列の右端沿いに、垂直方向のカーソルとマウス ポインターが正符号 [+] になるまでドラッグします。 マウス ボタンを離すと `[Qty]`の 4 番目の列が作成されます。  
![ssrs_tutorial_addcolumn](../reporting-services/media/ssrs-tutorial-addcolumn.png)  
  
7.  同様に [明細小計] フィールドを追加して、5 番目の列を作成します。 列ヘッダーは [Line Total] です。 レポート デザイナーは、LineTotal を 2 つの語に分割して、列の表示名を自動的に作成します。  
  
  
次の図は、[Date]、[Order]、[Product]、[Qty]、および [Line Total] の各フィールドを使用して作成したテーブル データ領域を示しています。  
![rs_BasicTableDetailsDesign](../reporting-services/media/rs-basictabledetailsdesign.png)  
  
## <a name="preview-your-report"></a>レポートをプレビューする  
レポートをプレビューすると、最初にレポート サーバーにパブリッシュする必要なしに、表示レポートを表示できます。 デザイン時にレポートを頻繁にプレビューできます。 レポートをプレビューするとデザインとデータ接続の検証が実行されるため、エラーと問題を修正した後にレポートをレポート サーバーにパブリッシュできます。  
  
#### <a name="to-preview-a-report"></a>レポートをプレビューするには  
  
-   **[プレビュー]** タブをクリックします。 レポート デザイナーによりレポートが実行され、[プレビュー] ビューに表示されます。
![ssrs_ssdt_preview](../reporting-services/media/ssrs-ssdt-preview.png)  
  
    [プレビュー] ビューに表示されたレポートの一部を次の図に示します。  
  
    ![プレビュー、5 つの列を含むテーブルの詳細行](../reporting-services/media/rs-basictabledetailspreview.png "プレビュー、5 つの列を含むテーブルの詳細行")  
  
    通貨 ([Line Total] 列) は小数点以下 6 桁まで表示され、日付にはタイム スタンプが付いています。 次のレッスンで書式設定を修正します。  
  
> [!NOTE]  
> **[ファイル]** メニューの **[すべてを保存]** をクリックして、レポートを保存します。  
  
## <a name="next-steps"></a>次の手順  
[テーブル] データ領域がレポートに、フィールドがデータ領域にそれぞれ正しく追加され、レポートが正しくプレビューされました。 次は、列ヘッダー、日付、および通貨の値の書式を設定します。 「[レッスン 5: レポートの書式設定 (Reporting Services)](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[テーブル &#40;レポート ビルダーおよび SSRS&#41;](../reporting-services/report-design/tables-report-builder-and-ssrs.md)  
[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  

