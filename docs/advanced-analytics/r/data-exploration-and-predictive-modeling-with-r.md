---
title: R でのデータ探索および予測モデリング | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 04/18/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf6de7e2-f394-4b8a-a4b7-0b8dadf25426
caps.latest.revision: ''
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 09f3ec8f5171050082ab4bc5ede085387682a33e
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="data-exploration-and-predictive-modeling-with-r"></a>R でのデータ探索および予測モデリング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server との統合により可能なデータ サイエンス プロセスの機能強化について説明します。

適用されます SQL Server 2016 R Services、SQL Server 2017 マシン Learnign Services。

## <a name="the-data-science-process"></a>データ サイエンス プロセス

多くの場合、データ サイエンティストは R を使用してデータを探索し、予測モデルを構築します。 通常、適切な予測モデルが構築されるまで、試行錯誤が繰り返されます。 経験豊富なデータ サイエンティストであれば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、RODBC パッケージを使用してローカル ワークステーションにデータをフェッチし、データを探索して標準的な R パッケージを使用して予測モデルを構築する場合があります。

ただし、このアプローチには多数の欠点は、その hae がエンタープライズでの R に広く普及を妨害します。 

+ データ移動が遅い、非効率である、あるいは安全でないを指定できます。
+ R 自体がパフォーマンスとスケールに関する制限

これらの欠点は、大量のデータを移動して分析する必要がある場合、またはコンピューターで使用可能なメモリに収まらないデータ セットを使用する場合に、より明白になります。

新しいスケーラブル パッケージと R 関数に含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]多くの課題を克服できます。 

## <a name="whats-different-about-revoscaler"></a>RevoScaleR の違いは何ですか。

**RevoScaleR** パッケージには、並列処理とスケール機能を提供するために再設計された、最も一般的ないくつかの R 関数の実装が含まれます。 詳細については、次を参照してください。[分散コンピューティング RevoScaleR を使用した](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing)です。

また、RevoScaleR パッケージでは *実行コンテキスト*の変更もサポートされます。 つまり、ソリューション全体または 1 つの関数のみの場合、ローカル ワークステーションではなく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターのリソースを使用して計算を行う必要があることを示すことができます。 これを行う利点は複数あります。不要なデータ移動を回避し、サーバー コンピューター上のより多くの計算リソースを活用することができます。

## <a name="r-environment-and-packages"></a>R の環境とパッケージ

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] でサポートされている R 環境は、ランタイム、オープン ソース言語、複数のパッケージでサポートされ拡張されたグラフィック エンジンで構成されます。 この言語では、パッケージを使用して実装されるさまざまな拡張機能を使用できます。  

### <a name="using-other-r-packages"></a>その他の R パッケージを使用します。

Microsoft Machine Learning に含まれている独自の R ライブラリに加えて、ソリューションでほぼすべての R パッケージを使用することができますを含みます。

+ パブリック リポジトリの汎用 R パッケージ。 データ サイエンティストが使用できる 6,000 個を超えるパッケージをホストする、CRAN などのパブリック リポジトリから最も一般的なオープン ソース R パッケージを取得することができます。
  
  Windows プラットフォームの場合、R パッケージは zip ファイルとして提供され、GPL ライセンス下でダウンロードしてインストールできます。  
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で使用するためにサードパーティ製のパッケージをインストールする方法については、「[Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md) (SQL Server に追加の R パッケージをインストールする)」をご覧ください。  
  
+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で提供される追加のパッケージとライブラリ。   
  
     **RevoScaleR** パッケージには、高パフォーマンスのビッグ データ分析、一般的なデータ サイエンス タスクをサポートする強化バージョンの関数、Naive Bayes 用に最適的化された学習者、線形回帰、タイム シリーズ モデル、ニューラル ネットワーク、高度な算術ライブラリなどが含まれています。  
  
     **RevoPemaR** パッケージでは、R で独自の並列外部メモリ アルゴリズムを開発できます。  
  
     これらのパッケージとその使用方法の詳細については、次を参照してください。 [RevoScaleR は](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-introduction)と[RevoPemaR 始める](https://msdn.microsoft.com/microsoft-r/pemar-getting-started)です。 

+ **MicrosoftML**大幅に最適化された機械学習アルゴリズムと Microsoft データ サイエンス チームからのデータ変換のコレクションを格納します。 Azure Machine Learning でアルゴリズムの多くも使われます。 詳細については、次を参照してください。 [MicrosoftML パッケージを使用して](../../advanced-analytics/using-the-microsoftml-package.md)です。

### <a name="r-development-tools"></a>R 開発ツール

R ソリューションを開発する場合は、Microsoft R クライアントをダウンロードすることを確認します。 この無料のダウンロードには、リモート計算コンテキストとスケーラブルな alorithms をサポートするために必要なライブラリが含まれています。

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** R ランタイムのディストリビューションと、標準的な R 演算のパフォーマンスを向上させる、Intel Math Kernel Library などの一連のパッケージ。  
  
+ **RevoScaleR:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに計算をプッシュできる R パッケージ。 [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)]に含まれている新しいスケーラブル パッケージと R 関数を使用して克服できます。 パフォーマンスとスケーラビリティを高めるために再設計された一連の共通の R 関数も含まれています。 これらの強化された関数は、 **rx** プレフィックスで識別できます。 さまざまなソースの強化されたデータ プロバイダーも含まれており、これらの関数には **Rx** のプレフィックスが付いています。

など、R をサポートしている任意の Windows ベースのコード エディターを使用する[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]または RStudio です。 [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] をダウンロードすれば、RGui.exe などの R の一般的なコマンド ライン ツールも取得できます。

## <a name="use-new-data-sources-and-compute-contexts"></a>使用して新しいデータ ソースと計算コンテキスト

RevoScaleR パッケージを使用して接続するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R コードで使用するこれらの関数を探します。

+ **RxSqlServerData** は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に含まれている新しいスケーラブル パッケージと R 関数を使用して克服できます。
  
     R コードでこの関数を使用して、 *データ ソース*を定義します。 データ ソース オブジェクトではデータがあるテーブルとサーバーを指定し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対するデータの読み取りおよび書き込みタスクを管理します。
  
-   **RxInSqlServer** 関数を使用して、*計算コンテキスト*を指定できます。  つまり、R コードを実行する必要がある場所 (ローカル ワークステーションや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターなど) を示すことができます。  詳細については、次を参照してください。 [RevoScaleR 関数](https://msdn.microsoft.com/microsoft-r/scaler/scaler)です。
  
     計算コンテキストを設定した場合、影響を受けるのはリモートの実行コンテキストをサポートする計算のみです。これは、R 演算が RevoScaleR パッケージと、関連する関数で提供されることを意味します。 一般に、CRAN の標準パッケージに基づく R ソリューションはリモートの計算コンテキストでは実行できませんが、T-SQL で開始した場合は [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューター上で実行できます。 ただし、`rxExec` 関数を使用して R 関数を個別に呼び出し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] でリモートで実行できます。

データ ソースと実行コンテキストを作成および操作する方法の例については、これらのチュートリアルを参照してください。

+ [データ サイエンスの詳細情報](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Microsoft R を使用するデータの分析](https://msdn.microsoft.com/en-us/microsoft-r/data-analysis-in-microsoft-r)

## <a name="deploy-r-code-to-production"></a>実稼働環境に R コードを配置します。

データ サイエンスの重要な部分は、自分の分析を他のユーザーに提供したり、予測モデルを使用してビジネスの結果またはプロセスを改善することです。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]では、R スクリプトまたはモデルの準備ができている場合、運用環境に簡単に移行することができます。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行するコードの移行方法の詳細については、「[Operationalizing Your R Code (R コードの運用)](../../advanced-analytics/r/operationalizing-your-r-code.md)」をご覧ください。

通常、デプロイ プロセスは、運用環境では不要なコードを削除するためのスクリプトのクリーンアップから始まります。 データに近いの計算を移動するより効率的に移動、要約、またはより R. 内のすべてのデータを表示する方法を見つける可能性があります。 パフォーマンスを向上させる方法について、データベース開発者に、データ サイエンティストを参照してください、ソリューションの場合に特にデータのクレンジングまたはエンジニア リングする機能がありますでより効率的に SQL のことをお勧めします。 モデルの構築またはスコアリングのワークフローが失敗していないことと、入力データが適切な形式で使用できることを確認するために、ETL プロセスの変更が必要な場合があります。

## <a name="see-also"></a>参照

[基本 R と ScaleR 関数の比較](https://msdn.microsoft.com/microsoft-r/scaler/compare-base-r-scaler-functions)

[SQL Server と連動する ScaleR 関数](../../advanced-analytics/r/scaler-functions-for-working-with-sql-server-data.md)
