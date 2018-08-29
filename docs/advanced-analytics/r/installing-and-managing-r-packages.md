---
title: 既定の SQL Server の R と SQL Server Machine Learning で R と Python のパッケージ ライブラリ |Microsoft Docs
description: SQL Server R Services で R Server では、Machine Learning サービス (In-database)、および Machine Learning Server (スタンドアロン) によってインストールされた R と Python のパッケージ
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7f5c51e9b93aca5d52858417667865633a0c4151
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118310"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>SQL Server の既定の R と Python のパッケージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server とパッケージ ライブラリを検索する場所にインストールされている R と Python のパッケージを一覧表示します。  

## <a name="r-package-list-for-sql-server"></a>SQL Server の R パッケージの一覧

R パッケージがインストールされている[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)と[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)セットアップ中に、R の機能を選択するとします。 

パッケージ         | 2016 | 2017 | 説明 |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | リモート計算コンテキスト、ストリーミング、データのインポートと変換、モデリング、視覚エフェクトと分析の rx 関数を並列実行に使用されます。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |ストアド プロシージャで R スクリプトを含めるために使用します。 |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | R での機械学習アルゴリズムを追加します。 | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | R での MDX ステートメントを記述するために使用 |

MicrosoftML、olapR を既定では SQL Server 2017 Machine Learning Services で利用できます。 これらのパッケージを追加する、SQL Server 2016 R Services のインスタンスで、[コンポーネントのアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。 コンポーネントのアップグレードも取得するパッケージの新しいバージョン (たとえば、SQL Server のパッケージ管理の機能を含む RevoScaleR の新しいバージョン)。

## <a name="python-package-list-for-sql-server"></a>SQL Server 用の Python パッケージの一覧

インストールするときに、Python パッケージは SQL Server 2017 でのみ使用可能な[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) Python 機能を選択します。

| パッケージ         | 2017    |  説明 |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | リモート計算コンテキスト、ストリーミング、データのインポートと変換、モデリング、視覚エフェクトと分析の rx 関数を並列実行に使用されます。 |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Python での機械学習アルゴリズムを追加します。 |

## <a name="open-source-r-in-your-installation"></a>オープン ソースでの R のインストール

R のサポートには、オープン ソースが含まれていますがされるため、基本の R 関数を呼び出すし、追加のオープン ソースとサード パーティ製のパッケージをインストールできます。 R 言語サポートなどのコア機能を含む**基本**、 **stats**、 **utils**、およびその他。 R の基本インストールは、多数のサンプル データセット、および標準の R ツールにも含まれます**RGui** (軽量の対話型エディター) と**RTerm** (R コマンド プロンプト)。 

インストールに含まれているオープン ソース R の配布が[Microsoft R を開きます (MRO)](https://mran.microsoft.com/open)します。 MRO 基本 r などその他のオープン ソース パッケージを含めることで値を追加する、 [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)します。

次の表は、SQL Server セットアップを使用して MRO によって提供される R のバージョンをまとめたものです。

|リリース             | R のバージョン       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 の Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Web 上の新しいバージョンに SQL Server セットアップによってインストールされている R のバージョンを上書きする必要があります手動でことはありません。 Microsoft R パッケージが基づく R. 変更の特定のバージョンで、インストールが不安定になることです。

## <a name="open-source-python-in-your-installation"></a>インストールでの Python のオープン ソース

SQL Server 2017 では、Python コンポーネントを追加します。 Python 言語のオプションを選択すると 4.2 の Anaconda ディストリビューションがインストールされています。 Python のコード ライブラリだけでなく、標準的なインストールには、サンプル データ、単体テスト、およびサンプル スクリプトが含まれています。 

SQL Server 2017 の Machine Learning は、R と Python の両方をサポートする最初のリリースです。

|リリース             | Anaconda バージョン| Microsoft パッケージ    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning サービス  | Python 3.5 経由で 4.2 | revoscalepy、microsoftml |

Web 上の新しいバージョンに SQL Server セットアップによってインストールされている Python のバージョンを上書きする必要があります手動でことはありません。 Microsoft Python パッケージは、Anaconda の特定のバージョンに基づいています。 インストールの変更が不安定になることです。

## <a name="component-upgrades"></a>コンポーネントのアップグレード

最初のインストール後、サービス パックと累積的更新プログラムは、R と Python のパッケージが更新されるが、完全なバージョンのアップグレードはのみによって可能*バインド*モダン ライフ サイクル サポート ポリシーにします。 バインディングは、サービス モデルを変更します。 既定では、最初のインストール後の R パッケージは更新サービス パックと累積的更新プログラムです。 追加のパッケージと R のコア コンポーネントの完全なバージョンのアップグレード (SQL Server 2017 への SQL Server 2016) から製品アップグレードによってのみ可能ですか、R をバインドすることによって、Microsoft Machine Learning Server をサポートします。 詳細については、次を参照してください。 [SQL Server のアップグレードの R と Python コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

## <a name="package-library-location"></a>パッケージ ライブラリの場所

SQL server machine learning をインストールするときに、各言語をインストールするのインスタンス レベルで 1 つのパッケージ ライブラリが作成されます。 、Windows では、インスタンス ライブラリは、SQL Server に登録されているセキュリティで保護されたフォルダーです。

すべてのスクリプトまたはコードを実行での SQL Server データベースは、インスタンスのライブラリから関数を読み込む必要があります。 SQL Server は、その他のライブラリにインストールされているパッケージにアクセスできません。 これは、リモート クライアントにも適用されます。 リモート クライアントからサーバーへの接続、ときに server コンピューティング コンテキストで実行する R または Python のコードはのみインスタンス ライブラリにインストールされているパッケージを使用できます。

サーバー資産を保護するには、インスタンスの既定のライブラリは、コンピューターの管理者によってのみ変更できます。 コンピューターの所有者でない場合は、このライブラリにパッケージをインストールする管理者からアクセス許可を取得する必要があります。 

#### <a name="file-path-for-in-database-engine-instances"></a>エンジンのインスタンスをデータベース内のファイル パス

次の表は、ファイルの場所を R と Python のバージョンとデータベース エンジン インスタンスの組み合わせを示します。 MSSQL13 が SQL Server 2016 に示しは R のみです。 MSSQL14 は、SQL Server 2017 を示しは R と Python のフォルダーがあります。 

ファイル パスには、インスタンス名も含まれます。 SQL Server インストール[データベース エンジン インスタンス](../../database-engine/configure-windows/database-engine-instances-sql-server.md)既定のインスタンス (MSSQLSERVER)、またはユーザー定義の名前付きインスタンスとして。 SQL Server は、名前付きインスタンスとしてインストールする場合は、次のように追加されます。 その名前が表示されます:`MSSQL13.<instance_name>`します。

|バージョンおよび言語  | 既定のパス|
|----------------------|------------|
| SQL Server 2016 |C:\Program files \microsoft SQL Server\MSSQL13 します。MSSQLSERVER\R_SERVICES\library|
| R を使用した SQL Server 2017|C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 の Python の使用 |C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\Lib\site パッケージ |


#### <a name="file-path-for-standalone-server-installations"></a>スタンドアロン サーバーのインストール ファイルのパス

次の表は、SQL Server 2016 R Server (スタンドアロン) または SQL Server 2017 の Machine Learning Server (スタンドアロン) サーバーがインストールされている場合、バイナリの既定のパスを示します。 

|バージョン| インストール|既定のパス|
|-------|-------------|------------|
| SQL Server 2016|R Server (スタンドアロン)| C:\Program files \microsoft SQL server \130\r_server|
|SQL Server 2017|Machine Learning Server、R の使用 |C:\Program files \microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server、Python の使用 |C:\Program files \microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Microsoft R Server のスタンドアロン インストール可能性があるようなサブフォルダー名とファイルを持つその他のフォルダーを検索する場合または[Machine Learning Server](https://docs.microsoft.com/machine-learning-server/)します。 これらのサーバー製品では、別のインストーラーとパス (つまり、C:\Program Files\Microsoft\R Server\R_SERVER または C:\Program Files\Microsoft\ML SERVER\R_SERVER) があります。 詳細については、次を参照してください。 [Machine Learning Server を Windows にインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)または[Windows のインストールの R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)します。

## <a name="next-steps"></a>次の手順

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [リモートの R パッケージ管理を有効にする](r-package-how-to-enable-or-disable.md)
+ [R パッケージ管理の RevoScaleR 関数](use-revoscaler-to-manage-r-packages.md)
+ [R パッケージの同期](package-install-uninstall-and-sync.md)
+ [ローカルの R パッケージ リポジトリの miniCRAN](create-a-local-package-repository-using-minicran.md)
