---
title: "どのような &#39; SQL Server 2017 Analysis Services の |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eb6afc9-76ed-45a2-a188-374a4fc23224
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: eb98483d6237f2db2fdb0cb9aa444dd938a431f0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="what39s-new-in-sql-server-2017-analysis-services"></a>どのような &#39; s SQL Server 2017 Analysis Services の新機能
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]


## <a name="sql-server-2017-analysis-services-rc2"></a>SQL Server 2017 分析サービス RC2
このリリースに新しい機能はありません。 このリリースの機能強化には、バグの修正とパフォーマンスが含まれます。

## <a name="sql-server-2017-analysis-services-rc1"></a>SQL Server 2017 Analysis Services RC1
このリリースでの新機能はありません、ただし、このリリースでは追加の機能強化[動的管理ビュー](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) の 1400 1200 互換性レベルは、表形式モデル。

DISCOVER_CALC_DEPENDENCY ようになりましたし 1400、1200 の表形式モデルで動作します。 1400 の表形式モデルでは、M パーティション、M 式および構造化されたデータ ソース間の依存関係を表示します。 詳細については、次を参照してください。、 [Analysis Services ブログ](https://blogs.msdn.microsoft.com/analysisservices/)です。

MDSCHEMA_MEASUREGROUP_DIMENSIONS の機能強化は、この DMV には、メジャーの次元を表示するさまざまなクライアント ツールで使用される含まれます。 たとえば、Excel ピボット テーブルの探索機能により、ユーザーが選択したメジャーに関連するディメンションへのクロス ドリル。 このリリースでは、正しくない値を表示している以前基数の列が修正されます。

## <a name="sql-server-analysis-services-ctp-21"></a>SQL Server Analysis Services CTP 2.1
このリリースに新しい機能はありません。 このリリースの機能強化には、バグの修正とパフォーマンスの機能強化が含まれます。[動的管理ビュー](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV)。 Dmv は、ローカル サーバーの操作とサーバーの正常性に関する情報を返す SQL Server Profiler でクエリです。 詳細については、次を参照してください。、 [Analysis Services ブログ](https://blogs.msdn.microsoft.com/analysisservices/)です。

## <a name="sql-server-analysis-services-ctp-20"></a>SQL Server Analysis Services (CTP 2.0)
このリリースでは、表形式モデルの多くの新しい機能強化を含みます。

* 表形式モデルのメタデータをセキュリティで保護する、オブジェクト レベルのセキュリティ。
* 応答性の高い開発エクスペリエンスのトランザクション パフォーマンスの向上。
* 依存関係の分析を有効にして、レポート モデルを 1200 と 1400 の動的管理ビュー向上。
* 詳細行の式のオーサリング エクスペリエンスが改善されました。
* Power BI のフィールド リストで有用な場所に表示される階層と列を再利用します。
* 日付関係を簡単に日付フィールドに基づく日付ディメンションへのリレーションシップを作成します。
* Analysis Services の既定のインストール オプションは、表形式モードのようになりました。
* 新しいデータの取得 (電源 Qery) データ ソース。
* SSDT 用の DAX エディター。
* M クエリの既存の DirectQuery データ ソースをサポートします。
* SSMS の向上、表示、編集、およびスクリプトの構造化されたデータ ソースのサポートなどです。

この CTP 2.0 のリリースに関する詳細を取得するには、次を参照してください。、 [Analysis Services ブログ](https://blogs.msdn.microsoft.com/analysisservices/)です。

## <a name="sql-server-analysis-services-on-windows-ctp-14"></a>Windows CTP 1.4 で SQL Server Analysis Services
[SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate)と[SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms-release-candidate)プレビュー リリースは、SQL Server 2017 プレビュー リリースと一致します。 新機能を取得する、最新バージョンを使用することを確認します。 詳細については、次を参照してください。、 [Analysis Services ブログ](https://blogs.msdn.microsoft.com/analysisservices/)です。



## <a name="sql-server-analysis-services-on-windows-ctp-13"></a>Windows CTP 1.3 では、SQL Server Analysis Services

### <a name="encoding-hints"></a>エンコードのヒント

このリリースでは、メモリ内の大規模な表形式モデルの処理 (データの更新) を最適化するために使用される高度な機能、エンコードのヒントを紹介します。 エンコードして理解するには、次を参照してください。[パフォーマンス チューニングのテーブル モデルの SQL Server 2012 Analysis Services](https://msdn.microsoft.com/library/dn393915.aspx)エンコードを理解するには」のホワイト ペーパー。 ここで説明するエンコードの処理は、CTP 1.3 で適用します。

* 値のエンコードは、集計にのみ使用される通常の列のクエリ パフォーマンスの向上を提供します。

* ハッシュのエンコードが group by の列 (多くの場合、ディメンション テーブルの値) と外部キー用に推奨します。 文字列型の列は、常にエンコードされるハッシュです。

数値列には、いずれかのエンコード方法を使用できます。 各数値の列値またはハッシュのエンコードを適用するかどうかを決定するのサンプル値の取得と Analysis Services が、いずれかのテーブルが空の場合 (またはパーティションに分割せず)、テーブルの処理を開始、テーブル全体の処理操作が実行されて、. 既定では、値のエンコードを選択すると、列の個別の値のサンプルでは、十分な大きさ – それ以外の場合ハッシュのエンコードは通常説明圧縮効率の改善。 Analysis services、列が部分的に処理された後、データの分布に関する詳しい情報に基づくエンコード方式を変更し、エンコード プロセスを再起動することができます。 これは、もちろん処理時間が増加し、効率的ではありません。 パフォーマンス チューニングに関するホワイト ペーパーでは、さらに詳しく再エンコードについて説明し、SQL Server Profiler を使用することを検出する方法について説明します。

CTP 1.3. でのエンコードのヒントは、データ プロファイルからやトレース イベントを再エンコードへの応答の知識を指定されたエンコーディング メソッドの基本設定を指定するモデルを使用できます。 ハッシュでエンコードされた列での集計は列の値でエンコードされた値のエンコードとして指定できるこのような列のヒントよりも遅くなります。 優先順位が適用されることです。 は保証されません。そのため、設定とは対照的にヒントを勧めします。 エンコードのヒントを指定するには、列に EncodingHint プロパティを設定します。 使用可能な値は"Default"、"Value"および「ハッシュ」です。 ドキュメントの執筆時に、プロパティはまだ公開されません SSDT では、JSON ベースのメタデータを表形式モデル スクリプト言語 (TMSL)、または表形式オブジェクト モデル (TOM) を使用して設定する必要があります。 JSON ベースのメタデータを Model.bim ファイルからの次のスニペットは、Sales Amount 列のエンコード値を指定します。

```
{
    "name": "Sales Amount",
    "dataType": "decimal",
    "sourceColumn": "SalesAmount",
    "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",
    "sourceProviderType": "Currency",
    "encodingHint": "Value"
}
```

### <a name="extended-events-not-working-in-ctp-13"></a>拡張イベントの CTP 1.3. で動作していません
SSAS 拡張イベントは、CTP 1.3 では機能しません。 修正プログラムは、次の CTP で予定されています。

## <a name="sql-server-analysis-services-on-windows-ctp-12"></a>Windows CTP 1.2 の SQL Server Analysis Services

このリリースに新しい機能はありません。 バグ修正とパフォーマンス強化が実施されました。

最新のプレビュー リリースの SQL Server Data Tools (SSDT)、SQL Server 2017 CTP 1.2 と一致するを新しいクエリ エディターのメニュー、クイック アクセス機能と CTP 1.1 で導入された新しいの最新のデータの取得エクスペリエンスを向上させます。 

## <a name="sql-server-analysis-services-on-windows-ctp-11"></a>Windows CTP 1.1 の SQL Server Analysis Services 

このリリースでは、テーブル モデルの機能が強化されました。 

### <a name="1400-compatibility-level-for-tabular-models"></a>テーブル モデルの&1400; 互換性レベル
  この記事で説明している特徴と機能を利用するには、新規または既存のテーブル モデルを 1400 互換性レベルに設定する必要があります。 1400 互換性レベルのモデルを SQL Server 2016 SP1 以前に展開したり、低い互換性レベルにダウングレードしたりすることはできません。
  
  新規の 1400 互換性レベルのテーブル モデル プロジェクトを作成するか、既存のテーブル モデル プロジェクトを 1400 互換性レベルにアップグレードするには、 **SQL Server Data Tools (SSDT) 17.0 RC2** の [以前のリリース](https://go.microsoft.com/fwlink?LinkId=837939)をダウンロードしてインストールします。 
  
SSDT では、新しいテーブル モデル プロジェクトを作成するときに新しい 1400 互換性レベルを選択できます。 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)

>[!NOTE]
> SQL Server Data Tools (SSDT) の 12 月リリースで統合されたワークスペースでは、1400 互換性レベルをサポートしています。 ワークスペース サーバー インスタンスで新しいテーブル モデル プロジェクトを作成すると、展開するそのインスタンスまたはインスタンスは [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1 である必要があります。 

SSDT では、ソリューション エクスプ ローラーで、既存のテーブル モデルのアップグレードを右クリックして**Model.bim**、し、**プロパティ**、設定、**互換性レベル**プロパティ**SQL Server 2017 (1400)**です。 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

### <a name="modern-get-data-experience"></a>新しい Get Data エクスペリエンス
SQL Server Data Tools (SSDT) の最新のプレビュー リリースは、 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 1.1 リリースと合わせてし、1400 互換性レベルのテーブル モデルに新しい **Get Data** を導入しました。 この新機能は、Power BI Desktop と Microsoft Excel 2016 の同様の機能に基づいています。

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

>[!NOTE]
> このリリースでは、少数のデータ ソースがサポートされています。 今後の更新プログラムでは、追加のデータ ソースと機能がサポートされる予定です。

新しい Get Data エクスペリエンスの詳細については、 [Analysis Services チームのブログ](https://blogs.msdn.microsoft.com/analysisservices/2016/12/16/introducing-a-modern-get-data-experience-for-sql-server-2017-on-windows-ctp-1-1-for-analysis-services/)を参照してください。

## <a name="ragged-hierarchies"></a>不規則階層
テーブル モデルでは、親子階層をモデル化できます。 さまざまな数のレベルがある階層は、不規則階層とも呼ばれます。 既定で、最下位の子の下のレベルについては、不規則階層が空白で表示されます。 不規則階層の組織図の例を次に示します。

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

このリリースでは、 **[Hide Members]** (メンバーを隠す) プロパティが導入されました。 階層の **[Hide Members]** (メンバーを隠す) プロパティを **[Hide blank members]**(空白のメンバーを隠す) に設定できます。

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > モデルの空白のメンバーは、空白の文字列ではなく DAX の空白値で表されます。

**[Hide blank members]**(空白のメンバーを隠す) に設定し、モデルを展開すると、Excel のように、レポート クライアントに読みやすいバージョンの階層が表示されます。

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)

### <a name="detail-rows"></a>詳細行
メジャー値に使用するカスタム行セットを定義できるようになりました。 詳細行は、多次元モデルの既定のドリルスルー アクションと似ています。 エンドユーザーは詳細行を使用して、集計レベルよりも詳細な情報を表示できます。 

次のピボットテーブルは、Adventure Works サンプル テーブル モデルのインターネット売上の年別合計を示します。 メジャーの集計値を含むセルを右クリックし、 **[詳細の表示]** をクリックして詳細行を表示します。

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

プロパティが定義され、モデルが展開されている場合、ユーザーが **[詳細の表示]**を選択すると、カスタム行セットが返されます。 選択されたセルのフィルター コンテキストが自動的に使用されます。 この例では、2010 値の行のみが表示されます。

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
このリリースには、DAX 式の `IN` 演算子が含まれています。 これは、`WHERE` 句で複数の値を指定するために一般的に使用されている [`TSQL IN`](/sql-docs/docs/t-sql/language-elements/in-transact-sql) 演算子と似ています。

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

この場合、 `IN` 演算子は、各行が指定した色を示す 3 行の単一列テーブルを参照しています。 テーブル コンストラクター構文には、中かっこ ({}) を使用します。

`IN` 演算子は、 `CONTAINSROW` 関数と機能的に等価です。
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

テーブル コンストラクターでは、 `IN` 演算子も効果的に使用できます。 たとえば、次のメジャー フィルターは、製品の色やカテゴリの組み合わせ別にフィルター処理します。
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

たとえば、次のコードを使用して、 **TablePermission** クラスの **MetadataPermission** プロパティを **None**に設定すると、サンプル Adventure Works テーブル モデルの Product テーブルをセキュリティで保護できます。

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


