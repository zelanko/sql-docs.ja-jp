---
title: SQL Server 2017 Analysis Services の新機能新機能 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 76e9bedbd7807b78288a901d0b2a7674232c7e91
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145987"
---
# <a name="whats-new-in-sql-server-2017-analysis-services"></a>SQL Server 2017 Analysis Services の新機能新機能
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

SQL Server 2017 Analysis Services は、SQL Server 2012 以降の最も重要な拡張機能のいくつかのように参照してください。 これまでよりもより強力な表形式モデルは、このリリース (SQL Server 2012 Analysis Services で初めて導入された) 表形式モードでの成功を構築します。

多次元モードと SharePoint モード用の Power Pivot は、多くの Analysis Services の展開のホチキス止めです。 Analysis Services の製品ライフ サイクルの成熟したはこれらのモードです。 このリリースでこれらのモードのいずれかの新機能はありません。 ただし、バグの修正とパフォーマンスの向上が含まれます。

SQL Server 2017 Analysis Services では、ここで説明する機能が含まれます。 それらを利用するには、最新バージョンを使用する必要がありますも[SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) (SSDT) と[SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md) (SSMS)。 SSDT および SSMS は、通常、SQL Server の新機能と一致する新規および改良された機能で毎月更新されます。  

されるがどのように把握しておくもすべての新機能の詳細については重要ですが、このリリースと今後のリリースで廃止された非推奨とされます。 チェック アウトを必ず[旧バージョンとの互換性 (SQL Server 2017 Analysis Services)](analysis-services-backward-compatibility-sql2017.md)します。

このリリースでは、主要な新機能のいくつか見てをみましょう。

## <a name="1400-compatibility-level-for-tabular-models"></a>テーブル モデルの1400 互換性レベル
  新機能と説明されている機能の多くの機能をここで実行するには、新規または既存のテーブル モデルを設定するか、1400 互換性レベルにアップグレードしてする必要があります。 1400 互換性レベルのモデルを SQL Server 2016 SP1 以前に展開したり、低い互換性レベルにダウングレードしたりすることはできません。 詳細についてを参照してください。 [Analysis Services 表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)します。
  
SSDT では、新しいテーブル モデル プロジェクトを作成するときに新しい 1400 互換性レベルを選択できます。 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)


ソリューション エクスプ ローラーで、SSDT で既存のテーブル モデルをアップグレードするを右クリックして**Model.bim**、し、**プロパティ**、設定、**互換性レベル**プロパティ**SQL Server 2017 (1400)** します。 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

留意することが重要するダウン グレードできません。 既存のモデルを 1400 にアップグレードした後。 1200 モデル データベースのバックアップを保管してください。

## <a name="modern-get-data-experience"></a>新しい Get Data エクスペリエンス
SQL Server Data Tools (SSDT) を表形式モデルにデータ ソースからデータをインポートする際に、最新が導入されています**データの取得**モデルの 1400 互換性レベルが発生します。 この新機能は、Power BI Desktop と Microsoft Excel 2016 の同様の機能に基づいています。 新しい Get Data エクスペリエンスは、クエリ ビルダーのデータの取得と M 式を使用して、膨大なデータ変換とデータのマッシュ アップ機能を提供します。

新しい Get Data エクスペリエンスでは、さまざまな種類のデータ ソースのサポートを提供します。 今後、更新プログラムではさらに多くのサポートが含まれます。

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

 強力で直感的なユーザー インターフェイスは、データとデータ変換/マッシュ アップ機能をより簡単に選択します。

![高度なマッシュ アップ](../analysis-services/media/as-get-data-advanced.png)


最新の Get Data エクスペリエンスし、を 1400 互換性レベル 1200 の表形式モデルの既存の upraded に M マッシュ アップ機能は適用されません。 新しいエクスペリエンスは、1400 互換性レベルで作成された新しいモデルにのみ適用されます。

## <a name="encoding-hints"></a>エンコードのヒント
このリリースでは、高度な機能を使用して大規模なメモリ内表形式モデルの処理 (データの更新) を最適化するエンコードのヒントを紹介します。 エンコードを理解を参照してください。[パフォーマンス チューニングの表形式モデル SQL Server 2012 Analysis Services で](https://msdn.microsoft.com/library/dn393915.aspx)エンコードをより深く理解するには、に関するホワイト ペーパー。

* 値のエンコードは、通常の集計をのみ使用される列のクエリ パフォーマンスの向上を提供します。

* ハッシュのエンコードは、group by の列 (ディメンション テーブルの値では多くの場合) と外部キーの優先です。 文字列型の列は、常に、エンコードされたハッシュです。

数値列には、これらのエンコード方法のいずれかを使用できます。 Analysis Services が、いずれかのテーブルが空の (パーティションの有無にかかわらず) の場合、テーブルの処理を開始または、テーブル全体の処理操作が実行される、サンプルの値は、各数値の列値またはハッシュ エンコードを適用するかどうかを判断するの取得します。 既定では、値のエンコード選択ときに十分では、列の個別の値のサンプル:、それ以外の場合圧縮効率の改善が提供通常ハッシュ エンコードされます。 Analysis Services データの分散の詳細に基づいて列が部分的に処理した後、エンコード方式を変更し、エンコード プロセス; を再起動する可能性があります。ただし、この処理時間を向上し、効率的ではありません。 パフォーマンス チューニングに関するホワイト ペーパーでは、さらに詳しく再エンコードについて説明し、SQL Server Profiler を使用してそれを検出する方法について説明します。

エンコードのヒントからデータ プロファイルやトレース イベントを再エンコードへの応答に関する予備知識を指定するエンコード方式の優先順位を指定するモデルを使用できます。 以降、列のハッシュ エンコードでの集計は、列の値でエンコードされた値のエンコードがヒントとして指定する、このような列のよりも遅くなります。 優先順位が適用されることは保証されません。 設定ではなく、ヒントになります。 エンコードのヒントを指定するには、列に EncodingHint プロパティを設定します。 使用可能な値は、"Default"、"Value"および「ハッシュ」です。 Model.bim ファイルから JSON ベースのメタデータの次のスニペットでは、Sales Amount 列のエンコード値を指定します。

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

## <a name="ragged-hierarchies"></a>不規則階層
テーブル モデルでは、親子階層をモデル化できます。 さまざまな数のレベルがある階層は、不規則階層とも呼ばれます。 既定で、最下位の子の下のレベルについては、不規則階層が空白で表示されます。 不規則階層の組織図の例を次に示します。

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

このリリースでは、 **[Hide Members]** (メンバーを隠す) プロパティが導入されました。 階層の **[Hide Members]** (メンバーを隠す) プロパティを **[Hide blank members]**(空白のメンバーを隠す) に設定できます。

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > モデルの空白のメンバーは、空白の文字列ではなく DAX の空白値で表されます。

**[Hide blank members]**(空白のメンバーを隠す) に設定し、モデルを展開すると、Excel のように、レポート クライアントに読みやすいバージョンの階層が表示されます。

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)


## <a name="detail-rows"></a>詳細行
メジャー値に使用するカスタム行セットを定義できるようになりました。 詳細行は、多次元モデルの既定のドリルスルー アクションと似ています。 エンドユーザーは詳細行を使用して、集計レベルよりも詳細な情報を表示できます。 

次のピボットテーブルは、Adventure Works サンプル テーブル モデルのインターネット売上の年別合計を示します。 メジャーの集計値を含むセルを右クリックし、 **[詳細の表示]** をクリックして詳細行を表示します。

![AS_Show_Details](../analysis-services/media/as-show-details.png)

既定では、Internet Sales テーブルの関連データが表示されます。 この制限付きの動作はユーザーにとって意味がないこともよくあります。顧客名や注文情報など、役に立つ情報を示す必要な列がテーブルに表示されないことがあるためです。 詳細行では、メジャーに **[詳細行の式]** プロパティを指定できます。

#### <a name="detail-rows-expression-property-for-measures"></a>メジャーの [詳細行の式] プロパティ
モデルの作成者は、メジャーの **[詳細行の式]** プロパティを使用して、エンドユーザーに返す列と行をカスタマイズすることができます。

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

[SELECTCOLUMNS](https://msdn.microsoft.com/library/mt761759.aspx) DAX 関数は、詳細行式でよく使用します。 次の例では、サンプル Adventure Works テーブル モデルの Internet Sales テーブルの行について返される列を定義しています。

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
メジャーだけでなく、テーブルにも、詳細行式を定義できるプロパティがあります。 **[Default Detail Rows Expression]** (既定の詳細行の式) プロパティは、テーブル内のすべてのメジャーについて既定として動作します。 独自の式が定義されていないメジャーは、テーブルから式を継承し、テーブルに対して定義されている行を表示します。 これにより、式の再利用し、式を継承する新しいメジャーを後で自動的にテーブルに追加します。

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>DETAILROWS DAX 関数
このリリースでは、詳細行式で定義された行セットを返す新しい `DETAILROWS` DAX が追加されました。 機能は MDX の `DRILLTHROUGH` ステートメントと似ています。MDX のこのステートメントも、テーブル モデルに定義されている詳細行式と互換性があります。

次の DAX クエリは、メジャーまたはそのテーブルの詳細行式に定義されている行セットを返します。 式が定義されていない場合、メジャーを含むテーブルなので、Internet Sales テーブルのデータが返されます。

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="object-level-security"></a>オブジェクト レベルのセキュリティ
このリリースで導入[オブジェクト レベル セキュリティ](../analysis-services/tabular-models/object-level-security.md)テーブルおよび列。 テーブルおよび列のデータへのアクセスを制限、だけでなく、機密性の高いテーブルおよび列名を保護できます。 これで、悪意のあるユーザーがテーブルの存在を検出できなくなります。

JSON ベースのメタデータ、Tabular Model Scripting Language (TMSL)、または表形式オブジェクト モデル (TOM) を使用して、オブジェクト レベルのセキュリティを設定する必要があります。 

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

## <a name="dynamic-management-views-dmvs"></a>動的管理ビュー (DMV)
[Dmv](../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)はローカル サーバーの操作やサーバーの正常性に関する情報を返す SQL Server Profiler でクエリします。
このリリースには機能強化が含まれています[動的管理ビュー](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV)、互換性レベル 1200 と 1400 の表形式モデル用です。

[DISCOVER_CALC_DEPENDENCY](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset) 1200 と 1400 の表形式モデルを使用したようになりました。 表形式 1400 モデルでは、M パーティション、M 式および構造化データ ソース間の依存関係を表示します。 詳細についてを参照してください、 [Analysis Services ブログ](https://blogs.msdn.microsoft.com/analysisservices/2017/07/17/whats-new-in-sql-server-2017-rc1-for-analysis-services/)します。

[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset)の向上は、この DMV には、メジャーの次元を表示するさまざまなクライアント ツールで使用されるために含まれています。 たとえば、Excel ピボット テーブルの探索機能により、ユーザーが選択されているメジャーに関連付けられたディメンションをクロス ドリルします。 このリリースでは、正しくない値が表示されていた以前基数の列を修正します。

## <a name="dax-enhancements"></a>DAX の機能強化
このリリースには、新しい DAX 関数と機能のサポートが含まれています。 を利用するためには、最新バージョンの SSDT を使用する必要があります。 詳細についてを参照してください。[新しい DAX 関数](https://msdn.microsoft.com/library/mt704075.aspx)します。

DAX の新しい機能の最も重要な情報の 1 つでは、新しい[IN 演算子/関数の CONTAINSROW](https://msdn.microsoft.com/library/mt842621.aspx)の DAX 式。 これは、 [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) 句で複数の値を指定するために一般的に使用されている `WHERE` 演算子と似ています。

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

## <a name="additional-improvements"></a>追加の機能強化
すべての新機能だけでなく、Analysis Services、SSDT および SSMS もとおりです。 次の機能強化

* 階層および列の再利用は、Power BI のフィールド リストでより便利な場所に表示します。
* 日付フィールドに基づく日付ディメンションへのリレーションシップを簡単に作成、日付リレーションシップ。
* Analysis Services の既定のインストール オプションは、表形式モードのようになりました。
* 新しいデータの取得 (Power Query) のデータ ソース。
* SSDT 用の DAX エディター。
* 既存の DirectQuery データ ソースは、M クエリをサポートします。
* SSMS の向上、表示、編集、およびスクリプトの構造化データ ソースのサポートなど。



## <a name="see-also"></a>関連項目
[SQL Server 2017 リリース ノートします。](../sql-server/sql-server-2017-release-notes.md)   
[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)
