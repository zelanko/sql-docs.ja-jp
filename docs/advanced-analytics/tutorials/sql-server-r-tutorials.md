---
title: "SQL Server R チュートリアル |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ee88d7dbbb1a10c11a1e1c50cb4c048189f9d026
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="sql-server-r-tutorials"></a>SQL Server R チュートリアル

この記事では、チュートリアルおよび SQL Server 2016 または SQL Server 2017 で R の使用方法を示すサンプルの一覧を示します。 これらのサンプルとデモでは、学びます。

+ T-SQL から R を実行する方法
+ リモートおよびローカルの計算コンテキスト、および SQL Server コンピューターを使用して R コードを実行する方法とは
+ ストアド プロシージャに R コードをラップする方法
+ SQL の運用環境のための R コードを最適化します。
+ 機械学習をアプリケーションに埋め込むための実際のシナリオ

要件およびセットアップについては、次を参照してください。[の前提条件](#bkmk_Prerequisites)です。

## <a name="bkmk_sqltutorials"></a>R のチュートリアル

特に記載のない限り、チュートリアルは SQL Server 2016 の R Services 用に開発されてし、大幅な変更なしで SQL Server 2017 Machine Learning サービスで動作する必要があります。

すべてのチュートリアルが広く利用 RevoScaleR パッケージでの機能の SQL Server の計算コンテキスト。

+ [R と SQL Server のデータ サイエンス Deep Dive](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

  RevoScaleR パッケージで関数を使用する方法を説明します。 R と SQL Server、およびスイッチとの間のデータの移動は、特定のタスクに合わせてコンテキストを計算します。 モデルおよびプロットを作成し、開発環境と、データベース サーバーの間で移動します。

  **対象:**データ科学者や開発者は、R 言語に慣れているユーザーおよび強化された R パッケージと Revolution Analytics によって Microsoft R 内の関数について説明したいのです。

  **要件:**基本的な R の知識。 SQL Server R Services または R と Machine Learning のサービスにサーバーへのアクセスセットアップのヘルプを参照してください。[の前提条件](#bkmk_Prerequisites)です。

+ [SQL 開発者のためのデータベース内 R の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

  ビルドおよびのみを使用して、完全な R ソリューションの配置[!INCLUDE[tsql](../../includes/tsql-md.md)]ツールです。

  ソリューションを実稼働環境に移動に重点を置いています。 ストアド プロシージャに R コードをラップし、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存し、パラメーター化された呼び出しを R モデルに行い、予測を実行する方法について学習します。

  **対象:** SQL 開発者、アプリケーション開発者、または SQL 技術者 R ソリューションをサポートし、R モデルを SQL Server に配置する方法を学習する必要の。

  **要件:** R 環境は必要ありません。 すべての R コードが提供され、のみを使用して完全なソリューションをビルドする[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]慣れ親しんだビジネス インテリジェンスや SQL 開発ツールです。 ただし、R の基本的な知識をお勧めします。

  インストールされ有効になっている、R 言語には、SQL Server へのアクセスが必要です。 セットアップのヘルプを参照してください。[の前提条件](#bkmk_Prerequisites)です。

+ [クイック スタート: T-SQL で R を使用します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

  このクイック スタートで R を使用するための基本構文を説明する[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

  T-SQL から R ランタイムを呼び出し、SQL コードに R 関数をラップし、R の出力と R モデルを SQL テーブルに保存するストアド プロシージャを実行する方法を説明します。

  **対象:**を初めて使用する機能、およびストアド プロシージャから R を呼び出すための基本事項を説明する方のためです。

  **要件:** R または必要な SQL を認識していません。 ただし、SQL Server Management Studio またはデータベースに接続して、T-SQL を実行する別のクライアントのいずれかが必要です。 お勧め、無料[Visual Studio Code の MSSQL 拡張子](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)T-SQL クエリに慣れていない場合。

  SQL Server R Services または既に有効になっている R で Machine Learning サービスにサーバーへのアクセスも必要です。 セットアップのヘルプを参照してください。[の前提条件](#bkmk_Prerequisites)です。

+ [データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

  最初から最後まで、データを取得し、SQL Server に保存、R によるデータ分析し、グラフを構築すると、データ サイエンス プロセスを示します。

  グラフィックスの間を移動する方法を学びます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]R、および比較特徴エンジニア リング T-SQL で R 関数。 最後で予測モデルを使用する方法を学習[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バッチ スコアリングと、単一行のスコア付けします。

  **対象:** R と SQL Server Management Studio などの開発ツールに慣れている方のためです。

  **要件:** R 開発環境にアクセスし、R コマンドを実行する方法を知っている必要があります。 PowerShell を使用すると、ニューヨーク タクシー データセットのダウンロードが必要です。 SQL Server R Services または既に有効になっている R で Machine Learning サービスにサーバーへのアクセスが必要です。 セットアップのヘルプを参照してください。[の前提条件](#bkmk_Prerequisites)です。

## <a name ="bkmk_samples"></a>製品サンプル

これらのサンプルおよびデモは、実際のアプリケーションに埋め込まれた分析を使用できるさまざまな方法を強調表示する SQL Server 開発チームによって提供されます。

+ [R と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Ski レンタル ビジネス可能性がありますの機械学習を将来のレンタルを予測するのに役立つ、今後の要求を満たすには、ビジネス プランとスタッフを使用する方法について説明します。

+ [顧客を実行する R と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  セグメントの顧客売上データに基づいて教師なし学習を使用します。

## <a name="bkmk_Prerequisites"></a>前提条件

これらのチュートリアルとサンプルを使用するには、次のサーバー製品の 1 つをインストールする必要があります。

+ SQL Server 2016 R Services (In-database)
  
  R. は必ず、機械学習の機能をインストールし、有効に外部スクリプトをサポートしています。

+ SQL Server 2017 Machine Learning Services (In-database)
  
  R、または Python をサポートしています。 機械学習機能とをインストールする言語を選択し、外部スクリプトを有効にする必要があります。

SQL Server セットアップを実行した後、これらの重要な手順を必ず。

+ 実行して、外部スクリプト実行機能を有効にします。`sp_configure 'external scripts enabled', 1`
+ サーバーの再起動
+ 外部のランタイムを呼び出して、サービスに必要なアクセス許可があることを確認します。
+ SQL ログインまたは Windows ユーザー アカウントが、データを読み取ると、このサンプルで必要なすべてのデータベース オブジェクトを作成するのには、サーバーに接続するために必要な権限を持つことを確認してください。

問題が実行する場合は、いくつかの一般的な問題には、この記事を参照してください: [Machine Learning のサービスのトラブルシューティング](../machine-learning-troubleshooting-faq.md)
