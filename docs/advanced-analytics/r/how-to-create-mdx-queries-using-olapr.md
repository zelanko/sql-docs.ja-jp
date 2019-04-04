---
title: OlapR - SQL Server Machine Learning Services を使って R で MDX クエリを作成する方法
description: SQL Server では、olapR パッケージ ライブラリを使用して、R スクリプトの言語で MDX クエリを記述します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1bee5741d00e4043314c36800cd4fe5cf61aab48
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510559"
---
# <a name="how-to-create-mdx-queries-in-r-using-olapr"></a>OlapR を使って R で MDX クエリを作成する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[OlapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)パッケージは、SQL Server Analysis Services でホストされているキューブに対して MDX クエリをサポートしています。 既存のキューブに対してクエリを作成する、ディメンションおよびその他のキューブ オブジェクトを探索、およびデータを取得する既存の MDX クエリに貼り付けることができます。

この記事の 2 つの主な用途を説明します、 **olapR**パッケージ。

+ [OlapR パッケージで提供されるコンス トラクターを使用して、R から MDX クエリを構築します。](#buildMDX)
+ [OlapR と OLAP プロバイダーを使用して、既存の有効な MDX クエリを実行します。](#executeMDX)

次の操作がサポートされていません。

+ 表形式モデルに対する DAX クエリ
+ 新規の OLAP オブジェクトの作成
+ メジャーまたは集計を含む、パーティションへの書き戻し

## <a name="buildMDX"></a> R から MDX クエリを構築します。

1. OLAP データ ソース (SSAS インスタンス) および MSOLAP プロバイダーを指定する接続文字列を定義します。

2. `OlapConnection(connectionString)` 関数を使って MDX クエリのハンドルを作成し、接続文字列を渡します。

3. `Query()` コンストラクターを使って、クエリ オブジェクトをインスタンス化します。

4. 以下のヘルパー関数を使って、MDX クエリに含めるディメンションとメジャーについての詳細を提供します。

     + `cube()` : SSAS データベースの名前を指定します。 名前付きインスタンスに接続する場合は、コンピューター名とインスタンス名を提供します。 
     + `columns()` 使用するメジャーの名前を指定、 **: ON COLUMNS**引数。
     + `rows()` 使用するメジャーの名前を指定、 **: ON ROWS**引数。
     + `slicers()` : スライサーとして使うフィールドまたはメンバーを指定します。 スライサーとは、すべての MDX クエリ データに適用されるフィルターのようなものです。
     
     + `axis()` : クエリで使う追加の軸の名前を指定します。 
     
         OLAP キューブは、最大で 128 個のクエリ軸を含むことができます。 一般に、最初の 4 つの軸と呼びます**列**、**行**、**ページ**、および**章**します。 
         
         クエリが比較的単純な場合は、 `columns`、 `rows`などの関数を使ってクエリを作成できます。 ただし、 `axis()` 関数を使って 0 以外のインデックス値を指定し、多くの修飾子を持つ MDX クエリを作成したり、修飾子として余分なディメンションを追加したりすることもできます。

5. 結果の形に応じて、次の関数のいずれかにして、ハンドルと完成した MDX クエリを渡します。 

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

次の例は、そのプロジェクトは広く普及して、複数のバージョンでは、Analysis Services に簡単に復元するバックアップ ファイルを含むために、AdventureWorks データ マートとキューブのプロジェクトに基づいています。 既存のキューブを持っていない場合は、これらのオプションのいずれかのサンプル キューブを取得します。

+ これらの例で使用されるキューブを作成するには、次のレッスン 4 まで Analysis Services チュートリアル。[OLAP キューブを作成します。](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

+ 既存のキューブをバックアップとしてをダウンロードして、Analysis Services のインスタンスに復元します。 たとえば、このサイトには、zip 形式で完全に処理されたキューブが用意されています。[Adventure Works 多次元モデル SQL 2014](https://msftdbprodsamples.codeplex.com/downloads/get/882334)します。 ファイルを抽出し、SSAS インスタンスに復元します。 詳細については、[バックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)、または[Restore-asdatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)を参照してください。

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
+ このクエリは 3 つの列を含むテーブルを返します、_ロールアップ_すべての国からのインターネット販売の概要。
+ WHERE 句を指定します、_スライサー軸_します。 この例で、スライサーがのメンバーを使用して、 **SalesTerritory**オーストラリアからの販売のみが計算で使われるように、クエリをフィルター処理するディメンション。

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

名前付きインスタンスの場合は、R での制御文字を考慮することがある文字をエスケープすることを確認します。 たとえば、次の接続文字列は、ContosoHQ という名前のサーバー インスタンス OLAP01 を参照します。

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

SQL Server Management Studio で MDX ビルダーを使用してクエリを定義する MDX 文字列を保存すると、次のように、0 から始まる軸を番号には。 

```MDX
SELECT {[Measures].[Internet Sales Count], [Measures].[Internet Sales-Sales Amount]} ON AXIS(0), 
   {[Product].[Product Line].[Product Line].MEMBERS} ON AXIS(1) 
   FROM [Analysis Services Tutorial] 
   WHERE [Sales Territory].[Sales Territory Countr,y].[Australia]
```

それでも、事前定義された MDX 文字列としてこのクエリを実行できます。 ただしを使用して R を使用して同じクエリを作成、`axis()`関数、1 から始まる軸再設定する必要があります。

### <a name="2-explore-cubes-and-their-fields-on-an-ssas-instance"></a>2.SSAS インスタンス上のキューブとそのフィールドを調べる

`explore` 関数を使ってキューブ、ディメンション、またはメンバーのリストを取得し、クエリの作成で使うことができます。 これは、他の OLAP 参照ツールにアクセスできない場合、またはプログラムで MDX クエリを操作または作成する場合に便利です。

#### <a name="to-list-the-cubes-available-on-the-specified-connection"></a>指定した接続で使用可能なキューブのリストを取得するには

表示権限のあるインスタンス上のすべてのキューブまたはパースペクティブを表示するには、 `explore`への引数としてハンドルを渡します。

> [!IMPORTANT]
> 最終的な結果が**いない**キューブ。True の場合だけを示すメタデータ操作が成功したことです。 無効な引数を渡すとエラーがスローされます。

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


## <a name="see-also"></a>関連項目

[R での OLAP キューブからのデータの使用](../../advanced-analytics/r/using-data-from-olap-cubes-in-r.md)
