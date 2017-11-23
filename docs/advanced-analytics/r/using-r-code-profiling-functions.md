---
title: "R コード プロファイル関数の使用 | Microsoft Docs"
ms.custom: 
ms.date: 11/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 132db249-b9f1-48f5-a63e-c9806cacc4af
caps.latest.revision: "6"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 745133739eed6e7ca08ffd55e51f479304566ec9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-r-code-profiling-functions"></a>R コード プロファイル関数の使用
SQL Server のリソースとツールを使用して R スクリプトの実行を監視できるほか、他の R パッケージが提供するパフォーマンス ツールを使用して、内部関数の呼び出しに関する情報を取得できます。 このトピックでは、始めるための基本的なリソースの一覧を提供します。 専門的なガイダンスについては、Hadley Wickham 著 "Advanced R" の、[Performance](http://adv-r.had.co.nz/Performance.html) の章をお勧めします。

## <a name="using-rprof"></a>rprof の使用

*rprof* は基本パッケージ **utils** に含まれる関数で、既定で読み込まれます。 *rprof* の利点の 1 つは、サンプリングを実行するため、監視によるパフォーマンスの負荷を軽減することです。

コードで R プロファイルを使用するには、この関数を呼び出してパラメーター (書き込まれるログ ファイルの場所の名前など) を指定します。 詳細については、*rprof* のヘルプを参照してください。

一般に *rprof* 関数は、指定した間隔でファイルに呼び出し履歴を記述することで機能します。 次に *summaryRprof* 関数を使用して、出力ファイルを処理できます。 

コードでプロファイルをオンまたはオフにできます。 プロファイルをオンにするには、プロファイルを一時停止してから再開し、一連の *rprof* の呼び出しを使用します。

1. プロファイルの出力ファイルを指定します。

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. プロファイルをオフにします。
    ```R
    Rprof(NULL)
    ```
    
3. プロファイルを再開します。
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE]
> この関数を使用するには、コードを実行するコンピューターに Windows Perl がインストールされている必要があります。 このため、R 環境での開発中にコードをプロファイルし、デバッグ済みのコードを SQL Server に展開することをお勧めします。  


## <a name="r-system-functions"></a>R システム関数

R 言語には、システム変数の内容を返すための多くの基本パッケージ関数が含まれています。 

たとえば、R コードの一部として、`Sys.timezone` を使用して現在のタイム ゾーンを取得したり、`Sys.Time` を使用して R からシステム時刻を取得することがあります。 

個別の R システム関数の情報を取得するには、R コマンド プロンプトから、R `help()` 関数の引数として関数名を入力します。

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>R のデバッグとプロファイル

既定でインストールされる Microsoft R Open のドキュメントには R 言語の拡張機能の開発に関するマニュアルが含まれており、プロファイルとデバッグの詳細について説明しています。

この章はオンラインでも入手できます。[https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>R のヘルプ ファイルの場所

C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual



