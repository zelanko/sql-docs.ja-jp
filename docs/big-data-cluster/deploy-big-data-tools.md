---
title: ビッグ データ ツールをインストールする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) で使用するツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 757209ff89fd40dcc737b65d3b19f2a7d4ef247b
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419460"
---
# <a name="install-sql-server-2019-big-data-tools"></a>SQL Server 2019 のビッグ データ ツールをインストールする

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグ データ クラスター (プレビュー) を作成、管理、使用するためにインストールする必要があるクライアント ツールについて説明します。 次のセクションでは、ツールおよびインストール手順へのリンクの一覧を示します。 ビッグ データ クラスターを配置する前に、必須とマークされているツールを Windows または Linux で構成します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>ビッグ データ クラスターのツール

次の表では、一般的なビッグ データ クラスター ツールとそのインストール方法を示します。

| ツール | Required | [説明] | インストール |
|---|---|---|---|
| **python** | はい | Python は、動的なセマンティクスを備えた、インタープリター方式でオブジェクト指向の高水準プログラミング言語です。 SQL Server 用のビッグ データ クラスターの多くの部分で、Python が使われています。 | [Python のインストール](#python)|
| **azdata** | はい | ビッグ データ クラスターをインストールして管理するためのコマンドライン ツールです。 | [インストール](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | はい | 基になる Kuberentes クラスターを監視するためのコマンドライン ツールです ([詳細情報](https://kubernetes.io/docs/tasks/tools/install-kubectl/))。 | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (Insiders)** | はい | SQL Server のクエリを実行するためのクロスプラットフォーム グラフィック ツールです ([詳細情報](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15))。 | [インストール](https://aka.ms/azdata-insiders) |
| **SQL Server 2019 拡張機能** | はい | ビッグ データ クラスターへの接続をサポートする Azure Data Studio の拡張機能です。 データ仮想化ウィザードも提供されています。 | [インストール](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | AKS の場合 | Azure のサービスを管理するための最新のコマンドライン インターフェイスです。 AKS ビッグ データ クラスターの展開で使われます ([詳細情報](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest))。 | [インストール](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | 省略可 | SQL Server のクエリを実行するための最新のコマンドライン インターフェイスです ([詳細情報](https://github.com/dbcli/mssql-cli/blob/master/README.rst))。 | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | 一部のスクリプトの場合 | SQL Server のクエリを実行するための従来のコマンドライン ツールです ([詳細情報](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15))。 | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | 一部のスクリプトの場合 | URL でデータを転送するためのコマンドライン ツールです。 | [Windows](https://curl.haxx.se/windows/) \| Linux: curl パッケージのインストール |

<sup>1</sup> kubectl バージョン 1.10 以降を使う必要があります。 また、kubectl のバージョンは、Kubernetes クラスターより 1 つ上または下のマイナー バージョンにする必要があります。 特定のバージョンの Kubectl クライアントをインストールする場合は、「[curl を使用して kubectl バイナリをインストールする](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)」を参照してください (windows 10 では、Windows PowerShell ではなく cmd.exe を使って、curl を実行してください)。 

> [!TIP]
> Azure Kubernetes Service (AKS) に以前に展開されたクラスターで kubectl を使うには、次の Azure CLI コマンドを使ってクラスター コンテキストを設定する必要があります。
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Azure CLI バージョン 2.0.4 以降を使う必要があります。 バージョンを確認する必要がある場合は、`az --version` を実行します。

<sup>3</sup> Windows 10 の場合は、cmd プロンプトから実行するときは、**curl** は既に PATH にあります。 他のバージョンの Windows では、リンクを使って **curl** をダウンロードし、PATH に配置します。

## <a name="which-tools-are-required"></a>必要なツール

上の表では、ビッグ データ クラスターで使われる一般的なツールがすべて示されています。 どのツールが必要かは、実際のシナリオによって異なります。 ただし、一般に、クラスターの管理、接続、クエリを行うには、次のツールが最も重要です。

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 拡張機能**

残りのツールは、特定のシナリオでのみ必要です。 **Azure CLI** を使って、AKS の展開に関連付けられている Azure サービスを管理できます。 **mssql-cli** は必須ではありませんが便利なツールです。これを使うと、クラスター内の SQL Server マスター インスタンスに接続し、コマンド ラインからクエリを実行できます。 そして、GitHub スクリプトでサンプル データをインストールする場合は、**sqlcmd** と **curl** が必要です。

### <a id="python"></a> Python をオフラインでインストールする

1. インターネットにアクセスできるコンピューターで、Python が含まれる次のいずれかの圧縮ファイルをダウンロードします。

   | オペレーティング システム | ダウンロード |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. 圧縮されたファイルをターゲット コンピューターにコピーし、任意のフォルダーに抽出します。

1. Windows の場合にのみ、そのフォルダーから `installLocalPythonPackages.bat` を実行して、パラメーターと同じフォルダーへの完全なパスを渡します。

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>次の手順

ツールを構成した後、クラウドまたはオンプレミスの Kubernetes に SQL Server 2019 ビッグ データ クラスターを配置します。 詳しくは、展開に関する次の記事をご覧ください。

- [クイックスタート: Azure Kubernetes Service (AKS) に SQL Server ビッグ データ クラスターを展開する](quickstart-big-data-cluster-deploy.md)
- [Kubernetes 上に SQL Server ビッグ データ クラスターを展開する方法](deployment-guidance.md)

ビッグ データ クラスターについて詳しくは、[SQL Server 2019 ビッグ データ クラスターの概要](big-data-cluster-overview.md)に関する記事をご覧ください。
