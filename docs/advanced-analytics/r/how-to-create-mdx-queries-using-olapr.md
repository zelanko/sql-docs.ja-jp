---
title: "OlapR を使用して作成する MDX クエリする方法 |Microsoft ドキュメント"
ms.custom: 
ms.prod: sql-non-specified
ms.date: 11/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: c12b988e-be7e-41ba-a84c-299a5c45d4ab
caps.latest.revision: "3"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 4ee223a3c27ee35a823917f9d1aefcd8fb86e80e
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-create-mdx-queries-using-olapr"></a>OlapR を使用して MDX クエリを作成する方法

[OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)パッケージは、SQL Server Analysis Services でホストされている多次元のモデルに対してクエリをサポートしています。 MDX を使用して既存のキューブに対してクエリを作成することができます、ディメンションとキューブの他のオブジェクトを探索し、データを取得する既存の MDX クエリに貼り付けます。

この記事では、olapR パッケージの 2 つの主な使用法について説明します。

+ [OlapR パッケージで提供されるコンス トラクターを使用して、R から、クエリを作成します。](#buildMDX)
+ [OlapR および OLAP プロバイダーを使用して、既存の有効な MDX クエリを実行します。](#executeMDX)

次の操作はサポートされていません。

+ 表形式モデルに対するクエリ
+ 新規の OLAP オブジェクトの作成
+ メジャーまたは値の計算を含むパーティションへの書き戻し

## <a name="buildMDX"></a>R からの MDX クエリを構築します。

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. `Query()` コンストラクターを使って、クエリ オブジェクトをインスタンス化します。

4. 以下のヘルパー関数を使って、MDX クエリに含めるディメンションとメジャーについての詳細を提供します。

     + `cube()` : SSAS データベースの名前を指定します。
     + `columns()`使用するメジャーの名前を指定、 **ON 列**引数。
     + `rows()`使用するメジャーの名前を指定、 **ON 行**引数。
     + `slicers()` : スライサーとして使うフィールドまたはメンバーを指定します。 スライサーとは、すべての MDX クエリ データに適用されるフィルターのようなものです。
     
     + `axis()` : クエリで使う追加の軸の名前を指定します。 
     
         OLAP キューブは、最大で 128 個のクエリ軸を含むことができます。 一般に、最初の 4 つの軸と呼びます**列**、**行**、**ページ**、および**チャプター**です。 
         
         クエリが比較的単純な場合は、 `columns`、 `rows`などの関数を使ってクエリを作成できます。 ただし、 `axis()` 関数を使って 0 以外のインデックス値を指定し、多くの修飾子を持つ MDX クエリを作成したり、修飾子として余分なディメンションを追加したりすることもできます。

5. 結果の形に応じて、ハンドルおよび完成した MDX クエリを `executeMD` または `execute2D`関数に渡します。

  + `executeMD` : 多次元配列を返します
  + `execute2D` : 2 次元 (表形式) のデータ フレームを返します

## <a name="executeMDX"></a>R からの有効な MDX クエリを実行します。

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. MDX クエリのテキストを格納する R 変数を定義します。

4. 結果の形に応じて、ハンドルおよび MDX クエリを含む変数を `executeMD` または `execute2D`関数に渡します。

    + `executeMD` : 多次元配列を返します
    + `execute2D` : 2 次元 (表形式) のデータ フレームを返します

## <a name="examples"></a>使用例

そのプロジェクトが広く利用可能で、Analysis Services に簡単に復元するバックアップ ファイルを含め、複数のバージョンであるために、次の例は、AdventureWorks データ マートおよびキューブのプロジェクトに基づきます。 既存のキューブをお持ちでない場合は、これらのオプションのいずれかのサンプル キューブを取得します。

+ 次のレッスン 4 まで Analysinotes Services のチュートリアルでこれらの例で使用されるキューブの作成: [OLAP キューブを作成します。](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

+ バックアップとして既存のキューブをダウンロードして、Analysis Services のインスタンスに復元します。 たとえば、このサイトで、zip 形式で完全に処理されたキューブ: [Adventure Works 多次元モデル SQL 2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334)です。 ファイルを抽出し、SSAS インスタンスに復元します。 詳細については、次を参照してください。[バックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)、または[Restore-asdatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)です。

### <a name="1-basic-mdx-with-slicer"></a>1.スライサーを使う基本的な MDX

この MDX クエリは、インターネットの販売数と販売金額の数と金額の_メジャー_を選択し、列軸に設定します。 SalesTerritory ディメンションのメンバーを *スライサー*として追加し、オーストラリアからの販売のみが計算で使われるようにクエリをフィルターします。

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ 列では、コンマ区切りの文字列の要素として複数のメジャーを指定できます。
+ 行軸では、"Product Line" ディメンションのすべての可能な値 (すべての MEMBERS) を使います。 
+ このクエリは、すべての国からのインターネット販売の _ロールアップ_ サマリーを含む 3 列のテーブルを返します。
+ WHERE 句を指定します、_スライサー軸_です。 この例では、スライサーのメンバーを使用して、 **SalesTerritory**オーストラリアからの売り上げ高のみを計算で使用できるように、クエリのフィルターを適用するにはディメンションです。

#### <a name="to-build-this-query-using-the-functions-provided-in-olapr"></a>olapR で提供される関数を使ってこのクエリを作成するには

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

qry <- Query()
cube(qry) <- "[Analysis Services Tutorial]"
columns(qry) <- c("[Measures].[Internet Sales Count]", "[Measures].[Internet Sales-Sales Amount]")
rows(qry) <- c("[Product].[Product Line].[Product Line].MEMBERS") 
slicers(qry) <- c("[Sales Territory].[Sales Territory Country].[Australia]")

result1 <- executeMD(ocs, qry)

```

#### <a name="to-run-this-query-as-a-predefined-mdx-string"></a>事前定義された MDX 文字列としてこのクエリを実行するには

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)

mdx <- "SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, {[Product].[Product Line].[Product Line].MEMBERS} ON ROWS FROM [Analysis Services Tutorial] WHERE [Sales Territory].[Sales Territory Country].[Australia]"

result2 <- execute2D(ocs, mdx)
```

SQL Server Management Studio で MDX ビルダーを使用してクエリを定義する MDX 文字列を保存して場合、は、次のように 0 から始まり、軸を数字には。 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

それでも、事前定義された MDX 文字列としてこのクエリを実行できます。 ただし、R を使用して同じクエリを作成する、`axis()`関数の場合、1 から始まる軸再設定する必要があります。

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2.SSAS インスタンス上のキューブとそのフィールドを調べる

`explore` 関数を使ってキューブ、ディメンション、またはメンバーのリストを取得し、クエリの作成で使うことができます。 これは、他の OLAP 参照ツールにアクセスできない場合、またはプログラムで MDX クエリを操作または作成する場合に便利です。

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>指定した接続で使用可能なキューブのリストを取得するには

表示権限のあるインスタンス上のすべてのキューブまたはパースペクティブを表示するには、 `explore`への引数としてハンドルを渡します。

> [!IMPORTANT]
> 最終的な結果が**いない**キューブです。True の場合だけを示すメタデータ操作が成功したことです。 無効な引数を渡すとエラーがスローされます。

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
explore(ocs)
```

| [結果]  |  
| ----|
| _Analysis Services Tutorial_|
|_Internet Sales_|
|_Reseller Sales_|
|_Sales Summary_|
|_[1] TRUE_|

#### <a name="to-get-a-list-of-cube-dimensions"></a>キューブ ディメンションのリストを取得するには

キューブまたはパースペクティブのすべてのディメンションを表示するには、キューブまたはパースペクティブの名前を指定します。

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| [結果]  |  
| ----|
| _Customer_|
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>指定したディメンションと階層のすべてのメンバーを取得するには

ソースを定義してハンドルを作成した後、取得するキューブ、ディメンション、および階層を指定します。

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs \<- OlapConnection(cnnstr)
explore(ocs, "Analysis Services Tutorial", "Product", "Product Categories", "Category")
```

| [結果]  |  
| ----|
| _Accessories_|
|_Bikes_|
|_Clothing_|
|_Components_|
|-> Assembly Components|
|-> Assembly Components|


戻り値の結果が付いているで項目 **->** 前のメンバーの子を表します。

## <a name="see-also"></a>参照

[R での OLAP キューブからデータの使用](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
