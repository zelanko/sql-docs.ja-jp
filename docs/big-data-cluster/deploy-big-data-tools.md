---
title: ビッグ データ ツールをインストールする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) で使用するツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 757209ff89fd40dcc737b65d3b19f2a7d4ef247b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419460"
---
# <a name="install-sql-server-2019-big-data-tools"></a>SQL Server 2019 ビッグデータツールのインストール

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) を作成、管理、および使用するためにインストールする必要があるクライアントツールについて説明します。 次のセクションでは、ツールの一覧とインストール手順へのリンクを示します。 ビッグデータクラスターを展開する前に、Windows または Linux で必要とマークされているツールを構成します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>ビッグデータクラスターツール

次の表に、一般的なビッグデータクラスターツールとそのインストール方法を示します。

| ツール | 必須 | 説明 | インストール |
|---|---|---|---|
| **python** | はい | Python は、解釈されたオブジェクト指向の高水準プログラミング言語で、動的なセマンティクスを備えています。 SQL Server 用のビッグデータクラスターの多くの部分は python を使用します。 | [Python をインストールする](#python)|
| **azdata** | [はい] | ビッグデータクラスターをインストールして管理するためのコマンドラインツールです。 | [インストール](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | はい | 基になる Kuberentes クラスターを監視するためのコマンドラインツール ([詳細情報](https://kubernetes.io/docs/tasks/tools/install-kubectl/))。 | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery)\| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (insider)** | はい | SQL Server にクエリを実行するためのクロスプラットフォームグラフィックツール ([詳細情報](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15))。 | [インストール](https://aka.ms/azdata-insiders) |
| **SQL Server 2019 拡張機能** | はい | ビッグデータクラスターへの接続をサポートする Azure Data Studio の拡張機能。 には、データ仮想化ウィザードも用意されています。 | [インストール](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | AKS の場合 | Azure サービスを管理するための最新のコマンドラインインターフェイスです。 AKS ビッグデータクラスターのデプロイで使用されます ([詳細情報](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest))。 | [インストール](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | 省略可 | SQL Server のクエリを実行するための最新のコマンドラインインターフェイス ([詳細情報](https://github.com/dbcli/mssql-cli/blob/master/README.rst))。 | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md)\| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | 一部のスクリプト | SQL Server のクエリを実行するための従来のコマンドラインツール ([詳細情報](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15))。 | [Windows](https://www.microsoft.com/download/details.aspx?id=36433)\| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl**<sup>3</sup> | 一部のスクリプト | Url を使用してデータを転送するためのコマンドラインツール。 | [Windows](https://curl.haxx.se/windows/)\| Linux: curl パッケージのインストール |

<sup>1</sup> kubectl バージョン1.10 以降を使用する必要があります。 また、kubectl のバージョンは、Kubernetes クラスターの1つ以上のマイナーバージョンにする必要があります。 Kubectl client に特定のバージョンをインストールする場合は、「curl を使用した[kubectl バイナリのインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)(windows 10 の場合)」を参照してください。また、windows PowerShell ではなく cmd.exe を使用して curl を実行します。 

> [!TIP]
> Azure Kubernetes Service (AKS) で以前にデプロイされたクラスターで kubectl を使用するには、次の Azure CLI コマンドを使用してクラスターコンテキストを設定する必要があります。
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Azure CLI バージョン2.0.4 以降を使用している必要があります。 必要`az --version`に応じて、を実行してバージョンを検索します。

<sup>3</sup> Windows 10 で実行している場合、コマンドプロンプトからを実行すると、 **curl**は既にパスにあります。 その他のバージョンの Windows では、リンクを使用して**curl**をダウンロードし、パスに配置します。

## <a name="which-tools-are-required"></a>どのツールが必要ですか?

上の表には、ビッグデータクラスターで使用される一般的なツールがすべて用意されています。 どのツールが必要かは、実際のシナリオによって異なります。 ただし、一般に、クラスターの管理、接続、および照会には、次のツールが最も重要です。

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 拡張機能**

残りのツールは、特定のシナリオでのみ必要です。 **Azure CLI**を使用して、AKS デプロイに関連付けられている Azure サービスを管理できます。 **mssql-cli**はオプションですが便利なツールです。これを使用すると、クラスター内の SQL Server マスターインスタンスに接続し、コマンドラインからクエリを実行できます。 GitHub スクリプトを使用してサンプルデータをインストールする場合は、 **sqlcmd**と**curl**が必要です。

### <a id="python"></a>Python をオフラインでインストールする

1. インターネットにアクセスできるコンピューターで、次のいずれかの Python を含む圧縮ファイルをダウンロードします。

   | オペレーティング システム | ダウンロード |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. 圧縮されたファイルをターゲットコンピューターにコピーし、任意のフォルダーに抽出します。

1. Windows の場合のみ、 `installLocalPythonPackages.bat`そのフォルダーからを実行し、パラメーターと同じフォルダーに完全なパスを渡します。

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>次の手順

ツールを構成した後、SQL Server 2019 ビッグデータクラスターをクラウドまたはオンプレミスの Kubernetes にデプロイします。 詳細については、次のデプロイに関する記事を参照してください。

- [クイック スタート:Azure Kubernetes Service (AKS) に SQL Server ビッグデータクラスターをデプロイする](quickstart-big-data-cluster-deploy.md)
- [Kubernetes にビッグデータクラスター SQL Server デプロイする方法](deployment-guidance.md)

ビッグデータクラスターの詳細については、「 [SQL Server 2019 ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
