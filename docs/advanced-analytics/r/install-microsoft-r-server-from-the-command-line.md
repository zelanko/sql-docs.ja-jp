---
title: "コマンドラインから Microsoft R Server をインストールする | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 811709fae77dee6daa46a97a51c44c02e372d9a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="install-microsoft-r-server-from-the-command-line"></a>コマンドラインから Microsoft R Server をインストールする
    
このトピックでは、SQL Server コマンドライン引数を使用して、SQL Server 2016 での Microsoft R Server のインストールまたは SQL Server 2017 で Machine Learning Server (スタンドアロン) をインストールする方法について説明します。 

> [!NOTE]
個別の Windows インストーラーを使用して、Microsoft R Server をインストールすることもできます。 詳細については、次を参照してください。[インストール R Server 9.0.1 for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)です。 

## <a name="prerequisites"></a>前提条件

このインストール方法では、SQL Server のコマンド ライン インストールを実行する方法を理解し、そのスクリプトの引数に慣れている必要があります。

- **無人** インストールでは、セットアップ ユーティリティの場所を指定し、インストールする機能を示す引数を使用する必要があります。 
- **Quiet** インストールの場合、同じ引数を渡し、 **/q** スイッチを追加します。 プロンプトは表示されず、操作の必要もありません。 ただし、必要な引数が省略されている場合、セットアップは失敗します。

詳細については、「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。

## <a name="sql-server-2017-microsoft-machine-learning-server-standalone"></a>SQL Server 2017: Microsoft した機械学習 Server (スタンドアロン)

Microsoft Machine Learning サーバーのみ (スタンドアロン) とその前提条件をインストールする管理者特権でコマンド プロンプトから次のコマンドを実行します。  例では、R. をインストールするための引数を示しています。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```

進行状況とプロンプトを表示するには、_/q_ 引数を削除します。

- **機能 = SQL_SHARED_MR** Machine Learning のサーバー コンポーネントのみを取得します。 これには、すべての前提条件には、既定で自動的にインストールされますが含まれます。
- **SQL_INST_MR**は R 言語の installl サポートするために必要です。
- **SQL_INST_MPY** Python のサポートをインストールするが必要です。
- **IACCEPTROPENLICENSETERMS** は、オープン ソースの R コンポーネントを使用するライセンス条項を承諾したことを意味します。
- **IACCEPTPYTHONLICENSETERMS** Python コンポーネントを使用するライセンス条項に同意を受け入れたことを示します。
- **IACCEPTSQLSERVERLICENSETERMS** はセットアップ ウィザードの実行に必要です。

**注**

1. 機能の引数は、SQL Server のライセンス条項は、必要です。
2. ライセンス契約フラグと共に、1 つ以上の言語を指定します。
3. 1 つの言語、または両方 R と、Python をインストールすることができますが、個別のライセンスはごとに必要です。

## <a name="sql-server-2016-microsoft-r-server-standalone"></a>SQL Server 2016: Microsoft R Server (スタンドアロン)

管理者特権で次のコマンドをコマンド プロンプトより実行し、Microsoft R Server (スタンドアロン) とその前提条件のみをインストールします。  この例は、SQL Server 2016 セットアップで使用される引数を示します。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

## <a name="offline-installation"></a>オフライン インストール

インターネットへのアクセスを持たないコンピューターで Machine Learning のサーバーまたは Microsoft R Server (スタンドアロン) をインストールする場合は、必要な R コンポーネントを事前にダウンロードし、ローカル フォルダーにコピーする必要があります。 ダウンロード場所については、「 [インターネットへのアクセスなしで R コンポーネントをインストールする](../r/installing-ml-components-without-internet-access.md)」を参照してください。

## <a name="what-is-installed"></a>インストールされている内容

セットアップが完了したら、SQL Server のセットアップで作成された構成ファイルを、セットアップ処理の概要と共に確認できます。

既定では、すべてのセットアップ ログと概要 for SQL Server との関連する機能は、次のフォルダーに作成されます。

- SQL Server 2016 の場合:`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`
- SQL Server 2017:`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`

インストールされる機能ごとに個別にサブフォルダーが作成されます。

Microsoft R Server の別のインスタンスと同じパラメーターを設定するにはインストール中に作成する構成ファイルを再利用できます。 詳細については、「 [構成ファイルを使用した SQL Server 2016 のインストール](https://msdn.microsoft.com/library/dd239405.aspx)


## <a name="customize-your-r-environment"></a>R 環境内をカスタマイズします。

インストール後、さらに R パッケージをインストールできます。 詳細については、「 [Installing and Managing R Packages](../r/install-additional-r-packages-on-sql-server.md)」 (R パッケージのインストールおよび管理) を参照してください。

> [!IMPORTANT]
> SQL Server で R コードを実行する場合は、開発、ソリューション、および SQL Server インスタンスを実行またはソリューションの配置を使用するコンピューターに同じパッケージをインストールすることを確認します。

R (In-database) の Machine Learning のサービスをインストールした後は、指定した SQL Server インスタンスに関連付けられている R のバージョンをアップグレードするのに個別の Windows インストーラーを使用することができます。 詳細については、次を参照してください。[アップグレード R を使用して SqlBindR](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。



