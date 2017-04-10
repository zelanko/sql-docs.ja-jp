---
title: "SQL Server Analysis Services vNext の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# SQL Server Analysis Services vNext の新機能
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>Windows CTP 1.2 の SQL Server Analysis Services

このリリースに新しい機能はありません。 バグ修正とパフォーマンス強化が実施されました。

SQL Server Data Tools (SSDT) の最新のプレビュー リリースでは、SQL Server vNext CTP 1.2 に合わせて、CTP 1.1 で導入された新しい Get Data エクスペリエンスが強化されており、新しいクエリ エディター メニューと素早いアクセス機能が追加されています。 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>Windows CTP 1.1 の SQL Server Analysis Services 

このリリースでは、テーブル モデルの機能が強化されました。 

### <a name="1400-compatibility-level-for-tabular-models"></a>テーブル モデルの&1400; 互換性レベル
  この記事で説明している特徴と機能を利用するには、新規または既存のテーブル モデルを 1400 互換性レベルに設定する必要があります。 1400 互換性レベルのモデルを SQL Server 2016 SP1 以前に展開したり、低い互換性レベルにダウングレードしたりすることはできません。
  
  新規の 1400 互換性レベルのテーブル モデル プロジェクトを作成するか、既存のテーブル モデル プロジェクトを 1400 互換性レベルにアップグレードするには、[SQL Server Data Tools (SSDT) 17.0 RC2](https://go.microsoft.com/fwlink?LinkId=837939) の**以前のリリース**をダウンロードしてインストールします。 
  
SSDT では、新しいテーブル モデル プロジェクトを作成するときに新しい 1400 互換性レベルを選択できます。 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE] SQL Server Data Tools (SSDT) の 12 月リリースで統合されたワークスペースでは、1400 互換性レベルをサポートしています。 ワークスペース サーバー インスタンスで新しいテーブル モデル プロジェクトを作成すると、展開するそのインスタンスまたはインスタンスは [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1 である必要があります。 

SSDT で既存のテーブル モデルをアップグレードするには、ソリューション エクスプローラーで **Model.bim** を右クリックし、**[プロパティ]** で **[互換性レベル]** プロパティを **[SQL Server vNext (1400)]** に設定します。 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>新しい Get Data エクスペリエンス
SQL Server Data Tools (SSDT) の最新のプレビュー リリースは、[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1 リリースと合わせてし、1400 互換性レベルのテーブル モデルに新しい **Get Data** を導入しました。 この新機能は、Power BI Desktop と Microsoft Excel 2016 の同様の機能に基づいています。

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE] このリリースでは、少数のデータ ソースがサポートされています。 今後の更新プログラムでは、追加のデータ ソースと機能がサポートされる予定です。

新しい Get Data エクスペリエンスの詳細については、[Analysis Services チームのブログ](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-vnext-on-windows-ctp-1-1-for-analysis-services/)を参照してください。

## <a name="ragged-hierarchies"></a>不規則階層
テーブル モデルでは、親子階層をモデル化できます。 さまざまな数のレベルがある階層は、不規則階層とも呼ばれます。 既定で、最下位の子の下のレベルについては、不規則階層が空白で表示されます。 不規則階層の組織図の例を次に示します。

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

このリリースでは、**[Hide Members]** (メンバーを隠す) プロパティが導入されました。 階層の **[Hide Members]** (メンバーを隠す) プロパティを **[Hide blank members]** (空白のメンバーを隠す) に設定できます。

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE] モデルの空白のメンバーは、空白の文字列ではなく DAX の空白値で表されます。

**[Hide blank members]** (空白のメンバーを隠す) に設定し、モデルを展開すると、Excel のように、レポート クライアントに読みやすいバージョンの階層が表示されます。

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>詳細行
メジャー値に使用するカスタム行セットを定義できるようになりました。 詳細行は、多次元モデルの既定のドリルスルー アクションと似ています。 エンドユーザーは詳細行を使用して、集計レベルよりも詳細な情報を表示できます。 

次のピボットテーブルは、Adventure Works サンプル テーブル モデルのインターネット売上の年別合計を示します。 メジャーの集計値を含むセルを右クリックし、**[詳細の表示]** をクリックして詳細行を表示します。

![AS_Show_Details](../analysis-services/media/as-show-details.png)

既定では、Internet Sales テーブルの関連データが表示されます。 この制限付きの動作はユーザーにとって意味がないこともよくあります。顧客名や注文情報など、役に立つ情報を示す必要な列がテーブルに表示されないことがあるためです。 詳細行では、メジャーに **[詳細行の式]** プロパティを指定できます。

#### <a name="detail-rows-expression-property-for-measures"></a>メジャーの [詳細行の式] プロパティ
モデルの作成者は、メジャーの **[詳細行の式]** プロパティを使用して、エンドユーザーに返す列と行をカスタマイズすることができます。

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

[SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) DAX 関数は、詳細行の式でよく使用されます。 次の例では、サンプル Adventure Works テーブル モデルの Internet Sales テーブルの行について返される列を定義しています。

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

プロパティが定義され、モデルが展開されている場合、ユーザーが **[詳細の表示]** を選択すると、カスタム行セットが返されます。 選択されたセルのフィルター コンテキストが自動的に使用されます。 この例では、2010 値の行のみが表示されます。

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>テーブルの既定の [詳細行の式] プロパティ
メジャーだけでなく、テーブルにも、詳細行式を定義できるプロパティがあります。 **[Default Detail Rows Expression]** (既定の詳細行の式) プロパティは、テーブル内のすべてのメジャーについて既定として動作します。 式が定義されていないメジャーは、テーブルから式が継承され、テーブルに定義されている行セットが表示されます。 これで式が再利用できるようになり、後でテーブルに新しいメジャーを追加すると、式が自動的に継承されます。

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>DETAILROWS DAX 関数
このリリースでは、詳細行式で定義された行セットを返す新しい `DETAILROWS` DAX が追加されました。 機能は MDX の `DRILLTHROUGH` ステートメントと似ています。MDX のこのステートメントも、テーブル モデルに定義されている詳細行式と互換性があります。

次の DAX クエリは、メジャーまたはそのテーブルの詳細行式に定義されている行セットを返します。 式が定義されていない場合、メジャーを含むテーブルなので、Internet Sales テーブルのデータが返されます。

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="dax-enhancements"></a>DAX の機能強化
このリリースには、DAX 式の `IN` 演算子が含まれています。 これは、`WHERE` 句で複数の値を指定するために一般的に使用されている [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) 演算子と似ています。

以前は、次のメジャー式のように、論理 `OR` 演算子を使用して複数値フィルターを指定するのが一般的でした。

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

これが `IN` 演算子で簡単になりました。
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

この場合、`IN` 演算子は、各行が指定した色を示す 3 行の単一列テーブルを参照しています。 テーブル コンストラクター構文には、中かっこ ({}) を使用します。

`IN` 演算子は、`CONTAINSROW` 関数と機能的に等価です。
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

テーブル コンストラクターでは、`IN` 演算子も効果的に使用できます。 たとえば、次のメジャー フィルターは、製品の色やカテゴリの組み合わせ別にフィルター処理します。
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

新しい `IN` 演算子を使用すると、上記のメジャー式は次のようになります。
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```


## <a name="table-level-security"></a>テーブルレベルのセキュリティ
このリリースでは、テーブルレベルのセキュリティが導入されました。 テーブル データへのアクセスを制限するだけでなく、機密性の高いテーブル名も保護できます。 これで、悪意のあるユーザーがテーブルの存在を検出できなくなります。

テーブルレベルのセキュリティは、JSON ベースのメタデータ、テーブル モデル スクリプティング言語 (TMSL) またはテーブル オブジェクト モデル (TOM) を使用して設定する必要があります。 

たとえば、次のコードを使用して、**TablePermission** クラスの **MetadataPermission** プロパティを **None** に設定すると、サンプル Adventure Works テーブル モデルの Product テーブルをセキュリティで保護できます。

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```
## <a name="future-updates"></a>今後の更新プログラム
今後のリリースでは、さらに機能強化が追加される予定です。 この記事は、SQL Server vNext の新機能に関する重要なお知らせなどについて更新する予定です。
