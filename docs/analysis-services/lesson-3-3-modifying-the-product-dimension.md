---
title: Product ディメンションの変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e1e3500180a7fc82f37b4de03f066647d82ee37c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-3-3---modifying-the-product-dimension"></a>レッスン 3-3-Product ディメンションの変更
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

このトピックの実習では、名前付き計算を使用して製品ラインにわかりやすい名前を指定し、Product ディメンションに階層を定義して、その階層の (All) メンバー名を指定します。 また、属性をグループ化して別々の表示フォルダーに格納します。  
  
## <a name="adding-a-named-calculation"></a>名前付き計算の追加  
データ ソース ビューで名前付き計算をテーブルに追加できます。 次の実習では、製品ラインの完全な名前を表示する名前付き計算を作成します。  
  
#### <a name="to-add-a-named-calculation"></a>名前付き計算を追加するには  
  
1.  **Adventure Works DW 2012** データ ソース ビューを開くには、ソリューション エクスプローラーの **[データ ソース ビュー]** フォルダーで **[Adventure Works DW 2012]** をダブルクリックします。  
  
2.  ダイアグラム ペインの下部で **[Product]** テーブル ヘッダーを右クリックし、 **[新しい名前付き計算]** をクリックします。  
  
3.  **[名前付き計算の作成]** ダイアログ ボックスで、 **[列名]** ボックスに「 **ProductLineName** 」と入力します。  
  
4.  **[式]** ボックスに、次の **CASE** ステートメントを入力するか、またはコピーして貼り付けます。  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
    この **CASE** ステートメントは、キューブ内の各製品ラインにわかりやすい名前を付けるためのものです。  
  
5.  **[OK]** をクリックすると、 **ProductLineName** 名前付き計算が作成されます。 場合によっては、しばらく待つ必要があります。  
  
6.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>属性の NameColumn プロパティの変更  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>属性の NameColumn プロパティ値を変更するには  
  
1.  Product ディメンションのディメンション デザイナーに切り替えます。 これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Product]** ディメンションをダブルクリックします。  
  
2.  **[ディメンション構造]** タブの **[属性]** ペインで、 **[Product Line]** をクリックします。  
  
3.  画面右側の [プロパティ] ウィンドウで、ウィンドウの下部にある **[NameColumn]** プロパティ フィールドをクリックし、参照ボタン (**[...]**) をクリックして、 **[名前列]** ダイアログ ボックスを開きます (場合によっては、画面右側の **[プロパティ]** タブをクリックして、[プロパティ] ウィンドウを開く必要があります)。  
  
4.  **[基になる列]** ボックスの一覧の下部にある **[ProductLineName]** を選択し、 **[OK]** をクリックします。  
  
    NameColumn フィールドに、テキスト " **Product.ProductLineName (WChar)**" が表示されるようになりました。 これで、 **Product Line** 属性階層のメンバーが、簡略名ではなく製品ラインの完全な名前で表示されるようになりました。  
  
5.  **[ディメンション構造]** タブの **[属性]** ペインで、 **[Product Key]** をクリックします。  
  
6.  [プロパティ] ウィンドウで、 **[NameColumn]** プロパティ フィールドをクリックし、参照ボタン (**[...]**) をクリックして、 **[名前列]** ダイアログ ボックスを開きます。  
  
7.  **[基になる列]** ボックスの一覧で **[EnglishProductName]** を選択し、 **[OK]** をクリックします。  
  
    NameColumn フィールドに、テキスト " **Product.EnglishProductName (WChar)**" が表示されるようになりました。  
  
8.  [プロパティ] ウィンドウで、上にスクロールし、 **[Name]** プロパティ フィールドをクリックして「 **Product Name**」と入力します。  
  
## <a name="creating-a-hierarchy"></a>階層の作成  
  
#### <a name="to-create-a-hierarchy"></a>階層を作成するには  
  
1.  **[属性]** ペインの **[Product Line]** 属性を **[階層]** ペインにドラッグします。  
  
2.  **[属性]** ペインの **[Model Name]** 属性を、 **<new level>** [階層] **ペインの** セル ( **[Product Line]** レベルの下) にドラッグします。  
  
3.  **[属性]** ペインの **[Product Name]** 属性を、 **<new level>** [階層] **ペインの** セル ( **[Model Name]** レベルの下) にドラッグします。 (前のセクションで、Product Key を Product Name に名前変更しました)。  
  
4.  **[ディメンション構造]** タブの **[階層]** ペインで、 **[Hierarchy]** 階層のタイトル バーを右クリックし、 **[名前の変更]** をクリックして「 **Product Model Lines**」と入力します。  
  
    この階層の名前が **Product Model Lines**になりました。  
  
5.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="specifying-folder-names-and-all-member-names"></a>フォルダー名およびすべてのメンバー名の指定  
  
#### <a name="to-specify-the-folder-and-member-names"></a>フォルダー名とメンバー名を指定するには  
  
1.  **[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。  
  
    -   **クラス**  
  
    -   **色**  
  
    -   **Days To Manufacture**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **サイズ**  
  
    -   **Size Range**  
  
    -   **スタイル**  
  
    -   **Weight**  
  
2.  [プロパティ] ウィンドウで、 **[AttributeHierarchyDisplayFolder]** プロパティ フィールドに「 **Stocking**」と入力します。  
  
    上記の属性をグループ化し、1 つの表示フォルダーに表示されるようにしました。  
  
3.  **[属性]** ペインで、次の属性を選択します。  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  [プロパティ] ウィンドウで、 **AttributeHierarchyDisplayFolder** プロパティのセルに「 **Financial**」と入力します。  
  
    上記の属性をグループ化し、別の表示フォルダーに表示されるようにしました。  
  
5.  **[属性]** ペインで、次の属性を選択します。  
  
    -   **End Date**  
  
    -   **[開始日]**  
  
    -   **[状態]**  
  
6.  [プロパティ] ウィンドウで、 **AttributeHierarchyDisplayFolder** プロパティのセルに「 **History**」と入力します。  
  
    上記の属性をグループ化し、3 番目の表示フォルダーに表示されるようにしました。  
  
7.  **[階層]** ペインで **[Product Model Lines]** 階層をクリックします。次に、[プロパティ] ウィンドウで、 **AllMemberName** プロパティを **All Products**に変更します。  
  
8.  **[階層]** ペインの空いている領域をクリックし、[プロパティ] ウィンドウの上部にある **AttributeAllMemberName** プロパティを、 **All Products**に変更します。  
  
    空いている領域をクリックすると、Product ディメンション自体のプロパティを変更できます。 **[属性]** ペインの属性リストの上部にある **[Product]** をクリックすることもできます。  
  
9. **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="defining-attribute-relationships"></a>属性リレーションシップの定義  
基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。 属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理速度が上がります。 詳細については、「 [属性リレーションシップの定義](../analysis-services/multidimensional-models/attribute-relationships-define.md) 」および「 [属性リレーションシップ](../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。  
  
#### <a name="to-define-attribute-relationships"></a>属性リレーションシップを定義するには  
  
1.  Product ディメンションの **ディメンション デザイナー** で、 **[属性リレーションシップ]** タブをクリックします。  
  
2.  ダイアグラムで、 **[Model Name]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。  
  
3.  **[属性リレーションシップの作成]** ダイアログ ボックスで、**[基になる属性]** に **[Model Name]** を指定します。 **[関連属性]** を **[Product Line]** に設定します。  
  
    時間が経過するとメンバー間のリレーションシップが変化する可能性があるため、 **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類の設定は **[可変]** のままにします。 たとえば、製品モデルが最終的に別の製品ラインに移動される場合があります。  
  
4.  **[OK]** をクリックします。  
  
5.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="reviewing-product-dimension-changes"></a>Product ディメンションの変更の確認  
  
#### <a name="to-review-the-product-dimension-changes"></a>Product ディメンションの変更を確認するには  
  
1.  **で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  " **配置が正常に完了しました** " というメッセージが表示されたら、 **Product** ディメンションの **ディメンション デザイナー** の **[ブラウザー]** タブをクリックし、ディメンション デザイナーのツール バーにある再接続ボタンをクリックします。  
  
3.  **[階層]** ボックスで **[Product Model Lines]** が選択されていることを確認し、 **[All Products]** を展開します。  
  
    **All** メンバーの名前が " **All Products**" と表示されています。 これは、このレッスンの前の手順で、この階層の **AllMemberName** プロパティを **All Products** に変更したためです。 また、 **Product Line** レベルのメンバー名が、1 文字の簡略名から、わかりやすい名前に変わりました。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[Date ディメンションの変更](../analysis-services/lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>参照  
[データ ソース ビュー & #40; での名前付き計算を定義します。Analysis Services & #41;](../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
[ユーザー定義階層の作成](../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
[属性階層の &#40;All&#41; レベルの構成](../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
