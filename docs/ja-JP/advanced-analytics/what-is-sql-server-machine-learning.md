---
title: SQL Server マシン学習サービスとは | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d52196007b5a1de4753e9846e4057295113baa7b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="what-is-sql-server-machine-learning-services"></a>SQL Server マシン学習サービスとは
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server の Machine Learning のサービスは、埋め込み、予測分析およびデータ サイエンス エンジンのストアド プロシージャとして、R、または Python のステートメントを含む T-SQL スクリプトまたは R または Python コードを含むとして、SQL Server データベース内 R、Python コードを実行できます。T-SQL です。 

Machine Learning のサービスのキーの価値提案は、スケール、および計算して処理をデータの保存場所を聞くことで高度な分析を提供する、独自のパッケージの機能全体にデータをプルする必要がなくなるため、ネットワークです。

SQL Server で machine learning の機能を使用するための 2 つのオプションがあります。 

+ [**SQL Server マシン ラーニング Services (In-database)** ](r/sql-server-r-services.md)データベース エンジン インスタンス、データベース エンジンと、計算エンジンが完全に統合されている範囲内で動作します。 ほとんどのインストールは、このオプションです。
+ [**SQL Server マシン ラーニング サーバー (スタンドアロン)** ](r/r-server-standalone.md)は、マシン学習の Windows サーバー、データベース エンジンとは無関係に実行しています。 SQL Server セットアップを使用して、サーバーをインストールする機能はインスタンス対応はありません。 これは機能的には、非 SQL Server に相当[Microsoft Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

## <a name="r-and-python-packages"></a>R、Python パッケージ

各言語のサポートは Microsoft の独自のパッケージを作成およびデータ、および基になるシステム リソースを使用して並列処理をスコア付けのさまざまな種類のモデルを学習するためです。

独自のパッケージが構築されるためのオープン ソース R、Python ディストリビューション、スクリプトやコードが SQL Server で実行することができますも基本と関数を呼び出す SQL Server で提供される言語のバージョンと互換性のあるサード パーティのパッケージを使用して (Python 3.5 と最新バージョンの R、現在 3.3.3)。

| R  | Python | Description |
|-----------|----------------|-------------|
| [RevoScaleR](r/revoscaler-overview.md) | [revoscalepy](python/what-is-revoscalepy.md)   | これらのライブラリ内の関数は、最も広く使用されている間です。 これらのライブラリでは、データ変換と操作、統計の要約、ビジュアル化、およびモデリングと分析の多くの形式が見つかりました。 さらに、これらのライブラリ内の関数に自動的にワークロードを分散並列調整および計算エンジンによって管理されるデータのチャンクで作業を行うことで、処理の使用可能なコアです。 |
| [MicrosoftML](using-the-microsoftml-package.md) | [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 業界をリードするマシンがイメージの特性付け、分類問題、およびその他のアルゴリズムを学習します。 |
| [olapR](r/how-to-create-mdx-queries-using-olapr.md) | なし | ビルドまたは R スクリプトで MDX クエリを実行します。
| [sqlRUtils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) | なし | T-SQL に R スクリプトを配置するための関数はストアド プロシージャをデータベースとストアド プロシージャを登録して、R 開発環境からストアド プロシージャを実行しています。
| [mrsdeploy](operationalization-with-mrsdeploy.md) | なし | など、Machine Learning のサーバーの SQL 以外のインストールで使用される、主に、 [(スタンドアロン) バージョン](r/r-server-standalone.md)します。 展開と web サービスをホストする専用の web スケール アウト トポロジを構築およびコンピューティング ノード、診断、および複数の実行、ローカルおよびリモート セッションの間で切り替えるには、このパッケージを使用します。 (In-database) のインストールでは、クライアントの容量でこのパッケージを使用して: たとえば、リモート サーバー上の web サービスにアクセスする専用の Machine Learning Services ワークロードだけを実行します。 |

カスタム R、Python コードの移植性は、パッケージを配布して複数の製品に組み込まれている通訳扱われます。 SQL Server に含まれている同じパッケージが他のいくつかの Microsoft 製品やサービスをなどと呼ばれる非 SQL バージョンで使用できるも[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/)です。 空きクライアント含む、R、Python インタープリターにはが含まれます[Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)と[Python ライブラリ](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)です。

パッケージおよびインタープリターはいくつかの使用も[Azure の仮想マシン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux)、Azure Machine Learning とような Azure サービス[HDInsight](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-on-azure-hdinsight)です。 


## <a name="use-cases"></a>ユース ケース

**データベース内の分析**

開発者およびアナリスト多くの場合、ローカルの SQL Server インスタンス上で実行されるコードがあります。 場合などがある SQL Server および IDE [R での Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/)または[Python の Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio)同じコンピューターにすることができますを構築、トレーニング、およびモデルのいずれかの言語でローカルにテストします。 ローカル アクセスがパッケージの管理を簡略化します。 管理者には、その役割の組み込みの権限を使用してその他のサードパーティ製パッケージを読み込むことができます。

データベース内の分析のための最も一般的な方法は、使用する[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) R または Python スクリプトを実行します。 表示されているチュートリアル[次のステップ](#next-steps)作業を開始します。

**クライアントとサーバーの構成**

IDE のある任意のクライアント ワークステーションからインストール[Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)または[Python ライブラリ](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)、実行をプッシュするコードを記述および (と呼ばれる、*リモート計算コンテキスト*)データおよびリモートの SQL Server に操作します。 

同様に、Developer edition を使用している場合は、同じライブラリとインタープリターを使用して、クライアント ワークステーションでソリューションを構築し、実稼働コード上の SQL Server マシン ラーニング Services (In-database) を展開します。 

## <a name="version-history"></a>バージョン履歴

SQL Server 2017 Machine Learning サービスとは、python に強化され、SQL Server 2016 R Services の次世代です。 次の表は、現在のリリースに至るまでのすべてのバージョンの完全な一覧を示します。 

| [製品名] | エンジンのバージョン | リリース日 |
|--------------|---------|--------------|
| SQL Server 2017 Machine Learning Services (In-database) | R Server 9.2.1 <br/> Python Server 9.2 | 2017 年 10 月 |
| SQL Server 2017 Machine Learning サーバー (スタンドアロン) | R Server 9.2.1 <br/> Python Server 9.2 | 2017 年 10 月 |
| SQL Server 2016 R Services (In-database) | R Server 9.1  | 2017 年 7 月  |
| SQL Server 2016 R Server (スタンドアロン)  |  R Server 9.1 | 2017 年 7 月 |



## <a name="documentation-for-each-version"></a>各バージョン用のドキュメント

SQL Server のドキュメントの最近のリリースは、バージョンに依存しません。 SQL Server マシン ラーニング services、Python はのみ使用できます 2017年以降では、R のサポートは、すべてのバージョンで中にします。 明記しない限り、R ドキュメント 2016 と 2017 の両方のバージョンに適用されますを想定することができます。


## <a name="related-machine-learning-products"></a>関連の機械学習の製品

 +  [Azure の仮想マシンのプロビジョニング](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
  
  Azure marketplace には、Machine Learning のサーバーまたは R サーバーを含む複数の仮想マシン イメージが含まれています。 予測モデルの開発と配置を取得する最も簡単な方法は、Microsoft Azure でバーチャル マシンを作成します。 イメージを容易にアプリケーション内での分析を埋め込むとバックエンド システムと統合するスケーリングと、既に構成されている共有の機能が付属します。

+ [Data Science Virtual Machine](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)

  データ サイエンス仮想マシンの最新バージョンには、マシン学習サーバー、SQL Server が含まれています。 plus 機械学習に最も一般的なツールの配列のすべてをプレインストールし、テストします。 作成 Jupyter ノートブック、ジュリアは、ソリューションを開発および MXNet、CNTK、TensorFlow など深層学習の GPU が有効なライブラリを使用します。

<a name="next-steps"></a>

## <a name="next-steps"></a>次の手順

**手順 1:** をインストールし、ソフトウェアを構成します。 

+ [SQL Server 2017 Machine Learning Services (In-database) のインストールします。](install/sql-machine-learning-services-windows-install.md)

**手順 2:** これらのチュートリアルのいずれかを使用してコードで作業を開始します。

+ [チュートリアル: T-SQL で Python を実行します。](tutorials/run-python-using-t-sql.md)
+ [チュートリアル: T-SQL で R を実行します。](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

**手順 3:** お気に入りの R、Python パッケージを追加し、Microsoft によって提供されたパッケージと共に使用します。

+ [SQL Server の R パッケージの管理](r/r-package-management-for-sql-server-r-services.md)
