---
title: "Machine Learning Server (スタンドアロン) または Microsoft R Server (スタンドアロン) をコマンドラインからインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: "4"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 35194b08e43c98985e0ae0d03f1e470fe8370383
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="install-machine-learning-server-standalone-or-microsoft-r-server-standalone-from-the-command-line"></a>コマンドラインから Machine Learning Server (スタンドアロン) または Microsoft R Server (スタンドアロン) をインストールします。

この記事では、SQL Server コマンドライン引数を使用して、コマンドラインを使用して、次の SQL Server 機能をインストールする方法について説明します。

+ [SQL server 2017 機械学習のサーバー (スタンドアロン)](#bkmk_mls2017) 
+ [SQL Server 2016 では、Microsoft R Server (スタンドアロン)](#bkmk_mrs2016)

**無人**インストールは、セットアップ ユーティリティの場所を指定してをインストールする機能を示す引数を使用することが必要です。

**Quiet** インストールの場合、同じ引数を渡し、 **/q** スイッチを追加します。 プロンプトが指定されていないと、操作は必要ありません。 ただし、必要な引数が省略されている場合に、セットアップが失敗します。

## <a name="prerequisites"></a>前提条件

SQL Server のコマンド ライン インストールを実行し、スクリプトの引数に理解して方法を理解する必要があります。

詳細については、次を参照してください。[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)です。

インターネットへのアクセスを持たないコンピューターで Machine Learning のサーバーまたは Microsoft R Server (スタンドアロン) をインストールする場合は、R (または Python) の必須コンポーネントを事前にダウンロードし、ローカル フォルダーにコピーする必要があります。 ダウンロードの場所を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](installing-ml-components-without-internet-access.md)です。


## <a name="bkmk_mls2017"></a>マイクロソフトの機械学習のサーバー (スタンドアロン) のインストールします。

**適用されます SQL Server 2017。**

Machine Learning Server (スタンドアロン) のみとその前提条件をインストールする管理者特権でコマンド プロンプトから次のコマンドを実行します。

+ 機能の引数は、SQL Server のライセンス条項は、必要です。
+ 1 つの言語、または両方 R と、Python をインストールすることができますが、個別のライセンスはごとに必要です。

この例は、R. をインストールするための引数を示しています。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

この例では、Python をインストールするための引数を使用します。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MPY  /IACCEPTPYTHONOPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

+ 進行状況とプロンプトを表示するには、_/q_ 引数を削除します。
+ 引数を使用する場合**機能 = SQL_SHARED_MR**R でも Python での Machine Learning のサーバー コンポーネントのみをインストールします。 このインストールには、既定で自動的にインストールされているすべての前提条件が含まれています。 ただし、最初にインストールするときに、少なくとも 1 つの言語を追加することをお勧めします。
+ 追加**SQL_INST_MR** R. のサポートをインストールするには
+ 追加**SQL_INST_MPY** Python のサポートをインストールします。
+ **IACCEPTROPENLICENSETERMS** は、オープン ソースの R コンポーネントを使用するライセンス条項を承諾したことを意味します。
+ **IACCEPTPYTHONLICENSETERMS** Python コンポーネントを使用するライセンス条項に同意を受け入れたことを示します。
+ **IACCEPTSQLSERVERLICENSETERMS** はセットアップ ウィザードの実行に必要です。


## <a name="bkmk_mrs2016"></a>Microsoft R Server (スタンドアロン) のインストール

**適用されます SQL Server 2016。**

インストールする管理者特権でコマンド プロンプトから次のコマンドを実行**のみ**Microsoft R Server (スタンドアロン) とその前提条件です。 

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

> [!TIP]
> インストールすることはできませんこの SQL Server R Services のインスタンスをホストしている同じコンピューターをお勧めします。

## <a name="post-installation-tasks"></a>インストール後のタスク

Microsoft R Server の別のインスタンスと同じパラメーターを設定するにはインストール中に作成する構成ファイルを再利用できます。 詳細については、次を参照してください。 [SQL サーバーのインストール、構成ファイルを使用して](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)です。

### <a name="review-installed-components"></a>インストールされているレビュー コンポーネント

セットアップが完了したら、SQL Server のセットアップで作成された構成ファイルを、セットアップ処理の概要と共に確認できます。

既定では、すべてのセットアップ ログと概要 for SQL Server との関連する機能は、次のフォルダーに作成されます。

+ SQL Server 2017: `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`
+ SQL Server 2016:  `C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`

インストールされている各機能の個別のサブフォルダーが作成されます。

### <a name="customize-the-r-or-python-environment"></a>R、または Python 環境をカスタマイズします。

インストール後、追加の R または Python パッケージをインストールできます。 プロセスでは、SQL Server 2016 または SQL Server 2017 のどちらを使用しているかどうかによってやや異なります。

SQl Server の 2017年では、インストールし、T-SQL を使用して、R パッケージを管理します。 詳細については、次を参照してください。[のインストールと R パッケージを管理する](../r/install-additional-r-packages-on-sql-server.md)です。

Python、および SQL Server 2016 では、管理者が必要になる可能性がある追加のライブラリをインストールする必要があります。

> [!IMPORTANT]
> SQL Server で R コードを実行する場合は、開発、ソリューション、および SQL Server インスタンスを実行またはソリューションの配置を使用するコンピューターに同じパッケージをインストールすることを確認します。

### <a name="upgrading-r-server-or-sql-server-machine-learning"></a>R Server または SQL Server の機械学習のアップグレード

SQL Server を使用しない場合は、個別の Windows インストーラーを使用して、Microsoft R Server または Machine Learning のサーバーをインストールできます。 ダウンロード場所および手順については、これらのリンクを参照してください。

+ [機械学習の windows Server をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [R Server 9.0.1 を Windows をインストールします。](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) 

Machine Learning サーバー用の個別の windows インストーラーは、機械学習のインスタンスに関連付けられているコンポーネントのアップグレードにも使用できます。  詳細については、次のリンクを参照してください。

+ [SqlBindR を使用して R のアップグレード](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
