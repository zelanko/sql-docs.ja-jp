---
title: 保存して、ODBC の SQL Server Machine Learning Services を使用して SQL Server から R オブジェクトを読み込む
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1ed82ffe497af6393371486440e618c162406a01
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513048"
---
# <a name="save-and-load-r-objects-from-sql-server-using-odbc"></a>保存して、ODBC を使用して SQL Server から R オブジェクトを読み込む
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server R Services ではシリアル化された R オブジェクトをテーブルに格納した後で、必要に応じてテーブルからオブジェクトを読み込むことができます。その際に、R コードを再実行したり、モデルを再トレーニングしたりする必要はありません。 データベースで R オブジェクトを保存するこの機能は、モデルをトレーニングして保存し、後でスコアリングや分析にそれを使用するなどのシナリオでは重要です。

この重要な手順のパフォーマンスを向上させるため、現在、 **RevoScaleR** パッケージには新しいシリアル化と逆シリアル化関数が含まれています。これにより、パフォーマンスが大幅に向上し、オブジェクトをよりコンパクトに格納することができます。 この記事では、これらの関数とその使用方法について説明します。

## <a name="overview"></a>概要

現在、 **RevoScaleR** パッケージには新しい関数が含まれています。これにより、R オブジェクトを SQL Server に保存した後で、SQL Server テーブルからオブジェクトを読み取る作業がより簡単になります。 一般に、各関数呼び出しは、キーが、オブジェクトの名前は、単純なキー値ストアを使用して、キーに関連付けられている値はテーブルの内外で移動する varbinary R オブジェクトです。

SQL Server に R オブジェクトを保存、R 環境から直接には、次の必要があります。

+ 使用して SQL Server への接続が確立されている、 *RxOdbcData*データ ソース。
+ ODBC 接続経由で、新しい関数を呼び出す
+ 必要に応じて、オブジェクト、シリアル化されないことを指定できます。 次に、既定の圧縮アルゴリズムではなくを使用する新しい圧縮アルゴリズムを選択します。

既定では、SQL Server に移動するために R から呼び出されるオブジェクトはすべてシリアル化され、圧縮されます。 逆に、R コードで使用するために SQL Server テーブルからオブジェクトを読み込む場合、オブジェクトは逆シリアル化され、圧縮解除されます。

## <a name="list-of-new-functions"></a>新しい関数の一覧

- `rxWriteObject` は、ODBC データ ソースを使用して、R オブジェクトを SQL Server に書き込みます。

- `rxReadObject` は、ODBC データ ソースを使用して、SQL Server データベースから R オブジェクトを読み取ります。

- `rxDeleteObject` は、ODBC データ ソースで指定された SQL Server データベースから R オブジェクトを削除します。 キー/バージョンの組み合わせによって識別される複数のオブジェクトがある場合は、すべて削除されます。

- `rxListKeys` は、すべての使用可能なオブジェクトをキーと値のペアとして一覧表示します。 これは、R オブジェクトの名前とバージョンを特定する場合に役立ちます。

各関数の構文の詳細なヘルプが必要な場合は、R のヘルプを使用してください。 詳細についてはまた、 [ScaleR 参照](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)します。

## <a name="how-to-store-r-objects-in-sql-server-using-odbc"></a>ODBC を使用して SQL Server に R オブジェクトを格納する方法

この手順では、新しい関数を使用して、モデルを作成し、SQL Server に保存する方法を示します。

1. SQL Server の接続文字列をセットアップします。
   ```R
   conStr <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. 接続文字列を使用して、R で *rxOdbcData* データ ソース オブジェクトを作成します。
   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr)
   ```

3. 既存のテーブルがあり、古いバージョンのオブジェクトを追跡しない場合は、そのテーブルを削除します。

   ```R
   if(rxSqlServerTableExists(ds@table, ds@connectionString)) {
       rxSqlServerDropTable(ds@table, ds@connectionString)
       }
   ```
   
4. バイナリ オブジェクトを保存するために使用できるテーブルを定義します。

   ```R
   ddl <- paste(" CREATE TABLE [", ds@table, "] 
      (","  [id] varchar(200) NOT NULL,
       "," [value] varbinary(max),
       "," CONSTRAINT unique_id UNIQUE (id))", 
       sep = "") 
   ```
5. ODBC 接続を開き、テーブルを作成します。DDL ステートメントが完了したら、接続を閉じます。

   ```R
    rxOpen(ds, "w") 
    rxExecuteSQLDDL(ds, ddl) 
    rxClose(ds)
    ```
6. 保存する R オブジェクトを生成します。

   ```R
   infertLogit <- rxLogit(case ~ age + parity + education + spontaneous + induced, 
     data = infert)
   ```
6. 作成した *RxOdbcData* オブジェクトを使用して、モデルをデータベースに保存します。

   ```R
   rxWriteObject(ds, "logit.model", infertLogit)
   ```

## <a name="how-to-read-r-objects-from-sql-server-using-odbc"></a>ODBC を使用して SQL Server から R オブジェクトを読み取る方法

この手順では、新しい関数を使用して、SQL Server からモデルを読み込む方法を示します。

1. SQL Server の接続文字列をセットアップします。

   ```R
   conStr2 <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. 接続文字列を使用して、R で *rxOdbcData* データ ソース オブジェクトを作成します。

   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr2)
   ```
3. R オブジェクト名を指定して、テーブルからモデルを読み取ります。

   ```R
    infertLogit2 <- rxReadObject(ds, "logit.model")
   ```
