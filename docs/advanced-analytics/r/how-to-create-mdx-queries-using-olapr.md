---
title: SQL Server の Machine Learning で olapR を使用して R でのクエリを MDX を作成する方法 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76602c41fd6f8d300c240a6072f2a6decec18e3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203594"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>OlapR を使用して R で MDX クエリを作成する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)パッケージは、SQL Server Analysis Services でホストされているキューブに対して MDX クエリをサポートしています。 既存のキューブに対してクエリを作成することができます、ディメンションとキューブの他のオブジェクトを探索し、データを取得する既存の MDX クエリに貼り付けます。

この記事の 2 つの主な用途の説明、 **olapR**パッケージ。

+ [OlapR パッケージで提供されるコンス トラクターを使用して、R からの MDX クエリを構築します。](#buildMDX)
+ [OlapR および OLAP プロバイダーを使用して、既存の有効な MDX クエリを実行します。](#executeMDX)

次の操作はサポートされていません。

+ 表形式モデルに対する DAX クエリ
+ 新規の OLAP オブジェクトの作成
+ メジャーまたは値の計算を含むパーティションへの書き戻し

## <a name="buildMDX"></a> R からの MDX クエリを構築します。

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. `Query()` コンストラクターを使って、クエリ オブジェクトをインスタンス化します。

4. 以下のヘルパー関数を使って、MDX クエリに含めるディメンションとメジャーについての詳細を提供します。

     + `cube()` : SSAS データベースの名前を指定します。 名前付きインスタンスに接続する場合は、コンピューター名とインスタンス名を提供します。 
     + `columns()` 使用するメジャーの名前を指定、 **ON 列**引数。
     + `rows()` 使用するメジャーの名前を指定、 **ON 行**引数。
     + `slicers()` : スライサーとして使うフィールドまたはメンバーを指定します。 スライサーとは、すべての MDX クエリ データに適用されるフィルターのようなものです。
     
     + `axis()` : クエリで使う追加の軸の名前を指定します。 
     
         OLAP キューブは、最大で 128 個のクエリ軸を含むことができます。 一般に、最初の 4 つの軸と呼びます**列**、**行**、**ページ**、および**チャプター**です。 
         
         クエリが比較的単純な場合は、 `columns`、 `rows`などの関数を使ってクエリを作成できます。 ただし、 `axis()` 関数を使って 0 以外のインデックス値を指定し、多くの修飾子を持つ MDX クエリを作成したり、修飾子として余分なディメンションを追加したりすることもできます。

5. 結果の形状に応じて、次の関数のいずれかに、ハンドルと、完成した MDX クエリを渡します。 

  + `executeMD` : 多次元配列を返します
  + `execute2D` : 2 次元 (表形式) のデータ フレームを返します

## <a name="executeMDX"></a> R からの有効な MDX クエリを実行します。

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. MDX クエリのテキストを格納する R 変数を定義します。

4. 結果の形に応じて、ハンドルおよび MDX クエリを含む変数を `executeMD` または `execute2D`関数に渡します。

    + `executeMD` : 多次元配列を返します
    + `execute2D` : 2 次元 (表形式) のデータ フレームを返します

## <a name="examples"></a>使用例

そのプロジェクトが広く利用可能で、Analysis Services に簡単に復元するバックアップ ファイルを含め、複数のバージョンであるために、次の例は、AdventureWorks データ マートおよびキューブのプロジェクトに基づきます。 既存のキューブをお持ちでない場合は、これらのオプションのいずれかのサンプル キューブを取得します。

+ 次のレッスン 4 まで Analysis Services のチュートリアルでこれらの例で使用される、キューブの作成: [OLAP キューブを作成します。](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

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
+ このクエリは 3 つの列を含むテーブルを返します、_ロールアップ_すべての国からのインターネット販売の概要です。
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

名前付きインスタンスの場合は、必ず R. の制御文字と見なすことが任意の文字をエスケープするには たとえば、次の接続文字列は、OLAP01、ContosoHQ をという名前のサーバー上のインスタンスを参照します。

```R
cnnstr <- "Data Source=ContosoHQ\\OLAP01; Provider=MSOLAP;"
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

ソースを定義してハンドルを作成した後、取得するキューブ、ディメンション、および階層を指定します。 戻り値の結果が付いている項目に**->** 前のメンバーの子を表します。

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


## <a name="see-also"></a>参照

[R での OLAP キューブからデータの使用](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
