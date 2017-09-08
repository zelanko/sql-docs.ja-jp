---
title: "アーキテクチャと概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
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
ms.openlocfilehash: 7549b59d4edc00dd620deeb515f6cd7143a62db7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---

# <a name="architecture-and-overview-of-machine-learning-services"></a>アーキテクチャと Machine Learning のサービスの概要

このトピックでは、SQL Server での Python と R スクリプトの実行をサポートする機能拡張フレームワークの目標について説明します。

これらの目標を達成するアーキテクチャを設計する方法の概要についても用意されています。 R、Python のサポートと SQL Server、および統合のメリットで実行される方法です。

全体的に見て、拡張性フレームワークは若干の違いと呼ばれる起動ツールの詳細、構成オプションなどの R、Python、ほぼ同じです。 特定の言語の実装の詳細については、これらのトピックを参照してください。

- [SQL Server R Services のアーキテクチャの概要](r/architecture-overview-sql-server-r.md)
- [SQL Server での Python のアーキテクチャの概要](python/architecture-overview-sql-server-python.md)


## <a name="background"></a>背景情報

SQL Server 2016 では、SQL Server を使用して R スクリプトの実行をサポートするために、データベース エンジンに数多くの変更点が導入されました。 SQL Server の 2017 では、Python 言語のサポートを追加するこの基になるインフラストラクチャが強化されました。

Extensibility framework の目標は、SQL Server と R、Python、両方をデータ サイエンス ソリューションが、実稼働環境に移動したときに発生する競合を減らすために、および可能性のあるデータを保護するなどデータ サイエンスの言語の優れたインターフェイスを作成することでした。データ サイエンス開発プロセス中に公開されます。

SQL Server によって管理されているセキュリティで保護されたフレームワーク内で信頼できるスクリプト言語を実行することによって、データベース開発者は、エンタープライズ データを使用するデータ サイエンティストしながらセキュリティを維持できます。

  ![SQL Server との統合の目標](media/ml-service-value-add.png "Machine Learning サービス値の追加")

- R、または Python の現在のユーザーは、そのコードを移植して比較的重要でない変更での SQL Server で実行できるようにする必要があります。
- SQL Server のデータのセキュリティ モデルは、外部のスクリプト言語で使用されるデータまで拡張されます。 つまり、あらゆるデータを SQL クエリでは、そのユーザーがアクセスできませんでしたできません R または Python スクリプトを実行しているユーザーが必要があります。
- データベース管理者は、外部スクリプトで使用されるリソースを管理、ユーザーの管理し管理、および外部コード ライブラリを監視することにする必要があります。
- システムでは、セキュリティとパフォーマンスが向上を提供する microsoft R と、Python を使用して独自のコンポーネントの開発のオープン ソース ディストリビューションに完全に基づくソリューションをサポートする必要があります。

## <a name="architecture-core-concepts"></a>アーキテクチャの主要な概念

これらの目標を満たすためには、SQL Server 2016 の R Services および SQL Server の 2017 マシン ラーニング Services は R、Python のアーキテクチャは、これらの主要な概念に基づいています。

+ **マルチ プロセスのアーキテクチャ**

  R と Python は、多機能かつ熱心なコミュニティのサポートにオープン ソース言語がします。 そのため、これがオープン ソース R、Python と完全な相互運用を維持するために重要です。

  R、Python のオープン ソース ディストリビューションでは、license については、SQL Server と共にインストールされ、独立して機能から SQL Server が必要な場合です。

   さらに、Microsoft は、データの翻訳、圧縮、および最適化をサポートする各言語を対象としたなど、SQL Server との統合を提供する独自のライブラリのセットを提供します。

+ **セキュリティ**

   強力なセキュリティは、資格情報の処理を適切にセキュリティで保護されたデータ保護、および外部スクリプトを管理する SQL Server 信頼スタート パッドの使用の SQL Server への依存統合 Windows 認証と SQL ログインのパスワード ベースの両方のサポート実行とスクリプトで使用されるセキュリティで保護されたデータ。

+ **スケーラビリティとパフォーマンス**

  SQL Server との統合は、企業内の R、Python の有用性を向上させるためにキーです。 ストアド プロシージャの呼び出しで任意の R または Python スクリプトを実行できるし、結果の表形式の結果として、SQL Server に直接生成または SQL クエリを送信し、結果を処理できるすべてのアプリケーションからの機械学習を使用するは容易になります。

  パフォーマンスの最適化は、プラットフォームの 2 つの均等に強力な側面に依存していますリソース ガバナンスおよび並列実行する SQL Server を使用して処理および分散コンピューティング アルゴリズムによって提供される**RevoScaleR**と**。revoscalepy**です。


## <a name="solution-development-and-deployment"></a>ソリューションの開発と展開

これらの機能拡張プラットフォームのコア目標、に加えて SQL Server の machine learning サービスは、データベース エンジンとこれらの利点と、BI スタックの強力な統合を実現するよう設計されています。

+ 従来の監視ツールによるパフォーマンスとリソースの管理
+ 容易な BI スイートまたは SQL クエリの結果を利用できる任意のアプリケーションによって Python と R のデータの使用します。
+ Machine learning のソリューションの開発をエンタープライズの下位程度バリア

実際にそのしくみを見てみましょう。

  ![ML ソリューションの開発プロセス](media/ml-solution-development-process.png "開発 Machine Learning のサービスを使用して展開し、")

1. データは、コンプライアンスの境界内に保持し、データの使用を管理および SQL Server によって監視できます。 その一方で、DBA は、パッケージをインストールまたはサーバーでスクリプトを実行できるユーザーを完全に制御します。 必要な場合、DBA もデータ サイエンティストまたは管理者に、データベース レベルの権限を委任できます。
2. データ サイエンティストは、ビルドし、その優先 R または Python 環境で、サーバーから切断されているソリューションをテストできます。
3. SQL 開発者は、Management Studio または Visual Studio などの使い慣れたツールを使用して、R または Python コードを SQL Server と統合します。 緊密な統合は、経験豊富な開発者が各タスクを最適化するために最適なツールを選択できますを意味します。 たとえば、他のユーザーが一部のエンジニア リング タスクの機能および R SQL を使用する可能性があります。 高度なテキスト分析を実行する Integration Services タスクで Python スクリプトを埋め込む場合があります。
4. テストと展開の準備完了ソリューションは、パフォーマンス向上のため、列ストア インデックスなど、SQL Server のテクノロジを使用して最適化できます。 新しい機能を使用すると、バッチ並列パーティションのデータ セットに多数の小さいモデルをトレーニングまたは数百万の機械学習タスク用に最適化されたネイティブの SQL コードを使用して行をスコア付けできます。
5. 準備ができてを持ち上げますか。 ストアド プロシージャを使用して、予測の解決策、BI スタックまたは外部アプリケーションを簡単に公開できます。

## <a name="related-products"></a>関連する製品

わからない場合は、どの機械学習ソリューションはニーズを満たすか。 埋め込みの分析機能を SQL Server 2016 および SQL Server 2017、に加えては、マイクロソフトは、次の機械学習のプラットフォームとサービスを提供します。

+ [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver)

  開発、配布、および machine learning のジョブを管理するための複数のプラットフォーム環境
+ [データ サイエンス仮想マシン](https://docs.microsoft.com/azure/machine-learning/machine-learning-data-science-virtual-machine-overview)

  すべてのツールの machine learning、プレインストールされている必要があります。 使用 Jupyter ノートブック、Python や r です。
  
  新しいを再試行してください[Windows 2016 preview エディション](http://aka.ms/dsvm/win2016)、CNTK mxNet と Windows コンテナーのサポートなどの一般的な深層学習フレームワークの GPU のバージョンが含まれます。
+ [Azure の認知サービス](https://azure.microsoft.com/services/cognitive-services/)

  さまざまな自然言語が、ビデオ、顔認識のインデックスを含む、アプリケーションに AI および ML を追加するためのクラウド サービスの感情の検出、テキスト分析では、コンピューターの平行移動、およびそれほど多くより
+ [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/)

  自動化し、web サービス、および PowerShell 経由でアプリケーションを統合する機能と組み合わせると、マシン学習ワークフローを設計するためのクラウド ベースのドラッグ アンド ドロップ インターフェイス

## <a name="see-also"></a>参照

[R Server のスタンドアロン](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone)

