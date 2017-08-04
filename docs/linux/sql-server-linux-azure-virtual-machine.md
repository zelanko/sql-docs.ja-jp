---
title: "Linux の SQL Server で、Azure VM をプロビジョニング |Microsoft ドキュメント"
description: "このチュートリアルでは、Azure で SQL Server 2017 年 Linux 仮想マシンを作成する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 222e23b2-51e7-429b-b8e5-61e0ebe7df9b
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 0470622b0fe5a8835213617a4fc2e8c74f674873
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-linux-sql-server-2017-virtual-machine-with-the-azure-portal"></a>Azure ポータルで SQL Server 2017 年 Linux 仮想マシンを作成します。
Azure では、インストールされている SQL Server 2017 RC2 のある Linux 仮想マシン イメージを提供します。 このトピックでは、Azure ポータルを使用して、SQL Server の Linux 仮想マシンを作成する方法の短いチュートリアルを提供します。 

## <a name="create-a-linux-vm-with-sql-server-installed"></a>インストールされている SQL Server と Linux VM を作成します。

開く、 [Azure ポータル](https://portal.azure.com/)です。

1. をクリックして**新規**左側です。

1. **新規**ブレードで、をクリックして**コンピューティング**です。

1. をクリックして**すべてを参照してください** の横に、**アプリの機能を備えた**見出し。

   ![すべての VM イメージを参照してください。](./media/sql-server-linux-azure-virtual-machine/azure-compute-blade.png)

1. [検索] ボックスに入力**SQL Server 2017**、キーを押します**Enter**検索を開始します。

    ![SQL Server 2017 VM イメージの検索フィルター](./media/sql-server-linux-azure-virtual-machine/searchfilter.png)

    > [!TIP]
    > このフィルターは、SQL Server 2017 の使用の Linux 仮想マシン イメージを表示します。 時間の経過と共に他のサポートされている Linux ディストリビューションの SQL Server 2017 イメージが表示されます。 これをクリックすることもできます[リンク](https://ms.portal.azure.com/#blade/Microsoft_Azure_Marketplace/GalleryFeaturedMenuItemBlade/selectedMenuItemId/home/searchQuery/sql%20server%202017)SQL Server 2017 について検索結果に直接移動します。 

1. 検索結果から、SQL Server 2017 イメージを選択します。

1. **[作成]**をクリックします。

1. **の基礎**ブレードで、Linux VM の詳細に入力します。 

    ![基本ブレード](./media/sql-server-linux-azure-virtual-machine/basics.png)

    > [!Note]
    > ように SSH 公開キーまたはパスワード認証の使用を選択します。 SSH の方が安全です。 SSH キーを生成する方法については、次を参照してください。[作成 SSH キー Linux、Mac 上で、Azure Linux Vm の](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-mac-create-ssh-keys)します。 

1. **[OK]**をクリックします。

1. **サイズ**ブレードで、マシンのサイズを選択します。 開発と機能テストは、ことをお勧めの VM サイズ**DS2**またはそれ以降。 テストのパフォーマンス、使用して**DS13**またはそれ以降。

    ![VM サイズを選択します](./media/sql-server-linux-azure-virtual-machine/vmsizes.png)

    その他のサイズを表示するには、次のように選択します。**をすべて表示**です。 マシンの VM サイズの詳細については、次を参照してください。 [Linux VM のサイズ](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-sizes)です。

1. **[選択]**をクリックします。

1. **設定**ブレードで、設定を変更したり、既定の設定を保持します。

1. **[OK]**をクリックします。

1. **概要** ページで、をクリックして**OK** VM を作成します。

> [!NOTE]
> Azure の仮想マシンは、リモート接続の SQL Server のポート 1433 を開くようにファイアウォールを事前構成します。 リモートで接続する場合もする必要しますが、あります、次のセクションの説明に従って、ネットワーク セキュリティ グループ ルールを追加します。

## <a id="remote"></a>リモート接続を構成します。

Azure VM 上の SQL Server にリモート接続できるようにするには、ネットワーク セキュリティ グループの受信の規則を構成する必要があります。 このルールは、SQL Server がリッスンする (既定の 1433) ポートでトラフィックを許可します。 次の手順では、この手順の Azure ポータルを使用する方法を示します。 

1. ポータルで、次のように選択します。**仮想マシン**、し、SQL Server VM を選択します。

1. プロパティの一覧で選択**ネットワーク インターフェイス**です。

1. VM のネットワーク インターフェイスを選択します。

    ![ネットワーク インターフェイス](./media/sql-server-linux-azure-virtual-machine/networkinterfaces.png)

1. ネットワーク セキュリティ グループのリンクをクリックします。

    ![ネットワーク セキュリティ グループ](./media/sql-server-linux-azure-virtual-machine/networksecuritygroup.png)

1. ネットワーク セキュリティ グループ、selct のプロパティで**受信のセキュリティ規則**です。

1. クリックして、 **+ 追加**ボタンをクリックします。

1. "SQLServerRemoteConnections"の名前を指定します。

1. **サービス**一覧で、 **MS SQL**です。

    ![MS SQL セキュリティ グループ ルール](./media/sql-server-linux-azure-virtual-machine/sqlnsgrule.png)

1. をクリックして**OK** VM のルールを保存します。

## <a id="connect"></a>Linux VM に接続します。

BASH シェルを既に使用している場合に Azure VM を使用して、接続、 **ssh**コマンド。 次のコマンドでは、VM ユーザー名と、Linux VM に接続する IP アドレスを置き換えます。

```bash
ssh -l AzureAdmin 100.55.555.555
```

Azure ポータルで VM の IP アドレスを見つけることができます。

![Azure ポータルで IP アドレス](./media/sql-server-linux-azure-virtual-machine/vmproperties.png)

Windows で実行されており、BASH シェルを持っていない場合は、PuTTY などの SSH クライアントをインストールすることができます。

1. [ダウンロードしてインストール PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)です。

1. PuTTY を実行します。

1. [PuTTY の構成] 画面で、仮想マシンのパブリック IP アドレスを入力します。

1. [開く] をクリックし、ユーザー名とパスワードのプロンプトでを入力します。

Linux Vm への接続に関する詳細については、次を参照してください。[ポータルを使用して Azure での Linux VM の作成](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-quick-create-portal#ssh-to-the-vm)です。

## <a name="configure-sql-server"></a>SQL Server を構成します。

1. Linux VM に接続すると、新しいコマンド ターミナルを開きます。

1. 次のコマンドでは、SQL Server を設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup 
   ```

   ライセンスに同意し、システム管理者アカウントのパスワードを入力します。 表示されたら、サーバーを開始することができます。

1. 必要に応じて、 [SQL Server ツールのインストール](sql-server-linux-setup-tools.md)です。

## <a name="next-steps"></a>次の手順

ローカルに接続することができますを Azure で SQL Server 2017 仮想マシンをしたら**sqlcmd** TRANSACT-SQL クエリを実行します。

SQL Server のリモート接続用に Azure VM を構成した場合もリモートで接続できる必要があります。 リモートの Windows コンピューターから Linux に SQL Server への接続の例は、次を参照してください。 [on Linux に SQL Server への接続に Windows を使用して SSMS](sql-server-linux-develop-use-ssms.md)です。

Azure 内の Linux 仮想マシンの概要については、次を参照してください。、 [Linux 仮想マシンのマニュアル](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/)です。

