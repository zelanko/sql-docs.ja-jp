---
title: R パッケージ マネージャーの使用
description: Install. パッケージなどの標準の R コマンドを使用して、SQL Server 2016 R Services または SQL Server Machine Learning Services (データベース内) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1f6d828a7267ab2b4b1def17f9d1c6bf4a6018dc
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633620"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>R パッケージ マネージャーを使用して SQL Server に R パッケージをインストールする
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

標準の R ツールを使用すると SQL Server 2016 または SQL Server 2017 のインスタンスに新しいパッケージをインストールできます。この場合、コンピューターのポート 80 が開いており、管理者権限を持っている必要があります。

> [!IMPORTANT] 
> 現在のインスタンスに関連付けられている既定のライブラリに必ずパッケージをインストールしてください。 ユーザー ディレクトリにパッケージをインストールしないでください。

このプロシージャでは RGui を使用しますが、昇格されたアクセスをサポートする RTerm またはその他の R コマンド ライン ツールを使用することもできます。

## <a name="install-a-package-using-rgui"></a>RGui を使用してパッケージをインストールする

1. [インスタンス ライブラリの場所を決定します](../package-management/r-package-information.md)。 サンプル レポートがインストールされているフォルダーに移動します。 たとえば、SQL Server 2017 の既定のインスタンスの既定のパスは次のようになります。`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe または R.exe を右クリックし、 **[管理者として実行]** を選択します。 必要なアクセス許可がない場合は、データベース管理者に連絡し、必要なパッケージの一覧を提供してください。

1. パッケージ名がわかっている場合は、コマンド ラインから次のように入力できます。`install.packages("the_package-name")`パッケージ名は必ず二重引用符で囲む必要があります。

1. ミラーサイトの使用を確認するメッセージが表示されたら、その場所に適したサイトを選択します。

目的のパッケージがその他のパッケージに依存している場合、R インストーラーは依存関係にあるパッケージを自動的にダウンロードしてインストールします。

SQL Server の複数のインスタンスがある場合 (SQL Server 2016 R Services のサイド バイ サイド インスタンスや SQL Server Machine Learning Services など)、両方のコンテキストでパッケージを使用する場合は、インスタンスごとにインストールを個別に実行します。 パッケージをインスタンス間で共有することはできません。

## <a name = "bkmk_offlineInstall"></a> R ツールを使用したオフライン インストール

サーバーがインターネットにアクセスできない場合は、パッケージを準備するために追加の手順が必要になります。 インターネットにアクセスできないサーバーに R パッケージをインストールするには、次のことを行う必要があります。

+ 依存関係を事前に分析します。
+ インターネットにアクセスできるコンピューターにターゲット パッケージをダウンロードします。
+ 同じコンピューターに必要なパッケージをダウンロードし、すべてのパッケージを 1つのパッケージ アーカイブに配置します。
+ アーカイブを zip 形式にしていない場合は、zip 圧縮します。
+ パッケージ アーカイブをサーバー上の場所にコピーします。
+ アーカイブ ファイルをソースとして指定するターゲット パッケージをインストールします。

> [!IMPORTANT] 
>  インストールを開始する **前** に、すべての依存関係を分析し、必要なパッケージ**すべて**ダウンロードしてください。 このプロセスでは、[miniCRAN](https://mran.microsoft.com/package/miniCRAN) をお勧めします。 この R パッケージは、インストールするパッケージの一覧を取得し、依存関係を分析し、zip 形式のファイルをすべて取得します。 miniCRAN は、その後サーバー コンピューターにコピーできる単一のリポジトリを作成します。 詳細については、「[miniCRAN を使用してローカル パッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)」を参照してください

この手順では、必要なすべてのパッケージを zip 形式で準備し、それらをサーバーにコピーする準備ができていることを前提としています。

1. パッケージの zip 形式のファイル、または zip 形式のすべてのパッケージを含む完全なリポジトリをサーバーがアクセスできる場所にコピーします。

2. インスタンスの R ツールがインストールされているサーバー上のフォルダーを開きます。 たとえば、SQL Server 2016 R Services が搭載されたシステムで Windows コマンドプロンプトを使用している場合は、`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64` に切り替えます。

3. RGui または RTerm を右クリックし、 **[管理者として実行]** を選択します。

4. R コマンドを実行して、`install.packages`パッケージまたはリポジトリの名前と、zip 形式のファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、ディレクトリ `C:\Temp\Downloaded packages` にコピーを保存し、ローカル コンピューターにパッケージをインストールしたと仮定して、ローカルの zip 形式のファイルから R パッケージ `mynewpackage` を抽出します。 パッケージに依存関係がある場合、インストーラーはライブラリ内の既存のパッケージを確認します。 依存関係を含むリポジトリを作成した場合は、必要なパッケージもインストーラーによってインストールされます。

    必要なパッケージがインスタンス ライブラリに存在せず、zip 形式のファイルに見つからない場合、ターゲット パッケージのインストールは失敗します。

## <a name="see-also"></a>参照

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)
