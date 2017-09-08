---
title: "機械学習で SQL Server の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09d6e887a8c64c98a1c3f68c78b07c26da6ffb76
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-machine-learning-in-sql-server"></a>機械学習で SQL Server の概要

マイクロソフトは、オンプレミスとクラウドの両方の機械学習ソリューションのスケーラブルな統合セットを提供します。

+ **統合**、SQL Server で R、Python またはを実行することができます。 これを簡単にマージし、エンタープライズ プロセス ETL やデータをレポートし、エンジニア リング、モデルの作成、およびスコア付けの機能などサイエンス タスク。
+ **スケーラブルな**のため、データ サイエンティストを開発およびラップトップでは、ソリューションをテストしてから展開する複数のプラットフォームの分散したりなどのキー操作の並列処理モデルのトレーニングおよびスコア付けします。 サポートされているプラットフォームには、Windows、Hadoop, Spark での SQL Server が含まれます。

この記事では、Microsoft Machine Learning のプラットフォームでは、各製品のリソースへのリンクを提供します。

## <a name="machine-learning-in-sql-server"></a>機械学習の SQL server

+ SQL Server 2017

  以降で SQL Server 2017 CTP 2.0 のサポート、Python が追加されて、広範なマシン ラーニング ソリューションの Machine Learning サービス (In-database) のサポートを反映するために名前が変更されました。 これで、R、または Python コードを実行する SQL ツールを使用して、機械学習タスクを自動化できます。 または、として、SQL Server コンピューターを使用して、_計算コンテキスト_リモート開発環境から起動されたジョブにします。

    + [SQL Server での Python のアーキテクチャの概要](python/architecture-overview-sql-server-python.md)
    + [SQL Server R Services または Machine Learning のサービスのセットアップします。](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

+ SQL Server 2016

  SQL Server 2016 では、ストアド プロシージャを使用して SQL Server で R コードの実行をサポートします。 これにより、簡単に SQL ツールを使用して機械学習タスクを自動化します。 または、リモート ラップトップまたは R 開発環境から R コードを実行するにとして SQL Server コンピューターを使用しているときに、_計算コンテキスト_です。

  この統合により、データのセキュリティと使用して、管理、R. によって使用されるリソースのバランスをとる

    + [開始する契約 SQL Server R Services を取得します。](r/getting-started-with-sql-server-r-services.md)
    + [SQL Server R Services または Machine Learning のサービスのセットアップします。](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

## <a name="microsoft-machine-learning-server-microsoft-r-server"></a>マイクロソフトの機械学習のサーバー (Microsoft R Server)

Microsoft Machine Learning のサーバーをインストールするオプションは、スケーラブルな分散した機械学習、ジョブを実行するときに、SQL Server データベース エンジンの使用などを統合しない必要がある企業のお客様をサポートするために SQL Server 2017 で提供されます。SQL のコンテキストを計算します。

SQL Server 2016 では、Microsoft R Server をインストールするのにオプションを使用します。
  
  + [Introducing Microsoft R Server (Microsoft R Server の概要)](https://msdn.microsoft.com/microsoft-r/rserver)
  
MSDN から使用可能なプラットフォームに応じたインストーラーを R サーバーをインストールすることもできます。

  + [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
  + [R Server for Linux](https://msdn.microsoft.com/microsoft-r/rserver-install-linux-server)
  + [R Server for Hadoop](https://msdn.microsoft.com/microsoft-r/rserver-install-hadoop)

> [!IMPORTANT]
> R Server を使用して Python を実行する場合は、必ず最新のバージョンをインストールする**Machine Learning サーバー**、これは SQL Server 2017 セットアップを通してのみ入手できます。
> 
>    + [Microsoft R Server または Machine Learning のサーバーのセットアップします。](../advanced-analytics/r/create-a-standalone-r-server.md)

## <a name="related-products"></a>関連する製品

+ [データ サイエンス クライアントをセットアップします。](../advanced-analytics/r/set-up-a-data-science-client.md)

  既にインストールされている場合、機械学習のサーバー製品のいずれか、この記事は、ツール、および必要なライブラリを含む、ソリューションの開発とテストは別のコンピューターを設定する方法に関する情報を提供します。

+ [データ サイエンス仮想マシン](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

  機械学習ソリューション、Azure Marketplace からこの完全なマシンを取得することによって学習にエントリをすぐに開始します。 (頻繁に簡略化"DSVM") データ サイエンス仮想マシンには、SQL Server、Microsoft Machine Learning サーバー、およびすべての開発ツールが含まれています。
  
  データ サイエンス仮想マシン (DSVM) の最新バージョンは、Windows 10 のクリーンなカスタマイズ可能な外観を提供する、Windows 2016 のプレビュー版で実行されます。 NVIDIA ドライバー、CUDA Toolkit 8.0、および GPU のワークロードの NVIDIA cuDNN ライブラリは、既に構成されては取得されます。

## <a name="resources-for-learning"></a>学習用リソース

+ [Machine learning のチュートリアル](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

  SQL Server 2017 と SQL Server 2017 を使用して、マシン学習ソリューションについて学習するためのすべてのリソースの一覧を検索するには、ここから開始します。

### <a name="r-tutorials"></a>R のチュートリアル

+ [SQL Server R チュートリアル](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

   SQL Server で R を実行、作成し、リモート計算コンテキストを使用してまたは SQL Server を使用して R でシミュレーションを実行する方法を説明します。
   
   R IDE を開くことがなく、完全な R ソリューションを SQL Server Management Studio から実行できるように、「すべてのコードが提供される」チュートリアルが含まれます。

+ [短い関数を 25 で R と ScaleR を調べる](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

   R 初めてですか。 Microsoft R (または RevoScaleR) を比較する方法には、標準的な R お考えでしょうか。 R Server は、これらのクイック起動を参照してください。

### <a name="python-tutorials"></a>Python のチュートリアル

+ [SQL Server の Python のチュートリアル](../advanced-analytics/tutorials/sql-server-r-tutorials.md)

  SQL Server で Python を実行する方法を説明します。 Python を使用して、モデルをビルドし、SQL Server のデータをスコア付けに使用します。

   SQL 開発者のため、エンド ツー エンドのソリューションでは、SQL Server Management Studio から Python を実行する必要があります。 すべてのコードを提供します。

+ [発行および Python コードを使用します。](../advanced-analytics/python/publish-consume-python-code.md)

  このチュートリアルは、Machine Learning のサーバーを使用して web サービスにモデルを配置に必要なすべてのコードに付属します。

### <a name="product-samples-with-code"></a>コードでの製品サンプル

SQL Server 開発チームのこれらのソリューションは、Python または R のいずれかで実行され、機械学習をビジネス アプリケーションと統合するための一般的なシナリオを示します。

+ [SQL Server と R を使用してインテリジェンス アプリを構築する](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

+ [SQL Server および Python とインテリジェントなアプリをビルドします。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

### <a name="data-science-solution-templates"></a>データ サイエンス ソリューション テンプレート

Microsoft データ サイエンス チームからのソリューション テンプレートは、特定の産業またはシナリオに合わせて調整する完全なサンプル ソリューションを表します。 高速で、ソリューションを実装するのに役立つかを示すためのベスト プラクティスの構成要素の役目を意図しています。 各テンプレートには、サンプル データとカスタマイズ可能なコードが含まれています。

+ [ソリューション テンプレート](../advanced-analytics/tutorials/data-science-scenarios-and-solution-templates.md)

## <a name="next-steps"></a>次の手順

[SQL Server の Machine Learning のサービスを概要します。](../advanced-analytics/r/getting-started-with-sql-server-r-services.md)

[マイクロソフトの機械学習のサーバーを概要します。](../advanced-analytics/r/getting-started-with-microsoft-r-server-standalone.md)

