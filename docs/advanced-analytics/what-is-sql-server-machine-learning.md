---
title: R 言語と Python 機能の統合 - SQL Server Machine Learning サービス
description: R 言語とデータ サイエンスと統計モデリング、機械学習モデル、予測分析、データの視覚化などのリレーショナル データとの統合、SQL Server での Python 機能。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2018
ms.topic: overview
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: cf7d8a7cddcfbe0d47d4808f82abc0a47efade2c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512456"
---
# <a name="machine-learning-services-r-python-in-sql-server-2017"></a>SQL Server 2017 での machine Learning サービス (R、Python)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 Machine Learning Services とは、データベース エンジン インスタンス、SQL Server で R と Python のコードを実行するためのアドオンです。 この機能が含まれています[Microsoft R と Python のパッケージ](#components)高パフォーマンスの予測分析と機械学習します。 コア エンジンのプロセスから分離されたが、R または Python のステートメントを含む T-SQL スクリプトまたは R または Python のコードを含む T-SQL ストアド プロシージャとしてのリレーショナル データを完全に使用可能な機能拡張フレームワークでコードが実行されます。 

使用していた場合[SQL Server 2016 R Services](r/sql-server-r-services.md)、SQL Server 2017 での Machine Learning サービスは、基本の R で RevoScaleR の MicrosoftML の更新バージョンでの R のサポートの次世代および他のライブラリは、2016年で導入されました。 

Azure SQL Database で[(R) を使用した Machine Learning サービス](https://docs.microsoft.com/azure/sql-database/sql-database-machine-learning-services-overview)は現在パブリック プレビュー段階です。

## <a name="bring-compute-power-to-the-data"></a>データにコンピューティング能力をもたらす

Machine Learning サービスのキーの価値提案は、スケール、および計算と、データが存在する処理を統合する機能での高度な分析を提供する、企業の R と Python パッケージの電源間でデータをプルする必要はありませんネットワーク。 これは、複数の利点を提供します。

+ データのセキュリティ。 R および Python のデータ ソースに近い実行は無駄や安全でないデータ移動を回避します。
+ 速さ。 データベースは、セットベースの操作用に最適化されています。 インメモリ テーブルなどのデータベースの最新技術の概要と集計、処理が非常を行い、データ サイエンスを補完します。
+ 展開との統合が容易。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] その他の多くのデータ管理タスクやアプリケーションの操作のサーバーの全体のポイントです。 レポート ウェアハウスまたはデータベースに存在するデータを使用すると、機械学習ソリューションによって使用されるデータが一貫して最新の状態であることを確認します。 
+ クラウドとオンプレミス間の効率。 R または Python のセッションでデータの処理ではなくなどのエンタープライズ データ パイプラインに依存できます[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]と Azure Data Factory。 Power BI や [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用して、結果や分析を簡単にレポートできます。

さまざまなデータ処理や分析タスクで SQL と R を正しく組み合わて使用することで、データ サイエンティストと開発者の両方の生産性がさらに向上します。

<a name="components"></a>

## <a name="components"></a>コンポーネント

SQL Server 2017 では、R と Python がサポートされています。 次の表では、コンポーネントについて説明します。

| コンポーネント | 説明 |
|-----------|-------------|
| SQL Server スタート パッド サービス | 外部の R と Python のランタイムと、データベース エンジンのインスタンス間の通信を管理するサービス。 |
| R パッケージ | [**RevoScaleR** ](r/ref-r-revoscaler.md)はこのライブラリでスケーラブルな R. 関数が最も広く使用されている間は、プライマリ ライブラリ。 データ変換と操作、統計の概要作成、視覚化、およびモデリングと分析の多くの形式は、これらのライブラリで表示されます。 さらに、これらのライブラリ内の関数は、並列処理、調整され、計算エンジンによって管理されるデータのチャンク上で動作する機能の使用可能なコア間でワークロードを自動的に配布します。  <br/>[**MicrosoftML (R)** ](r/ref-r-microsoftml.md)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。 <br/>[**sqlRUtils** ](r/ref-r-sqlrutils.md) T-SQL ストアド プロシージャに R スクリプトを配置すること、データベースでストアド プロシージャを登録すると、R 開発環境からストアド プロシージャを実行しているヘルパー関数を提供します。<br/>[**olapR** ](r/ref-r-olapr.md)の構築または MDX クエリを実行する R スクリプトでは、します。|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open)は r です Microsoft のオープン ソース ディストリビューションには。パッケージおよびインタープリターが含まれます。 常にセットアップによってインストールされている MRO のバージョンを使用します。 |
| R ツール | R コンソール ウィンドウとコマンド プロンプトは、R のディストリビューションで標準的なツールです。  |
| R のサンプルとスクリプト |  オープン ソースの R と RevoScaleR パッケージには、作成して事前インストールされているデータを使用してスクリプトを実行できるように、組み込みのデータ セットが含まれます。 |
| Python パッケージ | [**revoscalepy** ](python/ref-py-revoscalepy.md)データ操作、変換、視覚エフェクトと分析のための関数での Python のスケーラブルなは、プライマリ ライブラリ。 <br/>[**microsoftml (Python)** ](python/ref-py-microsoftml.md)テキスト分析、画像分析、およびセンチメント分析のカスタム モデルを作成する機械学習アルゴリズムを追加します。  |
| Python ツール | 組み込みの Python のコマンド ライン ツールは、アドホック テストとタスクに適しています。  |
| Anaconda | Anaconda とは、Python と重要なパッケージのオープン ソース ディストリビューションです。 |
| Python のサンプルとスクリプト | R と Python には、組み込みのデータ セットとスクリプトが含まれています。  |
| R および Python で事前トレーニング済みモデル | 事前トレーニング済みモデルは特定のユース ケース用に作成し、microsoft データ サイエンスのエンジニア リング チームによって管理されます。 事前トレーニング済みモデルとして使用することができます-正、負のセンチメントをスコア付けで、テキストまたはイメージを提供する新しいデータの入力を使用して機能を検出します。 モデルでは、Machine Learning のサービスで実行しますが、SQL Server セットアップでインストールすることはできません。 詳細については、次を参照してください。[インストール事前トレーニング済みの機械学習では、SQL Server のモデル](install/sql-pretrained-models-install.md)します。 |

## <a name="using-sql-mls"></a>SQL MLS を使用します。

開発者およびアナリスト多くの場合、ローカルの SQL Server インスタンス上で実行されるコードがあります。 Machine Learning サービスを追加し、外部スクリプトの実行を有効にして、SQL Server のモダリティで R と Python のコードを実行することができますストアド プロシージャにスクリプトをラップする、モデルを格納する SQL Server テーブル、または T-SQL と R または Python 関数の組み合わせ。クエリ。

データのセキュリティ モデルの境界内にスクリプトの実行: リレーショナル データベースの権限は、スクリプト内のデータ アクセスの基礎です。 R または Python スクリプトを実行しているユーザーは、任意のデータを SQL クエリでは、そのユーザーにアクセスできませんでしたを使用する必要がありますできません。 標準的なデータベースの読み取りと書き込みのアクセス許可、および外部のスクリプトを実行する追加のアクセス許可必要があります。 モデルとリレーショナル データを記述するコードがラップ ストアド プロシージャ、またはバイナリ形式にシリアル化して、テーブルに格納または生のバイト ストリームをファイルにシリアル化する場合は、ディスクから読み込まれます。

データベース内分析の最も一般的なアプローチは、使用する[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、R または Python スクリプトを入力パラメーターとして渡します。

従来のクライアント サーバーのやり取りは別の方法です。 IDE のある任意のクライアント ワークステーションからインストールできます[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)または[Python ライブラリ](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)、実行をプッシュするコードを記述 (と呼ばれる、*リモート コンピューティングコンテキスト*) データとリモートの SQL Server を操作します。 

最後に、使用する場合、[スタンドアロン サーバー](r/r-server-standalone.md)と Developer edition では、同じライブラリとインタープリターを使用して、クライアント ワークステーションでソリューションを構築して SQL Server Machine Learning で運用環境のコードを配置することができます、Services (In-database)。 

## <a name="how-to-get-started"></a>開始する方法

### <a name="step-1-install-the-software"></a>手順 1:ソフトウェアをインストールします。

+ [SQL Server Machine Learning Services (In-database)](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>手順 2:開発ツールを構成します。

データ サイエンティスト通常 R または Python を使用、独自のラップトップ コンピューターや開発ワークステーションにデータを探索し、ビルド、適切な予測モデルを実現するまでは、予測モデルを調整します。 SQL server の in-database analytics では、このプロセスを変更する必要はありません。 インストールが完了したら、ローカルおよびリモートで、SQL Server で R または Python コードを実行します。

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **必要に応じて IDE を使用して**します。 任意の開発ツールには、R と Python ライブラリをリンクできます。 詳細については、次を参照してください。 [R tools セットアップ](r/set-up-a-data-science-client.md)と[Python ツールのセットアップ](python/setup-python-client-tools-sql.md)します。  

+ **リモートまたはローカルでの作業**します。 データ サイエンティストは、SQL Server に接続し、ローカルの分析のため、クライアントにデータを通常どおりさせます。 ただしより優れたソリューションは、使用する、 **RevoScaleR**または**revoscalepy** SQL Server コンピューターに計算をプッシュ Api にコストのかかる安全でないデータ移動を回避します。

+ **SQL Server ストアド プロシージャで R または Python スクリプトを埋め込む**します。 コードを完全に最適化するときは、不要なデータ移動を回避し、データ処理タスクを最適化するストアド プロシージャでラップします。

### <a name="step-3-write-your-first-script"></a>手順 3:最初のスクリプトを作成します。

T-SQL スクリプト内で R または Python 関数を呼び出します。

+ [R:R を使用してデータベース内分析について説明します](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [R:R を使用したエンド ツー エンド チュートリアル](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Python:T-SQL を使用して Python を実行します。](tutorials/run-python-using-t-sql.md)
+ [Python:Python を使用してデータベース内分析について説明します](tutorials/sqldev-in-database-python-for-sql-developers.md)

タスクの最適な言語を選択します。 R は、SQL を使用して実装するが困難な統計の計算に最適です。 データのセット ベース操作では、最大のパフォーマンスを実現するために SQL Server のパワーを活用します。 列にわたって非常に高速計算、メモリ内データベース エンジンを使用します。

### <a name="step-4-optimize-your-solution"></a>手順 4:ソリューションを最適化します。

モデルのエンタープライズ データを拡大縮小する準備ができたら、データ サイエンティストは多くの場合などのプロセスを最適化するために、データベース管理者または SQL の開発者で動作します。

+ 機能エンジニアリング
+ データの取り込みとデータ変換
+ ポイントの計算

これまでは、データ サイエンティストが R を使用して問題がある両方のパフォーマンスとスケール、特に大規模なデータセットを使用する場合。 共通ランタイムの実装はシングル スレッドし、ローカル コンピューターの使用可能なメモリに収まるデータ セットのみに対応できるためです。 SQL Server Machine Learning Services との統合は、多くのデータをパフォーマンスの向上のための複数の機能を提供します。

+ **RevoScaleR**:この R パッケージには、並列処理とスケールを提供する再設計された、最も一般的な R 関数のいくつかの実装が含まれています。 パッケージには、通常ははるかに大きなメモリと計算能力を持つ SQL Server コンピューターに計算をプッシュしてパフォーマンスとスケールをさらに向上させる機能も含まれています。

+ **revoscalepy**します。 この Python ライブラリが、リモート計算コンテキストなどの revoscaler の最も人気のある関数を実装し、分散処理をサポートする多くのアルゴリズム。

パフォーマンスの詳細については、この参照してください[パフォーマンスのケース スタディ](r/performance-case-study-r-services.md)と[R とデータの最適化](r/r-and-data-optimization-r-services.md)します。

### <a name="step-5-deploy-and-consume"></a>手順 5:デプロイし、使用

スクリプトまたはモデルが運用環境で使用できる状態と、データベース開発者を埋め込むことがコードまたはモデルをストアド プロシージャで保存した R または Python コードをアプリケーションから呼び出すことができるようにします。 格納して、SQL Server から R コードの実行が多くの利点: 便利な SQL Server のインターフェイスを使用して、不要なデータ移動を回避、データベースで実行されるすべての計算。

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **セキュリティで保護されたで拡張可能な**します。 SQL Server では、状態、データベース エンジンをセキュリティで保護された R と Python のセッションを分離する新しい拡張可能アーキテクチャを使用します。 コードでアクセスできるデータベースを指定することができますおよびスクリプトを実行できるユーザーを制御もあります。 サーバーの全体のパフォーマンスを損なうから大量の計算を防ぐために、実行時に割り当てられたリソースの量を制御できます。

+ **スケジュール設定と監査**します。 SQL Server の外部スクリプト ジョブの実行時に制御し、データ サイエンティストによって使用されるデータを監査できます。 ジョブと他の T-SQL ジョブまたはストアド プロシージャをスケジュールするのと同じように、外部の R または Python スクリプトを含むワークフローを作成をスケジュールすることもできます。

SQL Server で、リソース管理とセキュリティ機能の活用、展開プロセスにこれらのタスクが含まれます。

+ ストアド プロシージャで最適に実行できる関数にコードを変換します。
+ セキュリティを設定して、特定のタスクで使用されるパッケージのロックダウン
+ リソース ガバナンスが (Enterprise edition が必要) を有効にします。

詳細については、次を参照してください。 [R 用のリソース ガバナンス](r/resource-governance-for-r-services.md)と[SQL Server の R パッケージ管理](r/install-additional-r-packages-on-sql-server.md)します。

## <a name="version-history"></a>バージョン履歴

SQL Server 2017 Machine Learning Services とは、Python 拡張により、SQL Server 2016 R Services の次世代です。 次の表では、現在のリリースに至るまで、すべての製品バージョンの完全な一覧を示します。 

| [製品名] | エンジンのバージョン | リリース日 |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning サービス (データベース) | R Server 9.2.1 <br/> Python Server 9.2 | 2017 年 10 月 |
| SQL Server 2017 Machine Learning Server (スタンドアロン) | R Server 9.2.1 <br/> Python Server 9.2 | 2017 年 10 月 |
| SQL Server 2016 R Services (In-database) | R Server 9.1  | 2017 年 7 月  |
| SQL Server 2016 R Server (スタンドアロン)  |  R Server 9.1 | 2017 年 7 月 |

リリースでは、パッケージのバージョンのマップにバージョンを参照してください。[アップグレード R および Python コンポーネント](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md#version-map)します。

## <a name="portability-and-related-products"></a>移植性および関連製品

パッケージの配布と複数の製品に組み込まれているインタープリターで、カスタムの R と Python コードの移植性が対処されます。 その他のいくつかの Microsoft 製品やと呼ばれる非 SQL バージョンを含むサービスで使用できる SQL Server に含まれている同じパッケージも[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/)します。 

無料のクライアントを含む、R と Python インタープリターは[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)と[Python ライブラリ](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)。

Azure では、Microsoft の R と Python のパッケージおよびインタープリターも、Azure Machine Learning で使用できるなどの Azure サービスと[HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview)、および[Azure 仮想マシン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux)します。 [データ サイエンス仮想マシン](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)から複数のベンダーだけでなく、ライブラリのツールと Microsoft からのインタープリターを使用してフル装備の開発ワークステーションが含まれています。

## <a name="see-also"></a>関連項目

[SQL Server Machine Learning サービスをインストールします。](install/sql-machine-learning-services-windows-install.md)
