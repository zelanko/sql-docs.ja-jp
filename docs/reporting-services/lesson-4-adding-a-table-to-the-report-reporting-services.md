---
title: レッスン 4:テーブルをレポートに追加する | Microsoft Docs
description: データセットを定義したら、ページ分割されたレポートのデザインを開始できます。 レポート オブジェクトを [ツールボックス] ウィンドウからデザイン画面にドラッグ アンド ドロップすることで、レポートのレイアウトを作成します。
ms.date: 12/16/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fca89bf8992db9ec3b07cea422ec146993e8aec8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75244300"
---
# <a name="lesson-4-add-a-table-to-the-report-reporting-services"></a>レッスン 4:テーブルをレポートに追加する (Reporting Services)

データセットを定義したら、ページ分割されたレポートのデザインを開始できます。 *レポート オブジェクト*を **[ツールボックス]** ウィンドウから**デザイン画面**にドラッグ アンド ドロップすることで、レポートのレイアウトを作成します。 レポート オブジェクトの種類をいくつか挙げます。

- テーブル
- テキスト ボックス
- Image
- Line
- Rectangle
- グラフ
- マップ

基になるデータセットからデータ行を繰り返し表示するアイテムを *データ領域*と呼びます。 データ領域を追加したら、そのデータ領域にフィールドを追加できます。 基本的なレポートにはデータ領域が 1 つのみ存在します。 追加することで、グラフなどより多くの情報を表示することができます。

## <a name="add-a-table-data-region-and-fields-to-a-report-layout"></a>テーブル データ領域とフィールドをレポート レイアウトに追加する

1. レポート デザイナーの左側のウィンドウにある **[ツールボックス]** タブを選択します。 マウスで **[テーブル]** オブジェクトを選択し、レポートのデザイン画面にドラッグします。 デザイン画面の中央に 3 列のテーブル データ領域が作成されます。 **[ツールボックス]** タブが表示されない場合は、 **[表示]** メニュー > **[ツールボックス]** の順に選択します。

    ![ssrs_ssdt_addtable](media/ssrs-ssdt-addtable.png)

    デザイン画面からレポートにテーブルを追加することもできます。 デザイン画面を右クリックし **[挿入]**  >  **[テーブル]** の順に選択します。

2. **[レポート データ]** ウィンドウで、AdventureWorksDataset を展開してフィールドを表示します。

3. **[レポート データ]** ウィンドウから `[Date]` フィールドをテーブルの最初の列にドラッグします。

    > [!IMPORTANT]
    > フィールドを最初の列にドラッグすると、2 つの処理が行われます。 最初に、レポート デザイナーにより*フィールド式*と呼ばれるフィールド名が `[Date]` のように角かっこで囲まれてデータ セルに表示されます。 次に、列ラベルがヘッダー行 (フィールド式のすぐ上) に追加されます。 既定では、この列ラベルがフィールド名になります。 変更したい場合は、列ラベルを選択して新しい値を入力します。

4. **[レポート データ]** ウィンドウから `[Order]` フィールドをテーブルの 2 番目の列にドラッグします。

5. **[レポート データ]** ウィンドウから `[Product]` フィールドをテーブルの 3 番目の列にドラッグします。

6. `[Qty]` フィールドを、3 番目の列の右端沿いに、垂直方向のカーソルとマウス ポインターが正符号 [+] になるまでドラッグします。 マウス ボタンを離すと `[Qty]` フィールド式の 4 番目の列が作成されます。

    ![ssrs_tutorial_addcolumn](media/ssrs-tutorial-addcolumn.png)

7. 同様に [`[LineTotal]`] フィールドを追加して、5 番目の列を作成します。 列ラベルが [Line Total] として追加されます。 レポート デザイナーにより、"LineTotal" を 2 つの語に分割して列のフレンドリ名が自動的に作成されます。

次の図は、次のフィールドを使って設定されたテーブル データ領域を示しています:Date、Order、Product、Qty、および Line Total です。
![rs_BasicTableDetailsDesign](media/rs-basictabledetailsdesign.png)

## <a name="preview-your-report"></a>レポートをプレビューする

レポートをプレビューすると、最初にレポート サーバーにパブリッシュする必要なしに、表示レポートを表示できます。 デザイン時にレポートを頻繁にプレビューできます。 これにより、デザインとデータ接続を検証して、エラーや問題を段階的に修正できます。

### <a name="to-preview-a-report"></a>レポートをプレビューするには

- **[プレビュー]** タブを選択します。レポート デザイナーによりレポートが実行され、 **[プレビュー]** ビューに表示されます。

    ![ssrs_ssdt_preview](media/ssrs-ssdt-preview.png)

**[プレビュー]** ビューに表示されたレポートの一部を次の図に示します。

   ![プレビュー、列が 5 つあるテーブルの詳細行](media/rs-basictabledetailspreview.png "プレビュー、列が 5 つあるテーブルの詳細行")

[Date] と [Line Total] の値を確認します。 次のレッスンで、書式を設定してよりきれいに表示する方法について学習します。

> [!NOTE]
> **[ファイル]** メニューから **[すべてを保存]** をクリックしてレポートを保存します。

## <a name="next-steps"></a>次のステップ

テーブル データ領域がレポートに、フィールドがデータ領域にそれぞれ正しく追加され、レポートが正しくプレビューされました。 次のレッスンでは、列ヘッダーとフィールド式の書式を設定する方法について学習します。 次に、「[レッスン 5: レポートの書式設定 &#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)」を参照してください。
  
## <a name="see-also"></a>関連項目

[テーブル &#40;レポート ビルダーおよび SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)  
[データセット フィールド コレクション (レポート ビルダーおよび SSRS)](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
