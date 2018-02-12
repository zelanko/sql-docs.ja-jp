---
title: "どのような &#39; s Machine Learning のサービスの新機能 |Microsoft ドキュメント"
ms.date: 01/08/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: c5f9810dfb057045fd1ec0ba25fd7651b2e10ea1
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="whats-new-in-machine-learning-services-in-sql-server"></a>SQL Server の Machine Learning のサービスの新機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 では、Microsoft には、SQL Server R Services、SQL Server データベース エンジンと、R 言語を統合することにより、エンタープライズ規模のデータ サイエンスをサポートする機能が導入されました。

SQL Server 2017、データベースに統合された機械学習は一般的な Python 言語のサポートを追加するより強力なになりました。 新しい名前は、新しい言語のサポートと共に: **Machine Learning Services (In-database)**です。

最新のお知らせは、ここをキャッチします。 [SQL Server 2017 の Python: データベース内の機械学習の強化](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="whats-new-in-sql-server-2017"></a>SQL Server 2017 の新機能

SQL Server でマシン学習サーバーは、構築および R または Python で machine learning ソリューションを配置するための包括的なサポートを提供します。 このリリースの要点を次に示します。

### <a name="whats-new-in-cumulative-update-3-for-sql-server-2017"></a>SQL Server 2017 の累積更新プログラム 3 の新機能

このリリースには、Python と R コンポーネントの更新プログラムが含まれています。 

+ Python モデルでのシリアル化 revoscalepy、rx_serialize_model 関数を使用してサポートが追加されました

### <a name="in-database-python-integration"></a>データベース内の Python の統合

Python ストアド プロシージャ、またはを実行する計算コンテキストとして、SQL Server コンピューターを使用してリモートで Python を実行します。 この統合は、SQL Server の機能を使用するには、Python の開発者やデータ サイエンティストの膨大なコミュニティの新しい手法が表示されます。

SQL Server の開発者にアクセスする広範な Python ライブラリ scikit などの一般的なフレームワークを含む、オープン ソース エコシステムから-TensorFlow、Caffe、および Theano/Keras を説明します。 Microsoft からなどの技術革新を試してみてくださいと**revoscalepy**と**microsoftml**!

データベース内のないあらゆる実行中の Python は機械学習、方法です。 これは、SQL では、Python と統合して、各言語の電源を使用して、高度な強力なソリューションを提供するその他の潜在的なアプリケーションの無数です。

+ **revoscalepy**

    このリリースでは最終バージョンの**revoscalepy**RevoScaleR 内のアルゴリズムに相当する Python を供給します。 線形とロジスティック回帰、デシジョン ツリー、ブースト ツリー、およびランダム フォレスト、すべて並列処理、およびリモート計算コンテキストで実行中の対応の Python モデルを作成することができます。

    詳細については、次を参照してください。 [revoscalepy は](python/what-is-revoscalepy.md)します。

+ Python のリモート計算コンテキスト

    このリリースでは、複数のデータ ソースとリモート計算コンテキストの使用をサポートします。 データ科学者や開発者は、データを参照するか、データを移動せずにモデルを構築する、リモートの SQL Server での Python コードを実行できます。 リモート計算コンテキストを使用する必要**revoscalepy**です。

+ Microsoft Machine Learning Server (スタンドアロン) での Python のサポート

    [!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)] Microsoft Machine Learning Server のスタンドアロン バージョンをインストールするオプションが含まれます。 Machine Learning のサーバーを使用するは、配布し、SQL Server を使用せずに R または Python コードをスケールします。

### <a name="linux-support"></a>Linux サポート

データベースを使用して R または Python での機械学習は SQL Server on Linux で現在サポートされていません。 以降のリリースのお知らせを参照してください。

ただし、Linux で行うことができます[ネイティブ スコアリング](sql-native-scoring.md)T-SQL で予測関数を使用します。 ネイティブのスコア付けするには、設定しなくても呼び出すことも、R ランタイム、非常に高速で、事前トレーニング済みモデルからスコア付けすることができます。 これは、Linux に SQL Server を使用するには非常に高速で、クライアント アプリケーションを提供する予測を生成することを意味します。

### <a name="new-algorithms"></a>新しいアルゴリズム

**MicrosoftML** R、Python の両方のパッケージには、最先端の機械学習アルゴリズムが含まれています、リモートのスケールまたはで実行できるデータの変換は、コンテキストを計算します。 深層ニューラル ネットワークのカスタマイズ可能な高速なデシジョン ツリーとデシジョン フォレスト、線形回帰、およびロジスティック回帰アルゴリズムが含まれます。 MicrosoftML パッケージ R、Python の両方のインターフェイスが付属します。

詳細については、次を参照してください。 [MicrosoftML 概要](using-the-microsoftml-package.md)と[for Python microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)です。

### <a name="operationalization"></a>操作運用

このリリースには、展開および機械学習タスクを配布するために、複数のオプションと機能が含まれています。

+ 配置し、T-SQL を使用して、マシン Python ソリューションを統合

    呼び出すことができる Python コードを使用して、T-SQL での Python の統合を意味`sp_execute_external_script`です。 このセキュリティで保護されたインフラストラクチャでは、Python モデルと単純なストアド プロシージャを使用して、アプリケーションから呼び出すことができるスクリプトのエンタープライズ レベルの展開できるようにします。 その他のパフォーマンスは、SQL から Python プロセスと MPI リングの並列化にデータをストリーミングでです。

+ **mrsdeploy** for Python

    **Mrsdeploy**にパッケージ化する[!INCLUDE[rsql-platform-md](../includes/rsql-platformnew-md.md)]と[!INCLUDE[rsql-platformnew-md](../includes/rsql-platformnew-md.md)]web サービスとしての Python モデルとスクリプトの展開をサポートします。 そのしくみの例は、次を参照してください。[発行 Python コードを使用すると](python/publish-consume-python-code.md)です。

+ パフォーマンス

    Microsoft はスコアリングのためのパフォーマンスの境界をプッシュされます。 ごとに 100万行を処理したデータベース内のスコアリングと 2 番目の R モデルを使用します。 このリリースでは、新機能で**リアルタイム スコアリング**と**ネイティブ スコアリング**の単一行のバッチ スコアリング パフォーマンス向上をサポートします。

### <a name="realtime-scoring-and-native-scoring"></a>リアルタイムのスコアリングと、ネイティブのスコアリング

リアルタイムのスコアリングは、最適化されたバイナリ形式で格納されているモデルを読み込むし、R ランタイムを呼び出さずに予測を生成するネイティブの C++ ライブラリに依存します。 これにより、スコア付けの操作をはるかに高速です。

さらに、このリリースの[!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]スコアリングを高速 Linux 上であっても、SQL Server の任意のエディションで実行できるネイティブ T-SQL 関数が含まれています。 関数には、R または追加の構成のインストールは不要です。 つまり、他の場所で、モデルのトレーニング、SQL Server に保存および R. を呼び出さないでスコアリングを実行し、この機能と呼ばれます_ネイティブ スコアリング_です。

  - のみ使用可能なはネイティブ スコアリング[!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]です。 Linux を含む、SQL Server の任意のエディションで実行できる T-SQL 関数を使用します。
 - リアルタイムのスコア付けがサポートされている[!INCLUDE[sscurrent-md](../includes/sscurrent-md.md)]、Microsoft Machine Learning のサーバーではします。 ストアド プロシージャを実行したり、リアルタイムの R コードのスコア付けを実行できます。
 - インスタンスが、最新のリリースにアップグレードした場合は SQL Server 2016 用に使用可能なリアルタイム スコアリングも[!INCLUDE[rsql-platform-md](../includes/rsql-platform-md.md)]します。

詳細については、次の記事を参照してください。

 + [リアルタイムのスコアリング](real-time-scoring.md)
 + [ネイティブのスコアリング](sql-native-scoring.md)
 + [リアルタイムのスコアリングまたはネイティブ スコアリングを実行する方法](r/how-to-do-realtime-scoring.md)

### <a name="upgrade-your-machine-learning-experience-and-get-pre-trained-models"></a>機械学習のエクスペリエンスをアップグレードし、事前トレーニング済みモデルの取得

SQL Server 2016 の R Services の以前のバージョンをインストールした場合重要度の最新のソフトウェア ライフ サイクル ポリシーを使用するようにサーバーを切り替えることによって、最新バージョンにアップグレードすることができますようになりました。 これにより、R の高速のリリース サイクルの活用し、すべての R コンポーネントを自動的にアップグレードできます。 詳細については、次を参照してください。 [Machine Learning のサーバーの新機能](https://docs.microsoft.com/machine-learning-server/whats-new-in-machine-learning-server)します。

インストーラーでは、バイナリ形式で事前トレーニング済みモデルのコレクションをインストールするオプションも提供します。 これらのモデルでは、ここで難しい可能性があるモデルをトレーニングする大規模なデータセットを検索する顧客の画像認識などのシナリオで機械学習をサポートします。 事前トレーニング済みモデルの 1 つをインストールした後は、時間とコストがこのような大規模で複雑なモデルのトレーニングに関係することがなく、独自のデータの予測使用することができます。

詳細については、次を参照してください[事前トレーニング済みモデルを SQL Server のインストール。](r/install-pretrained-models-sql-server.md)

### <a name="package-management"></a>パッケージの管理

このリリースには、SQL server パッケージ管理の多くの機能強化が含まれています。 たとえば、次のオブジェクトにアクセスできます。

- DBA は、パッケージの管理し、パッケージをインストールするアクセス許可を割り当てるためのデータベース ロール
- R を知らなくてもパッケージの管理の Dba を支援する、T-SQL で、外部ライブラリの作成ステートメント
- インストールするための R 関数の豊富なセットは、削除、または、ユーザーが所有するパッケージを一覧表示

詳細については、次を参照してください。[パッケージの管理](r/r-package-management-for-sql-server-r-services.md)です。

### <a name="get-started"></a>概要します。

+ [SQL Server の Machine Learning のサービスでの Python の設定します。](../advanced-analytics/python/setup-python-machine-learning-services.md)

+ [SQL Server の Machine Learning のサービスで R を設定します。](r/set-up-sql-server-r-services-in-database.md)

+ [Machine learning のチュートリアルおよびサンプル](tutorials/machine-learning-services-tutorials.md)
