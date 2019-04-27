---
title: データ探索と R - SQL Server Machine Learning Services を使用した予測モデリング
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: de293cd7caf481c51e4195a82ac036526c477739
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642015"
---
# <a name="data-exploration-and-predictive-modeling-with-r-in-sql-server"></a>データ探索と SQL Server で R を使用した予測モデリング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server との統合により可能なデータ サイエンス プロセスの機能強化について説明します。

適用対象SQL Server 2016 R Services、SQL Server 2017 Machine 必要ですサービス

## <a name="the-data-science-process"></a>データ サイエンス プロセス

多くの場合、データ サイエンティストは R を使用してデータを探索し、予測モデルを構築します。 通常、適切な予測モデルが構築されるまで、試行錯誤が繰り返されます。 経験豊富なデータ サイエンティストであれば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続し、RODBC パッケージを使用してローカル ワークステーションにデータをフェッチし、データを探索して標準的な R パッケージを使用して予測モデルを構築する場合があります。

ただし、このアプローチには、多くの欠点を hae、エンタープライズでの R の広く普及が阻害します。 

+ データの移動は、低速、非効率的なまたは安全でないです。
+ R 自体がパフォーマンスとスケールに関する制限

これらの欠点は、移動、大量のデータの分析や、コンピューターで使用できるメモリに収まらないデータ セットを使用する必要があるとは明らかになります。

スケーラブルな新しいパッケージと R の関数に含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]これらの課題の多くを解決するためにします。 

## <a name="whats-different-about-revoscaler"></a>RevoScaleR の違いは何ですか。

**RevoScaleR** パッケージには、並列処理とスケール機能を提供するために再設計された、最も一般的ないくつかの R 関数の実装が含まれます。 詳細については、次を参照してください。[分散 RevoScaleR を使用したコンピューティング](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-distributed-computing)します。

また、RevoScaleR パッケージでは *実行コンテキスト*の変更もサポートされます。 つまり、ソリューション全体または 1 つの関数のみの場合、ローカル ワークステーションではなく、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターのリソースを使用して計算を行う必要があることを示すことができます。 これを行う利点は複数あります。不要なデータ移動を回避し、サーバー コンピューター上のより多くの計算リソースを活用することができます。

## <a name="r-environment-and-packages"></a>R の環境とパッケージ

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] でサポートされている R 環境は、ランタイム、オープン ソース言語、複数のパッケージでサポートされ拡張されたグラフィック エンジンで構成されます。 この言語では、パッケージを使用して実装されるさまざまな拡張機能を使用できます。  

### <a name="using-other-r-packages"></a>その他の R パッケージを使用します。

ソリューションのほぼすべての R パッケージを使用するだけでなく Microsoft Machine Learning に含まれている独自の R ライブラリを含みます。

+ パブリック リポジトリの汎用 R パッケージ。 データ サイエンティストが使用できる 6,000 個を超えるパッケージをホストする、CRAN などのパブリック リポジトリから最も一般的なオープン ソース R パッケージを取得することができます。
  
  Windows プラットフォームの場合、R パッケージは zip ファイルとして提供され、GPL ライセンス下でダウンロードしてインストールできます。  
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で使用するためにサードパーティ製のパッケージをインストールする方法については、「[Install Additional R Packages on SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md) (SQL Server に追加の R パッケージをインストールする)」をご覧ください。  
  
+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で提供される追加のパッケージとライブラリ。   
  
     **RevoScaleR** パッケージには、高パフォーマンスのビッグ データ分析、一般的なデータ サイエンス タスクをサポートする強化バージョンの関数、Naive Bayes 用に最適的化された学習者、線形回帰、タイム シリーズ モデル、ニューラル ネットワーク、高度な算術ライブラリなどが含まれています。  
  
     **RevoPemaR** パッケージでは、R で独自の並列外部メモリ アルゴリズムを開発できます。  
  
     これらのパッケージとその使用方法の詳細については、次を参照してください。[は RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)と[RevoPemaR の概要](https://docs.microsoft.com/machine-learning-server/r/how-to-developer-pemar)します。 

+ **MicrosoftML**大幅に最適化された機械学習アルゴリズムと Microsoft データ サイエンス チームからのデータ変換のコレクションが含まれています。 アルゴリズムの多くは Azure Machine Learning でも使用されます。 詳細については、次を参照してください。 [SQL Server の MicrosoftML](ref-r-microsoftml.md)します。

### <a name="r-development-tools"></a>R 開発ツール

R ソリューションを開発する際に Microsoft R Client をダウンロードすることを確認します。 この無料のダウンロードには、リモート計算コンテキストとスケーラブルな alorithms をサポートするために必要なライブラリが含まれています。

+ **[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]:** R ランタイムと一連の標準的な R 演算のパフォーマンスを向上させる、Intel math kernel library などのパッケージの配布。  
  
+ **RevoScaleR:** インスタンスにできるようにする R パッケージが計算をプッシュ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] 。 パフォーマンスとスケーラビリティを高めるために再設計された一連の共通の R 関数も含まれています。 これらの強化された関数は、 **rx** プレフィックスで識別できます。 さまざまなソースの強化されたデータ プロバイダーも含まれており、これらの関数には **Rx** のプレフィックスが付いています。

など、R をサポートする任意の Windows ベースのコード エディターを使用する[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]または RStudio です。 [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] をダウンロードすれば、RGui.exe などの R の一般的なコマンド ライン ツールも取得できます。

## <a name="use-new-data-sources-and-compute-contexts"></a>使用して新しいデータ ソースと計算コンテキスト

RevoScaleR パッケージを使用して接続するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R コードで使用するこれらの関数を探します。

+ **RxSqlServerData** は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に含まれている新しいスケーラブル パッケージと R 関数を使用して克服できます。
  
     R コードでこの関数を使用して、 *データ ソース*を定義します。 データ ソース オブジェクトではデータがあるテーブルとサーバーを指定し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対するデータの読み取りおよび書き込みタスクを管理します。
  
-   **RxInSqlServer** 関数を使用して、*計算コンテキスト*を指定できます。  つまり、R コードを実行する必要がある場所 (ローカル ワークステーションや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターなど) を示すことができます。  詳細については、次を参照してください。 [RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)します。
  
     計算コンテキストを設定した場合、影響を受けるのはリモートの実行コンテキストをサポートする計算のみです。これは、R 演算が RevoScaleR パッケージと、関連する関数で提供されることを意味します。 一般に、CRAN の標準パッケージに基づく R ソリューションはリモートの計算コンテキストでは実行できませんが、T-SQL で開始した場合は [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューター上で実行できます。 ただし、`rxExec` 関数を使用して R 関数を個別に呼び出し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] でリモートで実行できます。

データ ソースと実行コンテキストを作成および操作する方法の例については、これらのチュートリアルを参照してください。

+ [データ サイエンスの詳細情報](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)  
+  [Microsoft R を使用したデータの分析](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)

## <a name="deploy-r-code-to-production"></a>R コードを運用環境にデプロイします。

データ サイエンスの重要な部分は、自分の分析を他のユーザーに提供したり、予測モデルを使用してビジネスの結果またはプロセスを改善することです。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]では、R スクリプトまたはモデルの準備ができている場合、運用環境に簡単に移行することができます。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行するコードの移行方法の詳細については、「[Operationalizing Your R Code (R コードの運用)](../../advanced-analytics/r/operationalizing-your-r-code.md)」をご覧ください。

通常、デプロイ プロセスは、運用環境では不要なコードを削除するためのスクリプトのクリーンアップから始まります。 データに近い場所に計算を移動すると場合より効率的に移動し、要約、またはより R. 内のすべてのデータを表示する方法があります。 パフォーマンスを向上させる方法について、データベース開発者とデータ サイエンティストを参照してくださいは、この solution の場合は特にデータ クレンジングまたは機能エンジニア リングがある方が効果的な SQL のことをお勧めします。 モデルの構築またはスコアリングのワークフローが失敗していないことと、入力データが適切な形式で使用できることを確認するために、ETL プロセスの変更が必要な場合があります。

## <a name="see-also"></a>参照

[基本 R と RevoScaleR 関数の比較](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r)

[SQL Server で RevoScaleR ライブラリ](ref-r-revoscaler.md)
