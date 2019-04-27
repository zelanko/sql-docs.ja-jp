---
title: R コード プロファイル関数の SQL Server Machine Learning サービスの使用します。
description: パフォーマンスが向上し、内部関数呼び出しに関する情報を返す R 関数のプロファイルを使用して SQL Server で R 計算をより迅速に結果を取得します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c9195a6c2b9a2192e9d8fd04ce3e5d2592b1b23e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642260"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>R コード プロファイル関数を使用して、パフォーマンスを向上させる
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server のリソースとツールを使用して R スクリプトの実行を監視できるほか、他の R パッケージが提供するパフォーマンス ツールを使用して、内部関数の呼び出しに関する情報を取得できます。 

> [!TIP]
> この記事では、開始するための基本的なリソースを提供します。 専門家によるガイダンスをお勧め、*パフォーマンス*セクション[Hadley Wickham 著"R の高度な"](http://adv-r.had.co.nz)します。

## <a name="using-rprof"></a>rprof の使用

[*rprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof)基本パッケージに含まれる関数は、 [ **utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1)既定で読み込まれます。 

一般に *rprof* 関数は、指定した間隔でファイルに呼び出し履歴を記述することで機能します。 使用することができますし、 [ *summaryRprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof)出力ファイルを処理する関数。 *rprof* の利点の 1 つは、サンプリングを実行するため、監視によるパフォーマンスの負荷を軽減することです。

コードで R プロファイルを使用するには、この関数を呼び出してパラメーター (書き込まれるログ ファイルの場所の名前など) を指定します。 コードでプロファイルをオンまたはオフにできます。 次の構文は、基本的な使用方法を示しています。 

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

Microsoft R Open、既定でインストールされるマニュアルには、拡張機能について説明している R 言語の開発に関するマニュアルが含まれています。[プロファイリングとデバッグ](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)詳しく説明します。 C:\Program files \microsoft SQL Server\MSSQL13 にコンピューターに、同じドキュメントが表示されます。MSSQLSERVER\R_SERVICES\doc\manual します。

## <a name="see-also"></a>関連項目

+ [R ユーティリティ パッケージ](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [Hadley Wickham 著"高度な R"](http://adv-r.had.co.nz)
