---
title: 'チュートリアル: 式の概要 | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79563abac2c6a9ed64dff93667ff3d3966b70bc5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098846"
---
# <a name="tutorial-introducing-expressions"></a>チュートリアル: 式の概要
  式を使用すると、強力で柔軟なレポートを作成できます。 このチュートリアルでは、一般的な関数および演算子を使用した式を作成および実装する方法を説明します。 [**式**] ダイアログボックスを使用すると、名前の値を連結する式を作成したり、別のデータセットの値を参照したり、フィールドの値に基づいてさまざまな画像を表示したりできます。  
  
 レポートは縞状で、各行には白と白でない色が交互に使用されます。 レポートには、白以外の行の色を選択するためのパラメーターが含まれています。  
  
 次の図に、ここで作成するレポートと同様のレポートを示します。  
  
 ![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>学習内容  
 このチュートリアルでは、次の方法を学習します。  
  
1.  [テーブルまたはマトリックス ウィザードを使用して表レポートとデータセットを作成する](#Setup)  
  
2.  [データ ソースおよびデータセットの既定名を更新する](#UpdateNames)  
  
3.  [姓、名、およびイニシャルを表示する](#Concatenate)  
  
4.  [画像を使用して性別を表示する](#Gender)  
  
5.  [CountryRegion 名を参照する](#Lookup)  
  
6.  [前回の購入日からの日数をカウントする](#Count)  
  
7.  [インジケーターを使用して売上比較を示す](#Indicator)  
  
8.  [レポートに "緑色のバー" レポートを作成する](#GreenBar)  
  
### <a name="other-optional-steps"></a>その他のオプションの手順  
  
-   [日付列の書式を設定する](#DateFormat)  
  
-   [レポートタイトルを追加する](#Title)  
  
-   [レポートを保存する](#Save)  
  
 このチュートリアルの推定所要時間: 30 分。  
  
## <a name="requirements"></a>要件  
 要件の詳細については、[「チュートリアルの前提条件 (レポート ビルダー)」](../reporting-services/report-builder-tutorials.md) を参照してください。  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a>1. テーブルまたはマトリックスウィザードからテーブルレポートとデータセットを作成する  
 表レポート、データ ソース、およびデータセットを作成します。 テーブルのレイアウト時には、少数のフィールドのみを含めておきます。 ウィザードの完了後に、列を手動で追加します。 ウィザードを使用すると、容易にテーブルをレイアウトし、スタイルを適用できます。  
  
> [!NOTE]  
>  このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。 このため、クエリが非常に長くなっています。 ビジネス環境でクエリにデータを含めることはありません。 これは、学習に使用することのみを目的としています。  
  
> [!NOTE]  
>  このチュートリアルでは、ウィザードに関する複数の手順を 1 つにまとめて示します。 レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 &#40;レポート ビルダー&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。  
  
#### <a name="to-create-a-new-table-report"></a>新しい表レポートを作成するには  
  
1.  [**スタート**] をクリックし、[**プログラム**]、[ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**レポートビルダー**] の順にポイントし、[**レポートビルダー**] をクリックします。  
  
     [**はじめに**] ダイアログボックスが表示されます。  
  
    > [!NOTE]  
    >  [**はじめに**] ダイアログボックスが表示されない場合は、[**レポートビルダー** ] ボタンの [**新規作成**] をクリックします。  
  
    > [!NOTE]  
    >  ClickOnce バージョンのレポートビルダーを使用する場合は、レポートマネージャーを開き、[**レポートビルダー**] をクリックするか、Reporting Services コンテンツの種類 (レポートなど) が有効になっている SharePoint サイトにアクセスして、共有ドキュメントライブラリの [**ドキュメント**] タブにある [**新しいドキュメント**] メニューの [**レポートのレポートビルダー** ] をクリックします。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[テーブルまたはマトリックス ウィザード]** をクリックします。  
  
4.  **[データセットの選択]** ページで、 **[データセットを作成する]** をクリックします。  
  
5.  **[次へ]** をクリックします。  
  
6.  **[データ ソースへの接続の選択]** ページで、種類が **[SQL Server]** のデータ ソースを選択します。 一覧からデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択します。  
  
7.  **[次へ]** をクリックします。  
  
8.  **[クエリのデザイン]** ページで、 **[テキストとして編集]** をクリックします。  
  
9. 次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     クエリには、生年月日、名前、姓、州または郡、国または地域の識別子、性別、年度累計購入額などを示す列の名前が指定されています。  
  
10. クエリデザイナーのツールバーで、[**実行**] (**!**) をクリックします。 結果セットには FirstName、LastName、StateProvince、CountryRegionID、Gender、YTDPurchase、および LastPurchase の各列が含まれ、20 行のデータが表示されます。  
  
11. **[次へ]** をクリックします。  
  
12. **[フィールドの配置]** ページで、 **[使用できるフィールド]** ボックスから **[値]** ボックスに、次に示すフィールドを指定順にドラッグします。  
  
    -   StateProvince  
  
    -   CountryRegionID  
  
    -   LastPurchase  
  
    -   YTDPurchase  
  
     CountryRegionID および YTDPurchase には数値データが格納されているため、これらには既定で SUM 集計が適用されます。  
  
    > [!NOTE]  
    >  この時点で FirstName フィールドと LastName フィールドは含まれていません。 これらは後の手順で追加します。  
  
13. [**値**] ボックスの一覧で、 `CountryRegionID`を右クリックし、[**合計**] をクリックします。  
  
     これでもう CountryRegionID には合計が適用されていません。  
  
14. **[値]** ボックスの一覧の **[YTDPurchase]** を右クリックし、 **[合計]** をクリックします。  
  
     これでもう YTDPurchase には合計が適用されていません。  
  
15. **[次へ]** をクリックします。  
  
16. **[レイアウトの選択]** ページで、**[次へ]** をクリックします。  
  
17. [**スタイルの選択**] ページで [**スレート**] をクリックし、[**完了**] をクリックします。  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a>2. データソースおよびデータセットの既定の名前を更新する  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a>データ ソースの既定名を更新するには  
  
1.  レポート データ ペインで **[データ ソース]** を展開します。  
  
2.  **[DataSource1]** を右クリックし、 **[データ ソースのプロパティ]** をクリックします。  
  
3.  **[名前]** ボックスに「 **ExpressionsDataSource**」と入力します。  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a>データセットの既定名を更新するには  
  
1.  レポート データ ペインで **[データセット]** を展開します。  
  
2.  **[DataSet1]** を右クリックし、 **[データセットのプロパティ]** をクリックします。  
  
3.  **[名前]** ボックスに「 **Expressions**」と入力します。  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a>3. 名、イニシャル、姓を表示する  
 姓およびイニシャルを含む名前に評価される式に、**Left** 関数および**連結** (**&**) 演算子を使用します。 式を手順どおりに作成することも、手順をスキップして先に進み、チュートリアルから式をコピーして **[式]** ダイアログ ボックスに貼り付けることもできます。  
  
#### <a name="to-add-the-name-column"></a>Name 列を追加するには  
  
1.  **[StateProvince]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[左]** をクリックします。  
  
     **[StateProvince]** 列の左側に、新しい列が追加されます。  
  
2.  新しい列のタイトルをクリックし、「**Name**」と入力します。  
  
3.  **[Name]** 列のデータ セルを右クリックし、 **[式]** をクリックします。  
  
4.  **[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[テキスト]** をクリックします。  
  
5.  **[アイテム]** ボックスの一覧の **[Left]** をダブルクリックします。  
  
     **Left** 関数が式に追加されます。  
  
6.  **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
7.  **[値]** ボックスの一覧の **[FirstName]** をダブルクリックします。  
  
8.  「 **, 1)**」と入力します。  
  
     この式により、 **FirstName** 値の左から数えて 1 文字が抽出されます。  
  
9. 「**&" "&**」と入力します。  
  
10. **[値]** ボックスの一覧の **[LastName]** をダブルクリックします。  
  
     完成した式は、次のようになります。 `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a>4. 画像を使用して性別を表示する  
 画像を使用して個人の性別を示し、3 つ目の画像を使用して不明な性別値を識別します。 レポートに、非表示の画像を 3 つと、画像を表示するための新しい列を追加し、Gender フィールドの値に基づいて、この列に表示する画像を決定します。  
  
 レポートを縞状レポートにする際に、画像を格納するテーブル セルに色を適用するには、四角形を追加して、この四角形に画像を追加します。 四角形を使用するのは、背景色を画像には適用せず、四角形に適用できるようにするためです。  
  
 このチュートリアルでは、Windows と共にインストールされた画像を使用しますが、それ以外の任意の画像を使用することもできます。 埋め込み画像を使用する場合は、ローカル コンピューターにもレポート サーバーにもその画像をインストールする必要はありません。  
  
#### <a name="to-add-images-to-the-report-body"></a>画像をレポート本文に追加するには  
  
1.  **[デザイン]** をクリックしてデザイン ビューに戻ります。  
  
2.  リボンの **[挿入]** タブで **[画像]** をクリックして、レポート本文内のテーブルより下をクリックします。  
  
     **[画像のプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[インポート]** をクリックし、C:\Users\Public\Public Pictures\Sample Pictures に移動します。  
  
4.  Penguins.JPG をクリックし、**[開く]** をクリックします。  
  
     [**画像のプロパティ**] ダイアログボックスで、[**表示**] をクリックし、[**非表示**] オプションをクリックします。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  手順 2. ～ 5. を繰り返します。ただし画像は Koala.JPG を選択します。  
  
7.  手順 2. ～ 5. を繰り返します。ただし画像は Tulips.JPG を選択します。  
  
#### <a name="to-add-the-gender-column"></a>Gender 列を追加するには  
  
1.  [**名前**] 列を右クリックし、[**列の挿入**] をポイントして、[**右**] をクリックします。  
  
     [**名前**列の右側に新しい列が追加されます。  
  
2.  新しい列のタイトルをクリックし、「**Gender**」と入力します。  
  
#### <a name="to-add-a-rectangle"></a>四角形を追加するには  
  
-   リボンの [**挿入**] タブで、[**四角形**] をクリックし、[**性別**] 列のデータセル内をクリックします。  
  
     四角形がセルに追加されます。  
  
#### <a name="to-add-an-image-to-the-rectangle"></a>四角形に画像を追加するには  
  
1.  四角形を右クリックし、[**挿入**] をポイントして、[**イメージ**] をクリックします。  
  
2.  [**イメージのプロパティ**] ダイアログボックスで、[**このイメージを使用する**] の横にある下矢印をクリックし、追加したイメージの1つを選択します (たとえば、penguins.jpg)。  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a>画像を使用して性別を示すには  
  
1.  [**性別**] 列のデータセルで画像を右クリックし、[**画像のプロパティ**] をクリックします。  
  
2.  [**画像のプロパティ**] ダイアログボックスで、[次の**画像を使用**] ボックスの横にある式の [ **fx** ] ボタンをクリックします。  
  
3.  **[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[プログラム フロー]** をクリックします。  
  
4.  **[アイテム]** ボックスの一覧の **[Switch]** をダブルクリックします。  
  
5.  **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
6.  **[値]** ボックスの一覧の **[Gender]** をダブルクリックします。  
  
7.  「** ="Male", "Koala",**」と入力します。  
  
8.  **[値]** ボックスの一覧の **[Gender]** をダブルクリックします。  
  
9. 「** ="Female", "Penguins",**」と入力します。  
  
10. **[値]** ボックスの一覧の **[Gender]** をダブルクリックします。  
  
11. 「**="Unknown", "Tulips")**」と入力します。  
  
     完成した式は、次のようになります。 `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. もう一度 [ **OK** ] をクリックして、[**画像のプロパティ**] ダイアログボックスを閉じます。  
  
14. **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a>5. 国名を検索する  
 国/地域の識別子の代わりに国/地域の名前を表示するには、国データセットを作成し、 **Lookup**関数を使用します。  
  
#### <a name="to-create-the-countryregion-dataset"></a>CountryRegion データセットを作成するには  
  
1.  **[デザイン]** をクリックしてデザイン ビューに戻ります。  
  
2.  レポートデータペインで、[**新規作成**] をクリックし、[**データセット**] をクリックします。  
  
3.  **[レポートに埋め込まれたデータセットを使用します]** をクリックします。  
  
4.  **[データ ソース]** ボックスの一覧の [ExpressionsDataSource] をクリックします。  
  
5.  **[名前]** ボックスに「 **CountryRegion**」と入力します。  
  
6.  クエリの種類に **[テキスト]** が選択されていることを確認し、 **[クエリ デザイナー]** をクリックします。  
  
7.  **[テキストとして編集]** をクリックします。  
  
8.  次のクエリをコピーし、クエリ ペインに貼り付けます。  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. [**実行**] (**!**) をクリックしてクエリを実行します。  
  
     クエリ結果は国/地域の識別子と名前です。  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. **[OK]** を再度クリックして、 **[データセットのプロパティ]** ダイアログ ボックスを閉じます。  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a>CountryRegion データセット内の値を参照するには  
  
1.  [ **Country REGION id** ] 列タイトルをクリックし、テキスト "id" を削除します。  
  
2.  **[Country Region]** 列のデータ セルを右クリックし、 **[式]** をクリックします。  
  
3.  先頭の等号 (=) 部分を除いて、式を削除します。  
  
     式は次のようになります。 `=`  
  
4.  [**式**] ダイアログボックスで、[**共通の関数**] を展開し、[**その他**] をクリックします。  
  
5.  [**アイテム**] ボックスの一覧の [**参照**] をダブルクリックします。  
  
6.  **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
7.  [**値**] ボックスの一覧で、 `CountryRegionID`をダブルクリックします。  
  
8.  カーソルが別の位置にある場合は、`CountryRegionID.Value` の直後に置きます。  
  
9. 右かっこを削除し、「**,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**」と入力します。  
  
     完成した式は、次のようになります。 `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`  
  
     **Lookup**関数の構文では、国の値を返す国データセット内の COUNTRYREGIONID と ID の間の参照を指定します。これは、国データセットにも含まれます。  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a>6. 前回の購入からの日数をカウントする  
 列を追加し、 **Now**関数または`ExecutionTime`組み込みグローバル変数を使用して、ユーザーが前回購入した日から今日までの日数を計算します。  
  
#### <a name="to-add-the-days-ago-column"></a>Days Ago 列を追加するには  
  
1.  **[デザイン]** をクリックしてデザイン ビューに戻ります。  
  
2.  **[Last Purchase]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[右]** をクリックします。  
  
     **[Last Purchase]** 列の右側に、新しい列が追加されます。  
  
3.  列ヘッダーに「 **Days Ago**」と入力します。  
  
4.  **[Days Ago]** 列のデータ セルを右クリックし、 **[式]** をクリックします。  
  
5.  **[式]** ダイアログ ボックスで、**[共通の関数]** を展開し、**[日付と時刻]** をクリックします。  
  
6.  **[アイテム]** ボックスの一覧の **[DateDiff]** をダブルクリックします。  
  
7.  カーソルが別の位置にある場合は、`DateDiff(` の直後に置きます。  
  
8.  「**"d",**」と入力します。  
  
9. **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
10. [**値**] ボックスの一覧の [ **lastpurchase**] をダブルクリックします。  
  
11. カーソルが別の位置にある場合は、`Fields!LastPurchase.Value` の直後に置きます。  
  
12. 型 **、**  
  
13. [**カテゴリ**] ボックスの一覧で、[**日付 & 時刻**] をもう一度クリックします。  
  
14. [**アイテム**] ボックスの一覧の [ **Now**] をダブルクリックします。  
  
    > [!WARNING]  
    >  運用環境のレポートでは、レポートのレンダリングごとに何度も評価される式に **Now** 関数を使用しないでください (レポートの詳細行内など)。 **Now** の値が行ごとに変わり、それが式の評価に影響して、微妙に一貫性に欠ける結果を招きます。 代わりに、によって提供`ExecutionTime`される[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]グローバル変数を使用する必要があります。  
  
15. カーソルが別の位置にある場合は、`Now(` の直後に置きます。  
  
16. 左かっこを削除し、「**)**」と入力します。  
  
     完成した式は、次のようになります。 `=DateDiff("d", Fields!LastPurchase.Value, Now)`  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a>7. インジケーターを使用して売上比較を表示する  
 新しい列を追加し、インジケーターを使用して、ユーザーの年度累計 (YTD) 購入額が平均 YTD 購入額を上回るか下回っているかを示します。 **Round** 関数では、値から小数が除去されます。  
  
 インジケーターとその状態を構成するには、多数の手順が必要です。 必要に応じて、「インジケーターを構成するには」の手順に進んで、このチュートリアルの完成した式をコピーして [**式**] ダイアログボックスに貼り付けます。  
  
#### <a name="to-add-the--or---avg-sales-column"></a>+ or - AVG Sales 列を追加するには  
  
1.  **[YTD Purchase]** 列を右クリックし、 **[列の挿入]** をポイントして、 **[右]** をクリックします。  
  
     **[YTD Purchase]** 列の右側に、新しい列が追加されます。  
  
2.  新しい列のタイトルをクリックし、「**+ or - AVG Sales**」と入力します。  
  
#### <a name="to-add-an-indicator"></a>インジケーターを追加するには  
  
1.  リボンの [**挿入**] タブで [**インジケーター**] をクリックし、[ **+ or-AVG Sales** ] 列のデータセルをクリックします。  
  
     **[インジケーターの種類の選択]** ダイアログ ボックスが表示されます。  
  
2.  アイコン セットの **[指向性]** グループ内で、3 つの灰色の矢印のセットをクリックします。  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a>インジケーターを構成するには  
  
1.  インジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックして、 **[値と状態]** をクリックします。  
  
2.  **[値]** ボックスの横にある式 ( **[Fx]** ) ボタンをクリックします。  
  
3.  **[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[数学]** をクリックします。  
  
4.  **[アイテム]** ボックスの一覧の **[Round]** をダブルクリックします。  
  
5.  **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
6.  [**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。  
  
7.  カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。  
  
8.  各種**-**  
  
9. [**共通の関数**] を再度展開し、[**集計**] をクリックします。  
  
10. [**アイテム**] ボックスの一覧の [ **Avg**] をダブルクリックします。  
  
11. **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
12. [**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。  
  
13. カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。  
  
14. 「**, "Expressions"))**」と入力します。  
  
     完成した式は、次のようになります。 `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. **[状態の単位]** ボックスの一覧の **[数値]** をクリックします。  
  
17. 下矢印のある行で、 **[開始]** 値のボックスの右にある **[fx]** ボタンをクリックします。  
  
18. **[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[数学]** をクリックします。  
  
19. **[アイテム]** ボックスの一覧の **[Round]** をダブルクリックします。  
  
20. **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
21. [**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。  
  
22. カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。  
  
23. 各種**-**  
  
24. [**共通の関数**] を再度展開し、[**集計**] をクリックします。  
  
25. [**アイテム**] ボックスの一覧の [ **Avg**] をダブルクリックします。  
  
26. **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
27. [**値**] ボックスの一覧で、[ **YTDPurchase**] をダブルクリックします。  
  
28. カーソルが別の位置にある場合は、`Fields!YTDPurchase.Value` の直後に置きます。  
  
29. 「**, "Expressions")) < 0**」と入力します。  
  
     完成した式は、次のようになります。 `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. **[終了]** 値のボックスに「 **0**」と入力します。  
  
32. 水平矢印のある行をクリックし、 **[削除]** をクリックします。  
  
33. 上矢印のある行で、 **[開始]** ボックスに「 **0**」と入力します。  
  
34. **[終了]** 値のボックスの右にある **[Fx]** ボタンをクリックします。  
  
35. [**式**] ダイアログボックスで、次の式を作成します。`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. **[OK]** を再度クリックして、 **[インジケーターのプロパティ]** ダイアログ ボックスを閉じます。  
  
38. **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a>8. レポートに "緑色のバー" レポートを作成する  
 パラメーターを使用して、レポート内で 1 行おきに適用する色を指定し、レポートを縞状にします。  
  
#### <a name="to-add-a-parameter"></a>パラメーターを追加するには  
  
1.  **[デザイン]** をクリックしてデザイン ビューに戻ります。  
  
2.  **レポート データ** ペインで、 **[パラメーター]** を右クリックし、 **[パラメーターの追加]** をクリックします。  
  
     **[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[プロンプト]** に「 **Choose color**」と入力します。  
  
4.  **[名前]** に「 **RowColor**」と入力します。  
  
5.  左側のウィンドウで、[**使用可能な値**] をクリックします。  
  
6.  [**値の指定] を**クリックします。  
  
7.  **[追加]** をクリックします。  
  
8.  [**ラベル**] ボックスに「**黄**」と入力します。  
  
9. **[値]** ボックスに「 **Yellow**」と入力します。  
  
10. **[追加]** をクリックします。  
  
11. **[ラベル]** ボックスに「 **Green**」と入力します。  
  
12. **[値]** ボックスに「 **PaleGreen**」と入力します。  
  
13. **[追加]** をクリックします。  
  
14. **[ラベル]** ボックスに「 **Blue**」と入力します。  
  
15. **[値]** ボックスに「 **LightBlue**」と入力します。  
  
16. **[追加]** をクリックします。  
  
17. **[ラベル]** ボックスに「 **Pink**」と入力します。  
  
18. **[値]** ボックスに「 **Pink**」と入力します。  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a>詳細行に色を交互に適用する  
  
1.  リボンの [**表示**] タブをクリックし、[**プロパティ**] が選択されていることを確認します。  
  
2.  [**名前**] 列のデータセルをクリックし、Shift キーを押します。  
  
3.  行内のセルを 1 つおきにクリックします。  
  
4.  プロパティ ペインで、 **[BackgroundColor]** をクリックします。  
  
     プロパティペインのプロパティがカテゴリ別に一覧表示されている場合は、[**塗りつぶし**] カテゴリの下に [ **BackgroundColor** ] が表示されます。  
  
5.  下矢印をクリックし、 **[式]** をクリックします。  
  
6.  **[式]** ダイアログ ボックスで、 **[共通の関数]** を展開し、 **[プログラム フロー]** をクリックします。  
  
7.  **[アイテム]** ボックスの一覧の **[IIf]** をダブルクリックします。  
  
8.  [**共通の関数**] を展開し、[**集計**] をクリックします。  
  
9. [**アイテム**] ボックスの一覧の [ **RunningValue**] をダブルクリックします。  
  
10. **[カテゴリ]** ボックスの一覧の **[フィールド (Expressions)]** をクリックします。  
  
11. **[値]** ボックスの一覧の **[FirstName]** をダブルクリックします。  
  
12. カーソルがまだの直後`Fields!FirstName.Value`にない場合は、そこに配置し **、「」** と入力します。  
  
13. [**共通の関数**] を展開し、[**集計**] をクリックします。  
  
14. [**アイテム**] ボックスの一覧の [ **Count**] をダブルクリックします。  
  
15. カーソルが別の位置にある場合は、`Count(` の直後に置きます。  
  
16. 左かっこを削除し **、「式」** と入力します。  
  
    > [!NOTE]  
    >  Expressions は、データ行をカウントするデータセットの名前です。  
  
17. [**演算子**] を展開し、[**算術**] をクリックします。  
  
18. [**アイテム**] ボックスの一覧の [ **Mod**] をダブルクリックします。  
  
19. カーソルが別の位置にある場合は、`Mod` の直後に置きます。  
  
20. 「**2 =0,**」と入力します。  
  
    > [!IMPORTANT]  
    >  2 という数値の前に、必ずスペースを入れてください。  
  
21. **[パラメーター]** をクリックし、 **[値]** ボックスの一覧の **[RowColor]** をダブルクリックします。  
  
22. カーソルが別の位置にある場合は、`Parameters!RowColor.Value` の直後に置きます。  
  
23. 「 **, "白色")」と入力します。**  
  
     完成した式は、次のようになります。 `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a>レポートを実行する  
  
1.  [**ホーム**] タブが表示されていない場合は、[**ホーム**] をクリックしてデザインビューに戻ります。  
  
2.  **[実行]** をクリックします。  
  
3.  [**色の選択**] ドロップダウンリストで、レポートの白以外のバーの色を選択します。  
  
4.  **[レポートの表示]** をクリックします。  
  
     選択した背景色が 1 行おきに適用された状態でレポートが表示されます。  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a>optional日付列の書式を設定する  
 日付を含む、**最後に購入**した列の書式を設定します。  
  
#### <a name="to-format-date-column"></a>日付列の書式を設定するには  
  
1.  **[デザイン]** をクリックしてデザイン ビューに戻ります。  
  
2.  [ **Last Purchase** ] 列のデータセルを右クリックし、[**テキストボックスのプロパティ**] をクリックします。  
  
3.  [**テキストボックスのプロパティ**] ダイアログボックスで、[**数値**] をクリックし、[**日付**] をクリックして、種類** \*1/31/2000**をクリックします。  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a>optionalレポートタイトルを追加する  
 レポートにタイトルを追加します。  
  
#### <a name="to-add-a-report-title"></a>レポート タイトルを追加するには  
  
1.  デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。  
  
2.  「 **Sales Comparison Summary**」と入力し、テキストボックスの外側をクリックします。  
  
3.  **売上比較の概要**が含まれているテキストボックスを右クリックし、[**テキストボックスのプロパティ**] をクリックします。  
  
4.  **[テキスト ボックスのプロパティ]** ダイアログ ボックスで、 **[フォント]** をクリックします。  
  
5.  **[サイズ]** ボックスの一覧の **[18pt]** を選択します。  
  
6.  [**色**] ボックスの一覧の [**灰色**] をクリックします。  
  
7.  [**太字**] と [**斜体**] を選択します。  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a>optionalレポートを保存する  
 レポートは、レポート サーバー、SharePoint ライブラリ、またはコンピューターに保存することができます。 詳細については、「[レポートの保存 &#40;レポート ビルダー&#41;](report-builder/saving-reports-report-builder.md)」を参照してください。  
  
 このチュートリアルでは、レポートをレポート サーバーに保存します。 レポート サーバーにアクセスできない場合は、レポートをコンピューターに保存してください。  
  
#### <a name="to-save-the-report-to-a-report-server"></a>レポート サーバーにレポートを保存するには  
  
1.  **レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。  
  
2.  **[最近使ったサイトとサーバー]** をクリックします。  
  
3.  レポートを保存する権限があるレポート サーバーの名前を入力するか選択します。  
  
     "レポート サーバーに接続しています" というメッセージが表示されます。 接続が完了すると、レポート サーバー管理者がレポートの既定の場所として指定したレポート フォルダーのコンテンツが表示されます。  
  
4.  [**名前**] で、既定の名前を「 **Sales Comparison Summary**」に置き換えます。  
  
5.  **[Save]** (保存) をクリックします。  
  
 レポートがレポート サーバーに保存されます。 接続しているレポート サーバーの名前がウィンドウ下部のステータス バーに表示されます。  
  
#### <a name="to-save-the-report-to-your-computer"></a>自分のコンピューターにレポートを保存するには  
  
1.  **レポート ビルダー** のボタンの **[名前を付けて保存]** をクリックします。  
  
2.  **[デスクトップ]**、 **[マイ ドキュメント]**、または **[マイ コンピューター]** をクリックして、レポートを保存するフォルダーを参照します。  
  
3.  [**名前**] で、既定の名前を「 **Sales Comparison Summary**」に置き換えます。  
  
4.  **[Save]** (保存) をクリックします。  
  
## <a name="see-also"></a>参照  
 [式 &#40;レポート ビルダーおよび SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [インジケーター &#40;レポートビルダーと SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)   
 [画像、テキストボックス、四角形、および行 &#40;レポートビルダーと SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md)   
 [テーブル &#40;レポートビルダーと SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)  
  
  
