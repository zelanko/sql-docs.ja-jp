---
title: "クラウド内の SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、任意のクラウド内の Linux 上の SQL Server 2017 を実行する方法を示します。"
author: annashres
ms.author: annashres
manager: craigg
ms.date: 10/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.component: 
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.openlocfilehash: 613f6e1b0182d5003c68380bb5a5698397db2207
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="run-the-sql-server-2017-in-the-cloud"></a>SQL Server 2017 をクラウドで実行します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このクイック スタート チュートリアルでは、Red Hat Enterprise Linux (RHEL)、SUSE Linux Enterprise Server (SLES)、または任意のクラウドで Ubuntu で SQL Server 2017 をインストールします。 移動して[Azure ポータルでの SQL Server の Linux 仮想マシンをプロビジョニング](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)を Azure での Linux に SQL Server を実行します。

    > [!NOTE]
    > If you choose to run a paid edition of SQL Server then you need to bring your own license (BYOL)

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Linux AMI を作成するには、少なくとも 2 gb のマーケットプ レースからメモリ 
    * [RHEL 7.3+](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  接続と AMI ssh
1.  選択した Linux ディストリビューションのクイック スタートに従います。 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  リモート接続を構成します。 
    * 開く、 [Amazon EC2 コンソール]( https://console.aws.amazon.com/ec2/)
    * ナビゲーション ウィンドウで、次のように選択します。**セキュリティ グループ**です。 
    * 選択**受信、編集、規則の追加**
    * SQL Server がリッスンする (既定の TCP ポートは 1433) ポートでトラフィックを許可する受信規則を追加します。

    
## <a name="digital-ocean"></a>デジタル オーシャン
1. ログインに、[コントロール パネルの [](https://cloud.digitalocean.com/login)ドロップレットの作成] をクリック
1. 少なくとも 2 GB のメモリと Ubuntu 16.04 ドロップレットを選択します。
1. 接続とドロップレット ssh
1. 以下の[Ubuntu のクイック スタート](quickstart-install-connect-ubuntu.md)
1. リモート接続を構成します。
    * コントロール パネルの上部には、以下の**ネットワーク**リンクし、**ファイアウォール**
    * SQL Server がリッスンする (既定の TCP ポートは 1433) ポートでトラフィックを許可する受信規則を追加します。
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Linux イメージには、少なくとも 2 GB のクラウド ランチャーからメモリを作成します。 
    * [RHEL 7.3+](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP2](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  接続のイメージに ssh
1.  選択した Linux ディストリビューションのクイック スタートに従います。 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  リモート接続を構成します。 
    * 移動して、[ファイアウォール規則](https://console.cloud.google.com/networking/firewalls)
    * SQL Server がリッスンするポートのトラフィックを許可する受信の規則の追加 (既定の tcp: 1433)
