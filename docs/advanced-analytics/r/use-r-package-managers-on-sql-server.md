---
title: SQL Server Machine Learning Services の R パッケージ マネージャーを使用して、
description: SQL Server 2016 R Services または SQL Server 2017 の Machine Learning Services (In-database) に新しい R パッケージを追加するのにには、install.packages などの標準の R コマンドを使用します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6012fb1a3376c00a64239e0fbf10115b8a4367d8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510389"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>SQL Server に R パッケージをインストールするのに R パッケージ マネージャーを使用します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

標準の R ツールを使用して、SQL Server 2016 のインスタンスに新しいパッケージをインストールまたはコンピューターを提供する、SQL Server 2017 が開いているポート 80 と管理者権限します。

> [!IMPORTANT] 
> 現在のインスタンスに関連付けられている既定のライブラリにパッケージをインストールしてください。 ユーザーのディレクトリにパッケージをインストールことはありません。

この手順で RGui は RTerm またはその他の R コマンド ライン ツールは管理者特権でのアクセスをサポートするを使用することができます。

## <a name="install-a-package-using-rgui"></a>RGui を使用してパッケージをインストールします。

1. [インスタンスのライブラリの場所を特定](installing-and-managing-r-packages.md)します。 R tools がインストールされているフォルダーに移動します。 たとえば、SQL Server 2017 の既定のインスタンスの既定のパスはとおりです。 `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe を右クリックして**管理者として実行**します。 必要なアクセス許可がない、データベース管理者に問い合わせてくださいし、必要なパッケージの一覧を提供します。

1. コマンドラインから、パッケージ名がわかっている場合を入力できます。`install.packages("the_package-name")` 二重引用符は、パッケージ名に必要な。

1. ミラー サイトを求められたら、その地域の便利な任意のサイトを選択します。

ターゲット パッケージは、追加のパッケージに依存している場合、R インストーラーは自動的に、依存関係をダウンロードしをインストールします。

SQL Server 2016 R Services と SQL Server 2017 Machine Learning Services のサイド バイ サイドのインスタンスなどの SQL Server の複数のインスタンスがある場合は、両方のコンテキストで、パッケージを使用する場合、インスタンスごとに個別にインストールを実行します。 パッケージは、インスタンス間で共有することはできません。

## <a name = "bkmk_offlineInstall"></a> R ツールを使用してオフラインのインストール

サーバーには、インターネット アクセスができない、追加の手順は、パッケージを準備する必要があります。 インターネットへのアクセスがないサーバー上の R パッケージをインストールするには、次の必要があります。

+ 依存関係を事前に分析します。
+ ターゲット パッケージをインターネットにアクセスできるコンピューターにダウンロードします。
+ 同じコンピューターに、必要なパッケージをダウンロードし、すべてのパッケージを 1 つのパッケージのアーカイブに配置します。
+ なっていない zip 形式の場合は、アーカイブを zip 圧縮します。
+ パッケージのアーカイブをサーバー上の場所にコピーします。
+ アーカイブ ファイルをソースとして指定するターゲット パッケージをインストールします。

> [!IMPORTANT] 
>  すべての依存関係を分析することを必ずダウンロードと**すべて**パッケージに必要な**する前に**インストールを開始します。 お勧め[miniCRAN](https://mran.microsoft.com/package/miniCRAN)このプロセスにします。 この R パッケージは、パッケージ、依存関係を分析、およびのすべての zip ファイルを取得するをインストールするのリストを取得します。 miniCRAN は、サーバー コンピューターにコピーできる単一のリポジトリを作成します。 詳細については、次を参照してください[miniCRAN を使用してローカル パッケージ リポジトリを作成する。](create-a-local-package-repository-using-minicran.md)

この手順では、zip 形式の形式で、必要がありますして、サーバーにコピーする準備がすべてのパッケージを準備したことを前提としています。

1. パッケージのコピーの圧縮ファイル、または複数のパッケージ内のすべてのパッケージを含む、完全なリポジトリは、サーバーがアクセスできる場所の形式を zip 形式します。

2. インスタンスの R ツールがインストールされているサーバー上のフォルダーを開きます。 SQL Server 2016 R Services でのシステムを Windows のコマンド プロンプトを使用している場合の切り替えなど、`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`します。

3. RGui または RTerm と選択を右クリックして**管理者として実行**します。

4. R コマンドを実行して`install.packages`パッケージまたはリポジトリの名前と、その zip ファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、R パッケージを抽出`mynewpackage`ディレクトリにコピーを保存すると仮定すると、ローカル zip ファイルから`C:\Temp\Downloaded packages`、ローカルのコンピューターにパッケージをインストールします。 パッケージにすべての依存関係がある場合、ライブラリ内の既存のパッケージのインストーラーを確認します。 依存関係を含むリポジトリを作成した場合も、必要なパッケージがインストールされます。

    場合は、必要なパッケージは、インスタンスのライブラリに存在しないと、その zip ファイル内に見つかりません、ターゲットのパッケージのインストールは失敗します。

## <a name="see-also"></a>関連項目

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)
