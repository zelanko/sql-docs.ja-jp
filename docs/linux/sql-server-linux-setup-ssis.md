---
title: "Linux 上の SQL Server Integration Services のインストール |Microsoft ドキュメント"
description: "このトピックでは、Linux に SQL Server Integration Services をインストールする方法について説明します。"
author: leolimsft
ms.author: lle
manager: craigg
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: integration-services
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3943870ec10b8430ac4819398908c5459a8b03c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Linux 上の SQL Server Integration Services (SSIS) のインストールします。

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

SQL Server Integration Services をインストールするには、この記事の手順に従います (`mssql-server-is`) on Linux です。 Linux 用の Integration Services のこのリリースでサポートされる機能については、次を参照してください。、 [Release Notes](sql-server-linux-release-notes.md)です。

お使いのプラットフォームを SQL Server の統合のサーバーをインストールします。

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)



## <a name="ubuntu"></a>Ubuntu で SSIS をインストールします。
インストールする、 `mssql-server-is` Ubuntu でパッケージ化、これらの手順に従います。


1.  パブリック リポジトリ鍵キーをインポートします。

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```


2.  Microsoft SQL Server Ubuntu リポジトリを登録します。

    ```bash
    curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list | sudo tee /etc/apt/sources.list.d/mssql-server.list
    ```


3.  SQL Server Integration Services をインストールする次のコマンドを実行します。

    ```bash
    sudo apt-get update
    sudo apt-get install -y mssql-server-is
    ```


4.  Integration Services をインストールすると、実行`ssis-conf`です。

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


5.  構成が完了したら、パスを設定します。

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


既に存在する場合`mssql-server-is`インストールされている、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo apt-get install mssql-server-is
```


削除する`mssql-server-is`、次のコマンドを実行することができます。
```bash
sudo apt-get remove msssql-server-is
```



## <a name="RHEL"></a>RHEL に SSIS をインストールします。
インストールする、 `mssql-server-is` RHEL にパッケージ化、これらの手順に従います。


1.  スーパー ユーザーのモードを入力します。

    ```bash
    sudo su
    ```


2.  Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードします。

    ```bash
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
    ```


3.  スーパー ユーザーのモードを終了します。

    ```bash
    exit
    ```


4.  SQL Server Integration Services をインストールする次のコマンドを実行します。

    ```bash
    sudo yum install -y mssql-server-is
    ```


5.  インストールを実行してください。`ssis-conf`です。

    ```bash
    sudo /opt/ssis/bin/ssis-conf setup
    ```


6.  構成を完了すると、パスを設定します。

    ```bash
    export PATH=/opt/ssis/bin:$PATH
    ```


既に存在する場合`mssql-server-is`インストールされている、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo yum update mssql-server-is
```


削除する`mssql-server-is`、次のコマンドを実行することができます。
```bash
sudo yum remove msssql-server-is
```




## <a name="run-a-package"></a>パッケージを実行します。
SSIS パッケージを Linux コンピューターにコピーします。 次のコマンドを使用して、パッケージを実行します。

```bash
dtexec /F <package name> /DE <protection password>
```



## <a name="next-steps"></a>次の手順

Linux 上の SSIS を使用して、抽出、変換、およびデータの読み込みする方法の詳細については、次を参照してください。[抽出、変換、および SQL Server on Linux と SSIS のデータを読み込む](sql-server-linux-migrate-ssis.md)します。
