---
title: "R コードの関数のプロファイルを使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 132db249-b9f1-48f5-a63e-c9806cacc4af
caps.latest.revision: 6
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# R コードの関数のプロファイルを使用
を R スクリプトの実行を監視するのに SQL Server リソースとツールを使用する以外には、内部関数呼び出しに関する詳細情報を表示他の R パッケージで提供されるパフォーマンス ツールを使用することができます。 このトピックでは、開始するためのいくつかの基本的なリソースの一覧を示します。 専門的なガイダンスをお勧めの章で [パフォーマンス](http://adv-r.had.co.nz/Performance.html) ""高度な R""、Hadley Wickham による著書です。

## <a name="using-rprof"></a>RPROF を使用します。

*rprof* 基本パッケージに含まれる関数は、 **ユーティリティ**, 、既定で読み込まれます。 利点の 1 つ *rprof* は、サンプリング、したがって監視によるパフォーマンスの負荷を緩和することを実行しています。

R コードのプロファイリングを使用するのには、この関数を呼び出すし、書き込まれるログ ファイルの場所の名前を含む、そのパラメーターを指定します。 ヘルプを表示 *rprof* 詳細です。

一般に、 *rprof* ファイルに指定した間隔でコール スタックを記述して関数の動作です。 使用して、 *summaryRprof* 出力ファイルを処理する関数。 

プロファイリングにできますオンとオフをコードにします。 プロファイリングをオンにしたり、プロファイリングを一時停止、再起動への呼び出しのシーケンスを使用するよう *rprof*:

1. プロファイルの出力ファイルを指定します。

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. プロファイリングをオフにします。
    ```R
    Rprof(NULL)
    ```
    
3. プロファイリングを再開します。
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE] この関数を使用するには、Windows Perl がコードを実行しているコンピューターにインストールすることが必要です。 そのため、R 環境での開発中にコードをプロファイルし、SQL Server にデバッグ コードを展開することお勧めします。  


## <a name="r-system-functions"></a>R システム関数

R 言語には、システム環境変数の内容を返すための多くの基本パッケージ関数が含まれています。 

たとえば、R コードの一部として、ことができます `Sys.timezone` を現在のタイム ゾーンを取得または `Sys.Time` R. からシステム時刻を取得するには 

R システムの個々 の関数に関する情報を取得するには、R への引数として関数名を入力 `help()` R コマンド プロンプトからの関数です。

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>デバッグと R のプロファイリング

Microsoft R Open、既定でインストールされるのドキュメントには、手動でのプロファイリングとデバッグの詳細について説明している、R 言語の拡張機能の開発が含まれます。

この章も利用可能なオンライン: [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>R のヘルプ ファイルの場所

C:\Program files \microsoft SQL Server\MSSQL13 します。MSSQLSERVER\R_SERVICES\doc\manual


