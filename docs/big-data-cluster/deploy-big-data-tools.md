---
title: ビッグ データ ツールをインストールする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) で使用するツールをインストールする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: dc53bdfb71efeafd55752686ff136355bc79bd34
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860483"
---
# <a name="install-sql-server-2019-big-data-tools"></a>SQL Server 2019 ビッグ データ ツールをインストールします。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、管理、作成については、インストールされるクライアント ツールをについて説明し、SQL Server 2019 を使用してビッグ データ クラスター (プレビュー)。 次のセクションでは、一連のツールとインストール手順へのリンクを提供します。 ビッグ データ クラスターをデプロイする前に必須の Windows または Linux にマークされているツールを構成します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>ビッグ データ クラスター ツール

次の表は、一般的なビッグ データ クラスター ツールとそれらをインストールする方法を示します。

| ツール | 必須 | 説明 | インストール |
|---|---|---|---|
| **mssqlctl** | はい | インストールすると、ビッグ データ クラスターを管理するコマンド ライン ツールです。 | [インストール](deploy-install-mssqlctl.md) |
| **kubectl**<sup>1</sup> | はい | 基になる Kuberentes クラスターを監視するためのコマンド ライン ツール ([詳細](https://kubernetes.io/docs/tasks/tools/install-kubectl/))。 | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio** | はい | SQL Server を照会するためのクロスプラット フォームでグラフィカルなツール ([詳細](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15))。 | [インストール](../azure-data-studio/download.md) |
| **SQL Server 2019 の拡張機能** | はい | ビッグ データ クラスターへの接続をサポートする Azure Data Studio の拡張機能です。 また、データの仮想化ウィザードを提供します。 | [インストール](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | AKS の | Azure サービスを管理するための最新のコマンド ライン インターフェイス。 AKS のビッグ データ クラスター展開での使用 ([詳細](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest))。 | [インストール](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | 省略可 | SQL Server を照会するための最新のコマンド ライン インターフェイス ([詳細](https://github.com/dbcli/mssql-cli/blob/master/README.rst))。 | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | いくつかのスクリプトの | SQL Server を照会するための従来のコマンド ライン ツール ([詳細](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15))。 | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | いくつかのスクリプトの | Url を使用してデータを転送するためのコマンド ライン ツールです。 | [Windows](https://curl.haxx.se/windows/) \| Linux: curl パッケージのインストール |

<sup>1</sup> kubectl バージョン 1.10 以降を使用する必要があります。 また、Kubernetes クラスターのマイナー バージョンを 1 つずつずらして kubectl のバージョンがあります。 Kubectl クライアントを特定のバージョンをインストールする場合は、「 [kubectl curl を使用してバイナリをインストール](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl)(Windows 10 を使用して cmd.exe、Windows PowerShell ではなく curl を実行する)。 

> [!TIP]
> Azure Kubernetes Service (AKS) で以前にデプロイされたクラスターでは、kubectl を使用するには、次の Azure CLI コマンドでクラスター コンテキストを設定する必要があります。
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Azure CLI バージョン 2.0.4 を使用する必要がありますまたはそれ以降。 実行`az --version`必要な場合は、バージョンを確認します。

<sup>3</sup> Windows 10 で実行している場合**curl**が、パスに既にコマンド プロンプトから実行する場合。 Windows の他のバージョンでは、ダウンロード**curl**のリンクを使用して、パスに格納します。

## <a name="which-tools-are-required"></a>どのツールが必要ですか。

前の表は、すべてのビッグ データ クラスターで使用される一般的なツールを提供します。 どのツールが必要なは、シナリオによって異なります。 一般に、次のツールへの管理、接続、およびクラスタをクエリに最も重要です。

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019 の拡張機能**

その他のツールは、特定のシナリオでのみ必要です。 **Azure CLI** AKS のデプロイに関連付けられている Azure サービスを管理するために使用できます。 **mssql cli**は、クラスター内の SQL Server のマスター インスタンスに接続し、コマンドラインからクエリを実行することができます、省略可能ですが、便利なツールです。 **Sqlcmd**と**curl**が GitHub のスクリプトを使用してサンプル データをインストールする場合に必要です。

## <a name="next-steps"></a>次のステップ

ツールを構成した後は、クラウドまたはオンプレミスでの Kubernetes に SQL Server 2019 ビッグ データ クラスターを展開します。 詳細については、次のデプロイに関する記事を参照してください。

- [クイック スタート:SQL Server のビッグ データ クラスター Azure Kubernetes Service (AKS) でのデプロイします。](quickstart-big-data-cluster-deploy.md)
- [Kubernetes での SQL Server のビッグ データ クラスターをデプロイする方法](deployment-guidance.md)

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
