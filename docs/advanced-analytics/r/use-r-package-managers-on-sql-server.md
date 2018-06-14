---
title: SQL Server の Machine Learning のサービスに新しい R パッケージをインストール |Microsoft ドキュメント
description: SQL Server 2016 の R Services または SQL Server 2017 Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8f7b0ee2b623f6a208a92823948bf0295bae33f6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707500"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>R パッケージ マネージャーを使用して、SQL Server で R パッケージをインストールするには
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

標準の R ツールを使用するには SQL Server 2016 のインスタンスに新しいパッケージをインストールするコンピューターを提供する、SQL Server 2017 開いているポート 80 や管理者権限します。

> [!IMPORTANT] 
> 現在のインスタンスに関連付けられている既定のライブラリにパッケージをインストールすることを確認します。 ユーザーのディレクトリにパッケージをインストールことはありません。

この手順が RGui を使用しますが、RTerm またはその他の R コマンド ライン ツールを管理者特権でのアクセスをサポートするを使用することができます。

## <a name="install-a-package-using-rgui"></a>RGui を使用してパッケージをインストールします。

1. [インスタンスのライブラリの場所を特定](installing-and-managing-r-packages.md)です。 R ツールがインストールされているフォルダーに移動します。 たとえば、SQL Server 2017 既定のインスタンスの既定のパスはとおりです。 `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe を右クリックし **管理者として実行**です。 必要なアクセス許可がない、データベース管理者に連絡し、必要なパッケージの一覧を指定します。

1. コマンドラインからパッケージ名がわかっている場合を入力できます。`install.packages("the_package-name")`二重引用符は、パッケージ名に必要です。

1. ミラー サイトを求められたら、現在の場所は便利では任意のサイトを選択します。

ターゲットのパッケージは、その他のパッケージに依存している場合、R インストーラーは自動的に依存関係をダウンロードして、インストールします。

SQL Server 2016 の R Services および SQL Server 2017 Machine Learning Services のサイド バイ サイド インスタンスなど、SQL Server の複数のインスタンスがある場合は、両方のコンテキストでパッケージを使用する場合、インスタンスごとに個別にインストールを実行します。 パッケージは、インスタンス間で共有することはできません。

## <a name = "bkmk_offlineInstall"></a> R ツールを使用してオフラインのインストール

サーバーがインターネットにアクセスを持たない場合、パッケージの準備をする追加の手順が必要です。 インターネット アクセスが許可されていないサーバーで R パッケージをインストールするには、次の必要があります。

+ 事前に依存関係を分析します。
+ 対象パッケージをインターネットにアクセスできるコンピューターにダウンロードします。
+ 同じコンピューターに、必要なパッケージをダウンロードして、1 つのパッケージ アーカイブ内のすべてのパッケージを配置します。
+ なっていない zip 形式の場合は、アーカイブを zip 圧縮します。
+ パッケージのアーカイブをサーバー上の場所にコピーします。
+ アーカイブ ファイルをソースとして指定する対象パッケージをインストールします。

> [!IMPORTANT] 
>  すべての依存関係を分析することを必ずおよびダウンロード**すべて**必須パッケージ**する前に**インストールを開始します。 お勧め[miniCRAN](https://mran.microsoft.com/package/miniCRAN)このプロセスにします。 この R パッケージ リストを受け取り、パッケージをインストールしてなどの依存関係を分析するすべての zip ファイルを取得します。 miniCRAN は、サーバー コンピューターにコピーできる 1 つのリポジトリを作成します。 詳細については、「 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。](create-a-local-package-repository-using-minicran.md)

この手順では、ことと必要とする、zip 形式の形式でサーバーにコピーする準備がすべてのパッケージを準備することを前提としています。

1. パッケージのコピーがファイルを zip 形式または複数のパッケージのすべてのパッケージを含む完全なリポジトリがサーバーにアクセスできる場所の形式を zip 形式です。

2. インスタンスの R ツールがインストールされているサーバー上のフォルダーを開きます。 たとえば、SQL Server 2016 の R Services のシステムを Windows のコマンド プロンプトを使用している場合は、切り替える`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`です。

3. RGui または RTerm と選択 を右クリックして**管理者として実行**です。

4. R コマンドを実行`install.packages`パッケージまたはリポジトリの名前とその zip ファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、R パッケージを抽出`mynewpackage`ディレクトリにコピーを保存すると仮定した場合、ローカル zip ファイルから`C:\Temp\Downloaded packages`、し、ローカル コンピューターにパッケージをインストールします。 パッケージがすべての依存関係を持つ、インストーラーは、ライブラリ内の既存のパッケージを確認します。 依存関係を含むリポジトリを作成した場合、インストーラーは必要なパッケージをインストールします。

    場合は、必要なパッケージは、インスタンス ライブラリに存在しない、その zip ファイルに見つかりません対象パッケージのインストールは失敗します。

## <a name="see-also"></a>参照

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)