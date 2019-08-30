---
title: Windows インストーラーで azdata をインストールする
titleSuffix: SQL Server big data clusters
description: インストーラーを使用して、(プレビュー) をインストールし[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]て管理するための azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8dd5d2c7d0210880a82d774185a3f2a915608ec
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158147"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-with-windows-installer"></a>Windows インストーラー `azdata`を使用[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]して管理するためのインストール

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Windows `azdata`で SQL Server 2019 ビッグデータクラスターリリース候補をインストールする方法について説明します。 Windows インストールを使用できるようにするには`azdata` 、 `pip`必須のがインストールされている必要があります。

>Linux (Ubuntu) については、「 [ `azdata` install with installer](./deploy-install-azdata-linux-package.md)」を参照してください。

現時点では、他のオペレーティングシステムまたはディストリビューション`azdata`にインストールするパッケージマネージャーはありません。 これらのプラットフォームについては、「[パッケージマネージャーを`azdata`使用しないインストール](./deploy-install-azdata.md)」を参照してください。

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Microsoft `azdata` Windows インストーラーと共にインストールする

を Microsoft `azdata` Windows インストーラーと共にインストールするには、

1. を`azdata`使用してインストールさ`pip`れた場合は、を削除します。 が`azdata` Windows インストーラーを使用してインストールされている場合は、次の手順に進みます。
1. Windows インストーラー `azdata`を使用してをインストールします。

### <a name="uninstall-if-previous-installation-done-with-pip"></a>以前のインストールがで実行される場合にアンインストールする`pip`

以前のリリースの**mssqlctl**がインストールされている場合は、それを削除します。 次のコマンドは、 **mssqlctl**の CTP 3.1 バージョンを削除します。

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

以前のリリースの`azdata`がインストールされている場合は、最新バージョンをインストールする前に最初にアンインストールすることが重要です。

   CTP 3.2 の場合は、次のコマンドを実行します。

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

削除されたら、 [Windows にインストール`azdata` ](#install-azdata-windows)します。

>[!NOTE]
>以前のインストールが MSI を使用して実行された場合、MSI インストーラーを使用する前に、現在のバージョンをアンインストールする必要はありません。

### <a id="install-azdata-windows"></a>Windows インストーラーと共にインストールする

Windows インストーラーを使用して、Windows `azdata`でインストールまたは更新します。

[Windows インストーラーを`azdata`ダウンロード](http://aka.ms/azdata-msi)します。

コンピューターに変更を加えることができるかどうかを確認する`Yes`メッセージが表示されたら、をクリックします。

### <a name="uninstall-azdata-with-windows-installer"></a>Windows インストーラー `azdata`を使用したアンインストール

Windows インストーラーで`azdata`アンインストールするには、該当するオペレーティングシステムの指示に従います。

| プラットフォーム      | 手順                                           |
| ------------- |--------------------------------------------------------|
| Windows 10    | アプリ > > 設定を開始する                                |
| Windows 8     | プログラムを起動 > コントロールパネル > プログラムをアンインストール > |

アンインストールするプログラムが呼び出さ **`Azdata CLI`** れます。 [このアプリケーション] を選択し`Uninstall` 、[] ボタンをクリックします。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細について[は[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md)、「」を参照してください。
