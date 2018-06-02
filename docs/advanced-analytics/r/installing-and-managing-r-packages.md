---
title: 既定の SQL Server R と SQL Server の Machine Learning での R、Python のパッケージ ライブラリ |Microsoft ドキュメント
description: SQL Server R Services、R サーバー マシン ラーニング Services (In-database)、およびマシン ラーニング Server (スタンドアロン) によってインストールされた R、Python のパッケージ
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9362d6e9dc98f80beabc301f43e755b205b40a10
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707290"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>SQL Server で既定の R、Python のパッケージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server と、パッケージのライブラリを検索する場所にインストールされている R、Python のパッケージが一覧表示します。  

## <a name="r-package-list-for-sql-server"></a>SQL Server の R パッケージの一覧

R パッケージがインストールされている[SQL Server 2016 の R Services](../install/sql-r-services-windows-install.md)と[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)セットアップ中に、R の機能を選択するとします。 

パッケージ         | 2016 | 2017 | 説明 |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | リモート計算コンテキスト、ストリーミング、データのインポートおよび変換、モデリング、視覚エフェクト、および分析の rx 関数の並列実行に使用されます。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |ストアド プロシージャで R スクリプトを含めるために使用します。 |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | R. の機械学習アルゴリズムを追加します。 | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | R. の MDX ステートメントを記述するために使用 |

MicrosoftML と olapR は、既定では SQL Server 2017 Machine Learning サービスで使用できます。 SQL Server 2016 の R Services のインスタンス上でこれらのパッケージを追加することができます、[コンポーネントのアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。 コンポーネントのアップグレードも取得するパッケージの新しいバージョン (など、RevoScaleR の新しいバージョンが、SQL Server 上のパッケージ管理の機能があります)。

## <a name="python-package-list-for-sql-server"></a>SQL Server 用 Python パッケージの一覧

Python パッケージは、インストールするときに SQL Server 2017 でのみ使用できます[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) Python 機能を選択します。

| パッケージ         | 2017    |  説明 |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | リモート計算コンテキスト、ストリーミング、データのインポートおよび変換、モデリング、視覚エフェクト、および分析の rx 関数の並列実行に使用されます。 |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Python の機械学習アルゴリズムを追加します。 |

## <a name="open-source-r-in-your-installation"></a>オープン ソース R のインストール

R のサポートにオープン ソースが含まれていますがベースの R 関数を呼び出すおよびその他のオープン ソースおよびサードパーティのパッケージをインストールできるようにします。 R 言語のサポートが含まれていますコア機能にはなど**基本**、 **stats**、**ユーティリティ**、およびその他。 R の基本インストールは、多数のサンプル データセット、および標準的な R などのツールも含まれます**RGui** (軽量の対話型エディター) および**RTerm** (R コマンド プロンプト)。 

インストールに含まれているオープン ソース R のディストリビューションが[Microsoft R を開きます (MRO)](https://mran.microsoft.com/open)です。 MRO 基本 r などその他のオープン ソース パッケージを含めることで値を追加する、 [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)です。

次の表は、SQL Server セットアップを使用して MRO によって提供される R のバージョンをまとめたものです。

|リリース             | R のバージョン       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 マシンがサービスの学習](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Web 上の新しいバージョンに SQL Server セットアップによってインストールされている R のバージョンを上書きする必要があります手動でことはありません。 Microsoft R パッケージが基づくは r です。 変更の特定のバージョンで、インストールが不安定になることです。

## <a name="open-source-python-in-your-installation"></a>インストールでオープン ソースの Python

SQL Server 2017 は、Python コンポーネントを追加します。 Python 言語オプションを選択すると、Anaconda 4.2 配布がインストールされます。 Python コード ライブラリ、だけでなく、標準インストールには、サンプル データ、単体テスト、およびサンプル スクリプトが含まれています。 

SQL Server 2017 Machine Learning は、R、Python のサポートの両方に最初のリリースです。

|リリース             | Anaconda バージョン| Microsoft パッケージ    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning サービス  | Python 3.5 経由で 4.2 | revoscalepy、microsoftml |

Web 上の新しいバージョンに SQL Server セットアップによってインストールされている Python のバージョンを上書きする必要があります手動でことはありません。 Microsoft Python パッケージは、Anaconda の特定のバージョンに基づいています。 インストールの変更が不安定になることです。

## <a name="component-upgrades"></a>コンポーネントのアップグレード

最初のインストール後、サービス パックおよび累積更新プログラムを R、Python のパッケージが更新されますが、フル バージョンのアップグレードのみで可能な*バインディング*を最新のライフ サイクルのサポート ポリシー。 バインディングは、サービス モデルを変更します。 既定では、最初のインストール後に R パッケージは更新サービス パックおよび累積更新プログラムをします。 追加のパッケージと R のコア コンポーネントの完全バージョンのアップグレードは、製品のアップグレード (SQL Server 2017 する SQL Server 2016) からを介してのみ可能ですか、R をバインドすることによって Microsoft Machine Learning のサーバーにサポートします。 詳細については、次を参照してください。 [SQL Server で R のアップグレードと Python コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="package-library-location"></a>ライブラリの場所にパッケージ

機械学習と SQL Server をインストールするときにインストールする言語ごとに、インスタンス レベルで 1 つのパッケージ ライブラリが作成されます。 Windows では、インスタンスのライブラリは、SQL Server に登録されているセキュリティで保護されたフォルダーです。

すべてのスクリプトやコードを実行での SQL Server データベースには、インスタンスのライブラリから関数を読み込む必要があります。 SQL Server は、その他のライブラリにインストールされているパッケージにアクセスできません。 これはリモート クライアントにも適用されます。 リモート クライアントからサーバーに接続する、ときに、サーバーのコンピューティング コンテキストで実行する R または Python コードはのみインスタンス ライブラリにインストールされているパッケージを使用できます。

サーバー資産を保護するのには、コンピューターの管理者によってのみ、既定のインスタンスのライブラリを変更できます。 コンピューターの所有者でない場合は、このライブラリにパッケージをインストールする管理者から権限を取得する必要があります。 

#### <a name="file-path-for-in-database-engine-instances"></a>データベース内のエンジンのインスタンスのファイル パス

次の表は、R、Python のバージョンとデータベースのファイルの場所にエンジンのインスタンスの組み合わせを示します。 MSSQL13 SQL Server 2016 を示しは R 専用です。 MSSQL14 は、SQL Server 2017 を示し、R、Python のフォルダーが存在します。 

ファイルのパスには、インスタンスの名前も含まれます。 SQL Server インストール[データベース エンジン インスタンス](../../database-engine/configure-windows/database-engine-instances-sql-server.md)またはユーザー定義の名前付きインスタンスとして既定のインスタンス (MSSQLSERVER) として。 SQL Server が名前付きインスタンスとしてインストールされている場合は、次のように追加されます。 その名前が表示されます:`MSSQL13.<instance_name>`です。

|バージョンと言語  | 既定のパス|
|----------------------|------------|
| SQL Server 2016 |C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\R_SERVICES\library|
| R と SQL Server 2017|C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\R_SERVICES\library |
| Python の SQL Server 2017 |C:\Program files \microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\Lib\site パッケージ |


#### <a name="file-path-for-standalone-server-installations"></a>スタンドアロン サーバー インストール環境のファイル パス

次の表は、SQL Server 2016 R Server (スタンドアロン) または SQL Server 2017 Machine Learning サーバー (スタンドアロン) サーバーがインストールされているときに、バイナリの既定のパスを一覧表示します。 

|バージョン| インストール|既定のパス|
|-------|-------------|------------|
| SQL Server 2016|R Server (スタンドアロン)| C:\Program files \microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning の R のサーバー |C:\Program files \microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Python でのサーバー |C:\Program files \microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Microsoft R Server のスタンドアロン インストール可能性があると同様のサブフォルダー名とファイルを持つ他のフォルダーを検索する場合または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/)です。 これらのサーバー製品では、インストーラーが異なると (つまり C:\Program Files\Microsoft\R Server\R_SERVER または C:\Program Files\Microsoft\ML SERVER\R_SERVER) のパスがあります。 詳細については、次を参照してください。 [Machine Learning Server for Windows のインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)または[Windows 用の R Server 9.1 のインストール](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)です。

## <a name="next-steps"></a>次のステップ

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [リモートの R パッケージ管理を有効にする](r-package-how-to-enable-or-disable.md)
+ [R パッケージ管理の RevoScaleR 関数](use-revoscaler-to-manage-r-packages.md)
+ [R パッケージの同期](package-install-uninstall-and-sync.md)
+ [ローカルの R パッケージ リポジトリの miniCRAN](create-a-local-package-repository-using-minicran.md)
