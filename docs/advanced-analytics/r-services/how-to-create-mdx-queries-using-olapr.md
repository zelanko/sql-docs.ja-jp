---
title: "olapR を使って MDX クエリを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: c12b988e-be7e-41ba-a84c-299a5c45d4ab
caps.latest.revision: 3
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# olapR を使って MDX クエリを作成する方法
## <a name="how-to-build-an-mdx-query-from-r"></a>R から MDX クエリを作成する方法

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. `Query()` コンストラクターを使って、クエリ オブジェクトをインスタンス化します。

4. 以下のヘルパー関数を使って、MDX クエリに含めるディメンションとメジャーについての詳細を提供します。
     + `cube()`: SSAS データベースの名前を指定します。
     + `columns()`: ON COLUMNS 引数で使うメジャーの名前を指定します。  
     + `rows()`: ON ROWS 引数で使うメジャーの名前を指定します。
     + `slicers()`: スライサーとして使うフィールドまたはメンバーを指定します。 スライサーとは、すべての MDX クエリ データに適用されるフィルターのようなものです。
     
     + `axis()`: クエリで使う追加の軸の名前を指定します。 OLAP キューブは、最大で 128 個のクエリ軸を含むことができます。 一般に、最初の 4 つの軸は、列、行、ページ、およびチャプターと呼ばれます。 クエリが比較的単純な場合は、`columns`、`rows` などの関数を使ってクエリを作成できます。     
     ただし、`axis()` 関数を使って 0 以外のインデックス値を指定し、多くの修飾子を持つ MDX クエリを作成したり、修飾子として余分なディメンションを追加したりすることもできます。

5. 結果の形に応じて、ハンドルおよび完成した MDX クエリを `executeMD` または `execute2D` 関数に渡します。

  + `executeMD`: 多次元配列を返します
  + `execute2D`: 2 次元 (表形式) のデータ フレームを返します


## <a name="how-to-run-an-existing-mdx-query-from-r"></a>R から既存の MDX クエリを実行する方法

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. MDX クエリのテキストを格納する R 変数を定義します。

4. 結果の形に応じて、ハンドルおよび MDX クエリを含む変数を `executeMD` または `execute2D` 関数に渡します。

    + `executeMD`: 多次元配列を返します
    + `execute2D`: 2 次元 (表形式) のデータ フレームを返します



## <a name="examples"></a>使用例

### <a name="1-basic-mdx-with-slicer"></a>1.スライサーを使う基本的な MDX

この MDX クエリは、インターネットの販売数と販売金額の数と金額の_メジャー_を選択し、列軸に設定します。 SalesTerritory ディメンションのメンバーを*スライサー*として追加し、オーストラリアからの販売のみが計算で使われるようにクエリをフィルターします。

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[InternetSales-Sales Amount]} ON COLUMNS, 
{[Product].[Product Line].[Product Line].MEMBERS} ON ROWS 
FROM [Analysis Services Tutorial] 
WHERE [Sales Territory].[Sales Territory Country].[Australia]
```

+ 列では、コンマ区切りの文字列の要素として複数のメジャーを指定できます。
+ 行軸では、"Product Line" ディメンションのすべての可能な値 (すべての MEMBERS) を使います。 
+ このクエリは、すべての国からのインターネット販売の_ロールアップ_ サマリーを含む 3 列のテーブルを返します。 
+ WHERE 句は_スライサー軸_です。 スライサーは、SalesTerritory ディメンションのメンバーを使って、オーストラリアからの販売のみが計算で使われるようにクエリをフィルターします。

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

SQL Server Management Studio で MDX ビルダーを使ってクエリを定義し、MDX 文字列を保存した場合、次に示すように、軸には 0 から始まる番号が付けられることに注意してください。 

~~~~
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Country].[Australia]
~~~~

それでも、事前定義された MDX 文字列としてこのクエリを実行できます。 ただし、`axis()` 関数を使って R で同じクエリを作成するには、軸に 1 から始まる番号を付ける必要があります。


### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2.SSAS インスタンス上のキューブとそのフィールドを調べる

`explore` 関数を使ってキューブ、ディメンション、またはメンバーのリストを取得し、クエリの作成で使うことができます。 これは、他の OLAP 参照ツールにアクセスできない場合、またはプログラムで MDX クエリを操作または作成する場合に便利です。

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>指定した接続で使用可能なキューブのリストを取得するには

表示権限のあるインスタンス上のすべてのキューブまたはパースペクティブを表示するには、`explore` への引数としてハンドルを渡します。
結果の最後にあるのはキューブではないことに注意してください。TRUE は、メタデータ操作が成功したことを示しているだけです。 無効な引数を渡すとエラーがスローされます。

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
ocs <- OlapConnection(cnnstr)
explore(ocs, "Sales")
```

| [結果]  |  
| ----|
| _Customer_|
|_Date_|
|_Region_|


#### <a name="to-return-all-members-of-the-specified-dimension-and-hierarchy"></a>指定したディメンションと階層のすべてのメンバーを取得するには

ソースを定義してハンドルを作成した後、取得するキューブ、ディメンション、および階層を指定します。
返される結果の項目で前に **->** が付いているものは、前のメンバーの子を表すことに注意してください。

```R
cnnstr <- "Data Source=localhost; Provider=MSOLAP;"
ocs <- OlapConnection(cnnstr)
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



## <a name="see-also"></a>参照

[R での OLAP キューブからのデータの使用](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md)