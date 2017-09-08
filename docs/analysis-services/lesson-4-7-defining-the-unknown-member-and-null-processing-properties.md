---
title: "不明なメンバーと Null 処理のプロパティを定義する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: d9abb09c-9bfa-4e32-b530-8590e4383566
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6a5d1d6dd514d346f4a24783307b27b86e777be1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-4-7---defining-the-unknown-member-and-null-processing-properties"></a>レッスン 4 ~ 7 の Null 処理のプロパティと不明なメンバーを定義します。
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がディメンションを処理するときに、ディメンションの属性を生成しているのは、データ ソース ビューのテーブルまたはビュー内の基になる列の各値です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] での処理中に NULL 値があった場合は、既定によって NULL は数値列ではゼロに、文字列型の列では空の文字列に変換されます。 この既定の設定を変更したり、基礎的なリレーショナル データ ウェアハウスに固有の抽出、変換、読み込みプロセスがあればそれらを使用して NULL 値を変換したりできます。 また、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を使用し、ディメンションに対しては **UnknownMember** プロパティと **UnknownMemberName** プロパティ、ディメンションのキー属性に対しては **NullProcessing** プロパティという 3 つのプロパティを構成して、指定した値に NULL 値を変換することもできます。  
  
ディメンション ウィザードおよびキューブ ウィザードでは、ディメンションのキー属性が NULL 値を許容するかどうか、またはスノーフレーク ディメンションのルート属性が NULL 値を許容する列に基づいているかどうかを基準にして、これらのプロパティを有効化します。 この場合では、キー属性の **NullProcessing** プロパティは **UnknownMember** に設定され、 **UnknownMember** プロパティは **Visible**に設定されます。  
  
ただし、このチュートリアルで Product ディメンションに対して行っているようにスノーフレーク ディメンションを段階的に構築する場合、またはディメンション デザイナーを使用してディメンションを定義してこれらの既存のディメンションをキューブに組み込む場合は、 **UnknownMember** プロパティおよび **NullProcessing** プロパティを手動で設定する必要があります。  
  
このトピックの実習では、 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW のデータ ソース ビューに追加するスノーフレーク テーブルから、製品カテゴリおよび製品サブカテゴリの属性を取得し、それらの属性を Product ディメンションに追加します。 次に、Product ディメンションの **UnknownMember** プロパティを有効にします。 **UnknownMemberName** プロパティの値には **Assembly Components** を指定し、 **Subcategory** 属性と **Category** 属性を製品名の属性に関連付けます。最後に、スノーフレーク テーブルを結合しているメンバー キー属性に対し、カスタム エラー処理を定義します。  
  
> [!NOTE]  
> キューブ ウィザードを使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを最初に定義したときに Subcategory 属性と Category 属性を追加していれば、これらの手順は自動的に実行されます。  
  
## <a name="reviewing-error-handling-and-unknown-member-properties-in-the-product-dimension"></a>Product ディメンションでのエラー処理のプロパティと不明なメンバーのプロパティの確認  
  
1.  **Product** ディメンションのディメンション デザイナーに切り替え、 **[ディメンション構造]** タブをクリックします。次に、 **[属性]** ペインで **[Product]** をクリックします。  
  
    ディメンション自体のプロパティを表示し、修正できるようになりました。  
  
2.  [プロパティ] ウィンドウで、 **UnknownMember** プロパティと **UnknownMemberName** プロパティを確認します。  
  
    **UnknownMember** プロパティは有効になっていません。このプロパティの値が **Visible** または **Hidden** ではなく、 **None**に設定されているためです。また、 **UnknownMemberName** プロパティには名前が指定されていません。  
  
3.  [プロパティ] ウィンドウで、 **ErrorConfiguration** プロパティのセルをクリックして、 **[(カスタム)]** を選択します。次に、 **ErrorConfiguration** プロパティ コレクションを展開します。  
  
    **ErrorConfiguration** プロパティを **[(Custom)]** に設定すると、既定のエラー構成設定を表示できます。既定のエラー構成設定は変更されていません。  
  
4.  キーおよび NULL キーについて、エラーの構成のプロパティを確認します。変更はしないでください。  
  
    NULL キーが不明なメンバーに変換される際に、この変換に関連する処理エラーが無視されていることがわかります (これが既定の動作です)。  
  
    次の図は、 **ErrorConfiguration** プロパティ コレクションのプロパティ設定を示しています。  
  
    ![ErrorConfiguration プロパティ コレクション](../analysis-services/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration プロパティ コレクション")  
  
5.  **[ブラウザー]** タブをクリックし、 **[階層]** ボックスで **[Product Model Lines]** が選択されていることを確認します。 **[All Products]**を展開します。  
  
    Product Line レベルには 5 つのメンバーが存在します。  
  
6.  **[Components]**を展開します。 **Model Name** レベルのメンバーのうち、ラベルが付いていないメンバーを展開します。  
  
    次の図のように、このレベルには、アジャスタブル レース ( **Adjustable Race** ) など、他の部品を組み立てるときに使用するアセンブリ部品が含まれています。  
  
    ![その他のコンポーネントの構築に使用するアセンブリ部品](../analysis-services/media/l4-productdimensionerrorconfig-2.gif "他のコンポーネントの構築に使用するアセンブリ部品")  
  
## <a name="defining-attributes-from-snowflaked-tables-and-a-product-category-user-defined-hierarchy"></a>スノーフレーク テーブルおよび Product Category ユーザー定義階層の属性の定義  
  
1.  [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW データ ソース ビューのデータ ソース ビュー デザイナーを開き、 **[ダイアグラム オーガナイザー]** ペインで **[Reseller Sales]** を選択します。次に、 **の** [データ ソース ビュー] **メニューの** [オブジェクトの追加と削除] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をクリックします。  
  
    **[テーブルの追加と削除]** ダイアログ ボックスが開きます。  
  
2.  **[含まれているオブジェクト]** ボックスの一覧の **[DimProduct (dbo)]**をクリックします。次に、 **[関連テーブルの追加]**をクリックします。  
  
    **DimProductSubcategory (dbo)** と **FactProductInventory (dbo)** の両方が追加されます。 **FactProductInventory (dbo)** を削除して、 **DimProductSubcategory (dbo)** テーブルだけが **[含まれているオブジェクト]** の一覧に追加されるようにします。  
  
3.  既定では、最後に追加した **DimProductSubcategory (dbo)** テーブルが選択されます。この状態で、 **[関連テーブルの追加]** をもう一度クリックします。  
  
    **[含まれているオブジェクト]** の一覧に **DimProductCategory (dbo)** テーブルが追加されます。  
  
4.  **[OK]**をクリックします。  
  
5.  **の** [書式] [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]メニューで **[自動レイアウト]**をポイントし、 **[ダイアグラム]**をクリックします。  
  
    **DimProductSubcategory (dbo)** テーブルと **DimProductCategory (dbo)** テーブルは互いにリンクしています。また、 **Product** テーブルを介して **ResellerSales** テーブルにもリンクしています。  
  
6.  **Product** ディメンションのディメンション デザイナーに切り替え、 **[ディメンション構造]** タブをクリックします。  
  
7.  **[データ ソース ビュー]** ペイン内を右クリックし、 **[すべてのテーブルを表示]**をクリックします。  
  
8.  **[データ ソース ビュー]** ペインで、 **DimProductCategory** テーブルを探します。次に、このテーブルの **ProductCategoryKey** を右クリックし、 **[列から新しい属性を作成]**をクリックします。  
  
9. **[属性]** ペインで、この新しい属性の名前を「 **Category**」に変更します。  
  
10. [プロパティ] ウィンドウで、 **[NameColumn]** プロパティ フィールド内をクリックし、参照ボタン (**[...]**) をクリックして、 **[名前列]** ダイアログ ボックスを開きます。  
  
11. **[基になる列]** ボックスの一覧で **[EnglishProductCategoryName]** を選択し、 **[OK]**をクリックします。  
  
12. **[データ ソース ビュー]** ペインで、 **DimProductSubcategory** テーブルを探します。このテーブルの **ProductSubcategoryKey** を右クリックし、 **[列から新しい属性を作成]**をクリックします。  
  
13. **[属性]** ペインで、この新しい属性の名前を「 **Subcategory**」に変更します。  
  
14. [プロパティ] ウィンドウで、 **[NameColumn]** プロパティ フィールド内をクリックし、参照ボタン ( **[...]** ) をクリックして、 **[名前列]** ダイアログ ボックスを開きます。  
  
15. **[基になる列]** ボックスの一覧で **[EnglishProductSubcategoryName]** を選択し、 **[OK]**をクリックします。  
  
16. **Product Categories** という名前の新しいユーザー定義階層を作成します。この階層の最上位レベルに **Category**レベルを配置し、その下に **Subcategory**レベル、さらにその下に **Product Name**レベルを配置します。  
  
17. Product Categories ユーザー定義階層の **AllMemberName** の値として、「 **All Products** 」と入力します。  
  
## <a name="browsing-the-user-defined-hierarchies-in-the-product-dimension"></a>Product ディメンションのユーザー定義階層の表示  
  
1.  **Product** ディメンションの **ディメンション デザイナー** で、 **[ディメンションの構造]** タブのツール バーにある **[処理]**をクリックします。  
  
2.  **[はい]** をクリックして、プロジェクトを作成し、配置します。次に、 **[実行]** をクリックして、 **Product** ディメンションを処理します。  
  
3.  処理が正常に完了したら、 **[処理の進行状況]** ダイアログ ボックスで **[ディメンション 'Product' の処理が正常に完了しました]** を展開し、 **[ディメンション属性 'Product Name' の処理が完了しました]**を展開します。次に、 **[SQL クエリ数 1]**を展開します。  
  
4.  SELECT DISTINCT クエリをクリックし、 **[詳細表示]**をクリックします。  
  
    SELECT DISTINCT 句に WHERE 句が追加されています。次の図のように、この WHERE 句は、値を持たない製品を ProductSubcategoryKey から削除します。  
  
    ![SELECT DISTINCT 句に含まれた WHERE 句](../analysis-services/media/l4-productnametraceline-1.gif "れた WHERE 句を SELECT DISTINCT 句")  
  
5.  **[閉じる]** を 3 回クリックし、処理中のダイアログ ボックスをすべて閉じます。  
  
6.  **Product** ディメンションのディメンション デザイナーで、 **[ブラウザー]** タブをクリックします。次に、 **[再接続]**をクリックします。  
  
7.  **[階層]** ボックスの一覧に **[Product Model Lines]** が表示されていることを確認し、 **[All Products]**、 **[Components]**の順に展開します。  
  
8.  **[階層]** ボックスの一覧から **[Product Categories]** を選択し、 **[All Products]**、 **[Components]**の順に展開します。  
  
    アセンブリ部品は何も表示されません。  
  
前の実習で説明した動作を変更するには、Product ディメンションの **UnknownMember** プロパティを有効にし、 **UnknownMemberName** の値を設定します。次に、 **Subcategory** 属性と **Model Name** 属性の **NullProcessing** プロパティを **UnknownMember**に設定します。最後に、 **Category** 属性を **Subcategory** 属性の関連する属性として定義し、 **Product Line** 属性を **Model Name** 属性の関連する属性として定義します。 以上の操作により、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、 **SubcategoryKey** 列に値を持たないそれぞれの製品について、不明なメンバーの名前の値が使用されるようになります。次の実習でそれを確認します。  
  
## <a name="enabling-the-unknown-member-defining-attribute-relationships-and-specifying-custom-processing-properties-for-nulls"></a>不明なメンバーの有効化、属性リレーションシップの定義、および NULL のカスタム処理プロパティの指定  
  
1.  **Product** ディメンションのディメンション デザイナーで **[ディメンション構造]** タブをクリックし、 **[属性]** ペインで **[Product]** をクリックします。  
  
2.  **[プロパティ]** ウィンドウで、 **UnknownMember** プロパティを **Visible**に変更します。次に、 **UnknownMemberName** プロパティのセルをクリックし、値として「 **Assembly Components**」と入力します。  
  
    **UnknownMember** プロパティを **Visible** または **Hidden** に変更すると、ディメンションの **[UnknownMember]** プロパティが有効になります。  
  
3.  **[属性リレーションシップ]** タブをクリックします。  
  
4.  ダイアグラムで、 **[Subcategory]** 属性を右クリックし、 **[新しい属性リレーションシップ]**をクリックします。  
  
5.  **[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Subcategory]**を指定します。 **[関連属性]** を **[Category]**に設定します。 リレーションシップの種類の設定は **[可変]**のままにします。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  **[属性]** ペインで、 **[Subcategory]**を選択します。  
  
8.  [プロパティ] ウィンドウで、 **[KeyColumns]** プロパティ、 **[DimProductSubcategory.ProductSubcategoryKey (Integer)]** プロパティの順に展開します。  
  
9. **NullProcessing** プロパティを **UnknownMember**に変更します。  
  
10. **[属性]** ペインで、 **[Model Name]**を選択します。  
  
11. [プロパティ] ウィンドウで、 **[KeyColumns]** プロパティ、 **[Product.ModelName (WChar)]** プロパティの順に展開します。  
  
12. **NullProcessing** プロパティを **UnknownMember**に変更します。  
  
    これらの変更により、処理中に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が **Subcategory** 属性または **Model Name** 属性に NULL 値を検出すると、不明なメンバーの値がキー値に置き換えられ、ユーザー定義階層が適切に作成されます。  
  
## <a name="browsing-the-product-dimension-again"></a>Product ディメンションの再表示  
  
1.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]**をクリックします。  
  
2.  配置が正常に完了したら、 **Product** ディメンションのディメンション デザイナーで **[ブラウザー]** タブをクリックし、 **[再接続]**をクリックします。  
  
3.  **[階層]** ボックスで **[Product Categories]** が選択されていることを確認し、 **[All Products]**を展開します。  
  
    Category レベルの新しいメンバーとして Assembly Components が表示されています。  
  
4.  **Category** レベルの **Assembly Components** メンバーを展開し、 **Subcategory** レベルの **Assembly Components** メンバーを展開します。  
  
    次の図のように、 **Product Name** レベルにアセンブリ部品が表示されるようになりました。  
  
    ![アセンブリ コンポーネントを示す製品名レベル](../analysis-services/media/l4-assemblycomponents-1.gif "アセンブリ コンポーネントを示す製品名レベル")  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 5 : ディメンションおよびメジャー グループ間のリレーションシップの定義](../analysis-services/lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
  
  

