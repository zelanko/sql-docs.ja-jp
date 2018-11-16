---
title: R コード プロファイル関数 (SQL Server Machine Learning) を使用して |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 64f065df5f5769e37bb1d5a8dbc2fba2d5f936ee
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703970"
---
# <a name="using-r-code-profiling-functions"></a>R コード プロファイル関数の使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server のリソースとツールを使用して R スクリプトの実行を監視できるほか、他の R パッケージが提供するパフォーマンス ツールを使用して、内部関数の呼び出しに関する情報を取得できます。 このトピックでは、始めるための基本的なリソースの一覧を提供します。 専門家のガイダンスについては、お勧めします」の章で[パフォーマンス](https://adv-r.had.co.nz/Performance.html)"Advanced R"、Hadley Wickham による著書 『 します。

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

章は、オンラインでも使用できます。 [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>R のヘルプ ファイルの場所

C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual



