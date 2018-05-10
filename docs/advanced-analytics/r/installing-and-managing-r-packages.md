---
title: 既定の SQL Server R と SQL Server の Machine Learning での R、Python のパッケージ ライブラリ |Microsoft ドキュメント
description: SQL Server R Services、R サーバー マシン ラーニング Services (In-database)、およびマシン ラーニング Server (スタンドアロン) によってインストールされた R、Python のパッケージ
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee2c8124cf3487ca300c0b08ea113c8e66b114f4
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="default-r-and-python-packages-in-sql-server"></a>SQL Server で既定の R、Python のパッケージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、パッケージのライブラリ、場所、および SQL Server と共にインストールされている R、Python のパッケージのバージョンについて説明します。 

## <a name="using-the-default-instance-library"></a>既定のインスタンスのライブラリを使用します。

機械学習と SQL Server をインストールするときにインストールする言語ごとに、インスタンス レベルで 1 つのパッケージ ライブラリが作成されます。 

すべてのスクリプトやコードを実行での SQL Server データベースには、インスタンスのライブラリから関数を読み込む必要があります。 SQL Server は、その他のライブラリにインストールされているパッケージにアクセスできません。 これはリモート クライアントにも適用されます。 リモート クライアントからサーバーに接続する、ときに、サーバーのコンピューティング コンテキストで実行する R または Python コードはのみインスタンス ライブラリにインストールされているパッケージを使用できます。

サーバー資産を保護するのには、既定のインスタンスのライブラリは、SQL Server に登録され、コンピューターの管理者によってのみ変更できますをセキュリティで保護されたフォルダーにインストールされます。 コンピューターの所有者でない場合は、このライブラリにパッケージをインストールする管理者から権限を取得する必要があります。 

コンピューターを所有している場合でも、パッケージをインスタンスのライブラリに追加する前に、特定の R または Python パッケージをサーバー環境での有用性を検討してください。 パッケージ ファイルと、必要な複数のバージョンのサイズなどの要因をできるだけでなく、パッケージでのネットワークまたはインターネットの必要かどうかを考慮アクセスします。

### <a name="in-database-engine-instance-file-paths"></a>データベース エンジン インスタンスのファイル パス

次の表は、R、Python のバージョンとデータベースのファイルの場所にエンジンのインスタンスの組み合わせを示します。 

|バージョン | [インスタンス名]|既定のパス|
|--------|--------------|------------|
| SQL Server 2016 |既定のインスタンス (default instance)| C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\R_SERVICES\library|
| SQL Server 2016 |名前付きインスタンス (named instance) | C:\Program files \microsoft SQL Server\MSSQL13 < instance_name > \R_SERVICES\library。|
| R と SQL Server 2017|既定のインスタンス (default instance) | C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\R_SERVICES\library |
| R と SQL Server 2017|名前付きインスタンス (named instance)| C:\Program files \microsoft SQL Server\MSSQL14 です。MyNamedInstance\R_SERVICES\library |
| Python の SQL Server 2017 |既定のインスタンス (default instance) | C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\library |
| Python の SQL Server 2017|名前付きインスタンス (named instance)| C:\Program files \microsoft SQL Server\MSSQL14 < instance_name > \PYTHON_SERVICES\library。 |

### <a name="standalone-server-file-paths"></a>スタンドアロン サーバーのファイル パス 

次の表は、SQL Server 2016 R Server (スタンドアロン) または SQL Server 2017 Machine Learning サーバー (スタンドアロン) サーバーがインストールされているときに、バイナリの既定のパスを一覧表示します。 

|バージョン| インストール|既定のパス|
|------|------|------|
| SQL Server 2016|R Server (スタンドアロン)| C:\Program files \microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning の R のサーバー |C:\Program files \microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Python でのサーバー |C:\Program files \microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Microsoft R Server のスタンドアロン インストール可能性があると同様のサブフォルダー名とファイルを持つ他のフォルダーを検索する場合または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/)です。 これらのサーバー製品では、インストーラーが異なると (つまり C:\Program Files\Microsoft\R Server\R_SERVER または C:\Program Files\Microsoft\ML SERVER\R_SERVER) のパスがあります。 詳細については、次を参照してください。 [Machine Learning Server for Windows のインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)または[Windows 用の R Server 9.1 のインストール](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)です。

## <a name="what-is-included-in-a-default-installation"></a>既定のインストールに含まれるもの

このセクションでは、既定のインストールに含まれている R、Python の機能をまとめたものです。

### <a name="r-components"></a>R コンポーネント

コンポーネントには、オープン ソース R としての Microsoft の分布が含まれます。 [Microsoft R Open](https://mran.microsoft.com/open)です。 ベースの R パッケージなどのコア機能**stats**と**ユーティリティ**です。 実行することができます`installed.packages(priority = "base")`パッケージ一覧を返します。 R の基本インストールには、多数のサンプル データセット、および RGui (軽量の対話型エディター) および RTerm (R コマンド プロンプト) などの標準の R ツールも含まれています。

Microsoft のパッケージを含める[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)のストリーミング、リモート計算コンテキストの並列実行 rx 関数のデータのインポートおよび変換、モデリング、視覚エフェクト、および分析します。 [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) R. で、モデリング、機械学習の追加その他のパッケージを含める[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) R での MDX ステートメントを記述するためと[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)ストアド プロシージャに R スクリプトを含めるためです。


|リリース             | R のバージョン       | Microsoft パッケージ    |
|--------------------|-----------------|-----------------------|
| SQL Server 2016 R サービス | 3.2.2   | RevoScaleR、sqlrutil  |
| SQL Server 2017 Machine Learning サービス| 3.4.3 | RevoScaleR、MicrosoftML、olapR、sqlrutil|

最新のライフ サイクルのサポート ポリシーにバインドして、パッケージと事前インストールされているモデルを SQL Server 2016 の R Services を追加できます。 バインディングは、サービス モデルを変更します。 既定では、最初のインストール後に R パッケージは更新サービス パックおよび累積更新プログラムをします。 追加のパッケージと R のコア コンポーネントの完全バージョンのアップグレードは、製品のアップグレード (SQL Server 2017 する SQL Server 2016) からを介してのみ可能ですか、R をバインドすることによって Microsoft Machine Learning のサーバーにサポートします。 詳細については、次を参照してください。 [SQL Server で R のアップグレードと Python コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="python-components"></a>Python コンポーネント

SQL Server 2017 は、Python コンポーネントを追加します。 Python 言語オプションを選択すると、Anaconda ディストリビューションがインストールされます。 Python コード ライブラリ、だけでなく、標準インストールには、サンプル データ、単体テスト、およびサンプル スクリプトが含まれています。 

Microsoft のパッケージを含める[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) Python と同等に RevoScaleR、ストリームでは、並列のデータのインポートおよび変換、モデリング、視覚エフェクト、および分析の rx 関数を実行します。 別の Python パッケージが[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)トレーニングと変換、スコアリング、テキストおよびイメージの分析、および既存のデータから値を派生させるため特徴を抽出します。

SQL Server 2017 Machine Learning は、R、Python のサポートの両方に最初のリリースです。

|リリース             | Anaconda バージョン| Microsoft パッケージ    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning サービス  | Python 3.5 経由で 4.2 | revoscalepy、microsoftml |

最初のインストール後 Python パッケージは、サービス パックおよび累積更新プログラムを通じて更新されますが、フル バージョンのアップグレードは、Microsoft Machine Learning のサーバーに Python サポートをバインドしてのみ可能です。 詳細については、次を参照してください。 [SQL Server で R のアップグレードと Python コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="administrative-permissions-for-package-installation"></a>パッケージのインストールに対する管理権限

パッケージのインストールに必要なアクセス許可は、SQL Server 2016 および SQL Server 2017 間で変更されました。

+ SQL Server 2016 では、管理アクセス権は新しい R パッケージのインストールに必要です。
+ SQL Server 2017、パッケージを管理者として R と、Python の両方のインストールを続行できがある可能性が最も簡単な方法です。 

    DDL ステートメント、外部ライブラリの作成には、R ツールを使用せずにパッケージをインストールするデータベース管理者ができます。 

    Machine Learning のサーバーにパッケージの管理機能を使用する場合は、データベース レベルでの R パッケージをインストールする RevoScaleR を使用することができます。 データベース管理者は、機能を有効にし、データベースごとに独自のパッケージをインストールする機能をユーザーに付与する必要があります。 詳細については、次を参照してください。 [Ddl を使用してパッケージの管理を有効にする](r-package-how-to-enable-or-disable.md)です。

### <a name="user-libraries-are-not-supported"></a>ユーザーのライブラリがサポートされていません

インストールできないユーザーのパッケージを安全な場所に多くの場合は、ユーザー ライブラリにパッケージをインストールする手段です。 ただし、SQL Server 環境でこれができません。 サーバーで、ファイル システム アクセスが制限されている通常、外部スクリプトの実行時 SQL Server で実行されるがアクセスできる既定のインスタンスの外部にインストール パッケージではない場合でも、サーバー上のユーザー ドキュメント フォルダーにある場合の管理者権限とアクセスは、ライブラリです。 ただし、回避策が可能です。 ユーザーのライブラリに関連する問題を解決する方法のヒントについては、次を参照してください。 [R ユーザーのライブラリの回避策](packages-installed-in-user-libraries.md)です。

## <a name="next-steps"></a>次の手順

+ [パッケージ情報を取得します。](determine-which-packages-are-installed-on-sql-server.md)
+ [新しい R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージをインストールします。](../python/install-additional-python-packages-on-sql-server.md)
+ [リモートの R パッケージの管理を有効にします。](r-package-how-to-enable-or-disable.md)
+ [R パッケージの管理の RevoScaleR 関数](use-revoscaler-to-manage-r-packages.md)
+ [R パッケージの同期](package-install-uninstall-and-sync.md)
+ [ローカルの R パッケージ リポジトリの miniCRAN](create-a-local-package-repository-using-minicran.md)
