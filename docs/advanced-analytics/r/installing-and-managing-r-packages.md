---
title: "既定の SQL Server 上の機械学習パッケージ ライブラリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/19/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: d871795effaace791541b4a1f751f8f9e3845b82
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="default-package-libraries-for-machine-learning-on-sql-server"></a>既定の SQL Server 上の機械学習パッケージ ライブラリ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、R と SQL Server と共にインストールされている Python の既定のライブラリについて説明します。 この記事は、これらのライブラリの既定の場所を提供し、どのパッケージと R のバージョンを判断する方法について説明します、または Python は、各インスタンスのライブラリにインストールします。

## <a name="using-the-default-instance-library"></a>既定のインスタンスのライブラリを使用します。

機械学習と SQL Server をインストールするときにインストールする言語ごとに、インスタンス レベルで 1 つのパッケージ ライブラリが作成されます。 SQL Server は、その他のライブラリにインストールされているパッケージにアクセスできません。

リモート クライアントからサーバーに接続する場合、サーバーのコンピューティング コンテキストで実行する R または Python コードは、インスタンス ライブラリでインストールされているパッケージのみを使用できます。

サーバー資産を保護するのには、既定のインスタンスのライブラリは、SQL Server に登録され、コンピューターの管理者によってのみ変更できますをセキュリティで保護されたフォルダーにインストールされます。 コンピューターの所有者でない場合は、このライブラリにパッケージをインストールする管理者から権限を取得する必要があります。 

コンピューターを所有している場合でも、パッケージをインスタンスのライブラリに追加する前に、特定の R または Python パッケージをサーバー環境での有用性を検討してください。 パッケージ ファイルと、必要な複数のバージョンのサイズなどの要因をできるだけでなく、パッケージでのネットワークまたはインターネットの必要かどうかを考慮アクセスします。

### <a name="sql-server"></a>SQL Server

|バージョン | [インスタンス名]|既定のパス|
|------|------|------|
| SQL Server 2016 |既定のインスタンス (default instance)|`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`|
| SQL Server 2016 |名前付きインスタンス (named instance) |`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES\library`|
| R と SQL Server 2017|既定のインスタンス (default instance) |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` |
| R と SQL Server 2017|名前付きインスタンス (named instance)|`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` |
| Python の SQL Server 2017 |既定のインスタンス (default instance) |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library` |
| Python の SQL Server 2017|名前付きインスタンス (named instance)|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES\library` |

### <a name="r-server-standalone-or-machine-learning-server-standalone"></a>R Server (スタンドアロン) または Machine Learning Server (スタンドアロン)

次の表は、SQL Server セットアップを使用して、スタンドアロン サーバーにインストールされている場合、バイナリの既定のパスを一覧表示します。 

|バージョン| インストール|既定のパス|
|------|------|------|
| SQL Server 2016|R Server (スタンドアロン)| |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Machine Learning の R のサーバー |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Machine Learning Python でのサーバー |`C:\Program Files\Microsoft SQL Server\130\PYTHON_SERVER`|

既定のパスが異なる Microsoft R Server または Machine Learning を個別の Windows インストーラーを使用してサーバーをインストールする場合。 一般のようなもの`C:\Program Files\Microsoft\R Server\R_SERVER`です。 詳細については、以下をご覧ください。
 
+ [機械学習の windows Server をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [R Server 9.1 を Windows をインストールします。](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="what-is-included-in-a-default-installation"></a>既定のインストールに含まれるもの

このセクションでは、既定でインストールされている R または Python の機能の概要を示します。

### <a name="default-r-installation-for-sql-server"></a>SQL Server の R の既定のインストール

既定では、R**基本**パッケージがインストールされています。 基本パッケージを含めるなどパッケージによって提供されるコア機能`stats`と`utils`です。

R の基本インストールには、多数のサンプル データセット、および RGui (軽量の対話型エディター) および RTerm (R コマンド プロンプト) などの標準の R ツールも含まれています。

SQL Server 2016 または SQL Server 2017 で R のインストールにも含まれています、 **RevoScaleR**パッケージ、および関連する拡張パッケージおよびプロバイダー、リモート計算コンテキストをサポートするストリーミング、並列 rx 関数の実行とその他の多くの機能です。

RevoScaleR パッケージをアップグレードするには、か、機械学習のコンポーネントだけをアップグレードまたは修正プログラムまたは新しいバージョンの SQL Server のインスタンスをアップグレードするバインディングを使用します。

+ 強化された R 機能の概要については、次を参照してください[Machine Learning サーバーについて。](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ クライアント コンピューター上に RevoScaleR ライブラリをダウンロードするには、インストール[Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

### <a name="default-python-installation-for-sql-server"></a>SQL Server の既定の Python インストール

機械学習の機能と Python 言語のオプションを選択すると、Anaconda ディストリビューションがインストールされます。 正確なバージョンは、インストールされている SQL Server のバージョンと Machine Learning Server インストーラーを使用して、インスタンスをアップグレードするかどうかによって異なります。

|リリース| Anaconda バージョン| その他の変更|
|------|------|------|
| SQL Server 2017 RTM| 3.5.2| 新しい: revoscalepy|
| Machine Learning サーバー 9.2.1 を経由して 2017 年 9 月を更新します。| Anaconda 4.2| revoscalepy への更新 |
| SQL Server 2017 CU3| Anaconda 4.2| revoscalepy への更新 |

Python コード ライブラリ、だけでなく、標準インストールには、サンプル データ、単体テスト、およびサンプル スクリプトが含まれています。

## <a name="restrictions-and-known-issues"></a>制限事項と既知の問題

SQL Server で実行されている任意のソリューションで使用できる**のみ**インスタンスに関連付けられている既定のライブラリにインストールされているパッケージ。

バインディングを使用してインスタンスに R コンポーネントをアップグレードする場合、インスタンスのライブラリへのパスを変更できます。 必ず SQL Server によって現在使用されているライブラリのパスを確認してください。

## <a name="administrative-permissions-required-for-package-installation"></a>パッケージのインストールに必要な管理者権限

パッケージのインストールに必要なアクセス許可は、SQL Server 2016 および SQL Server 2017 間で変更されました。

+ SQL Server 2016 では、管理アクセス権は新しい R パッケージのインストールに必要です。

+ SQL Server 2017、パッケージを管理者として R と、Python の両方のインストールを続行できがある可能性が最も簡単な方法です。

    DDL ステートメント、外部ライブラリの作成には、R ツールを使用せずにパッケージをインストールするデータベース管理者ができます。 

    Machine Learning のサーバーにパッケージの管理機能を使用する場合は、データベース レベルでの R パッケージをインストールする RevoScaleR を使用することができます。 データベース管理者は、機能を有効にし、データベースごとに独自のパッケージをインストールする機能をユーザーに付与する必要があります。 詳細については、次を参照してください。 [Ddl を使用してパッケージの管理を有効にする](r-package-how-to-enable-or-disable.md)です。

### <a name="user-libraries-are-not-supported"></a>ユーザーのライブラリがサポートされていません

インストールできないユーザーのパッケージを安全な場所に多くの場合は、ユーザー ライブラリにパッケージをインストールする手段です。 ただし、SQL Server 環境でこれができません。ファイル システム アクセスでもは多くの場合、サーバーで制限されます。

場合でも、サーバー上のユーザー ドキュメント フォルダーにある場合の管理者権限とアクセスは、SQL Server で実行する外部スクリプトの実行時は、ライブラリの既定インスタンス外にインストールされているすべてのパッケージにアクセスできません。

ユーザーのライブラリに関連する問題を解決する方法のヒントについては、次を参照してください。[ユーザー ライブラリでパッケージがインストールされている](packages-installed-in-user-libraries.md)です。