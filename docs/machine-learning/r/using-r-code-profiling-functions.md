---
title: R コード プロファイル関数を使用してパフォーマンスを向上させる
description: R プロファイリング関数を使用することで、パフォーマンスを向上させるのに役立つ情報を収集し、SQL Server での R 計算の結果をより速く得られるようにします。 *rprof* 関数は、内部関数呼び出しに関する情報を収集して返します。
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 12/12/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e65171fa0222c0c581f692bede727dc4366c9c53
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180442"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>R コード プロファイル関数を使用してパフォーマンスを向上させる
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

SQL Server のリソースとツールを使用して R スクリプトの実行を監視できるほか、他の R パッケージが提供するパフォーマンス ツールを使用して、内部関数の呼び出しに関する情報を取得できます。 

> [!TIP]
> この記事では、作業を開始するための基本的なリソースについて説明します。 専門家によるガイダンスとしては、[Hadley Wickham 著 "Advanced R"](http://adv-r.had.co.nz) の「*Performance*」の章をお勧めします。

## <a name="using-rprof"></a>rprof の使用

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) は、基本パッケージ [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1) に含まれる関数で、既定で読み込まれます。 

一般に *rprof* 関数は、指定した間隔でファイルに呼び出し履歴を記述することで機能します。 その後、[*summaryRprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) 関数を使用して、出力ファイルを処理できます。 *rprof* の利点の 1 つは、サンプリングを実行するため、監視によるパフォーマンスの負荷を軽減することです。

コードで R プロファイルを使用するには、この関数を呼び出してパラメーター (書き込まれるログ ファイルの場所の名前など) を指定します。 コードでプロファイルをオンまたはオフにできます。 基本的な使用法を次の構文に示します。 

```R
# Specify profiling output file.
varOutputFile <- "C:/TEMP/run001.log")
Rprof(varOutputFile)

# Turn off profiling
Rprof(NULL)
    
# Restart profiling
Rprof(append=TRUE)
```

> [!NOTE]
> この関数を使用するには、コードを実行するコンピューターに Windows Perl がインストールされている必要があります。 このため、R 環境での開発中にコードをプロファイルし、デバッグ済みのコードを SQL Server に展開することをお勧めします。  


## <a name="r-system-functions"></a>R システム関数

R 言語には、システム変数の内容を返すための多くの基本パッケージ関数が含まれています。 たとえば、R コードの一部として、`Sys.timezone` を使用して現在のタイム ゾーンを取得したり、`Sys.Time` を使用して R からシステム時刻を取得することがあります。 

個別の R システム関数の情報を取得するには、R コマンド プロンプトから、R `help()` 関数の引数として関数名を入力します。

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>R のデバッグとプロファイル

既定でインストールされる Microsoft R Open のドキュメントには、R 言語の拡張機能の開発に関するマニュアルが含まれており、[プロファイルとデバッグ](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)の詳細について説明しています。 お使いのコンピューターでこちらから同じドキュメントを取得できます。C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual

## <a name="see-also"></a>関連項目

+ [utils R パッケージ](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [Hadley Wickham 著 "Advanced R"](http://adv-r.had.co.nz)
