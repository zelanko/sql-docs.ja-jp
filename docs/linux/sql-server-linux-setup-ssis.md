---
title: "Linux 上の SQL Server Integration Services のインストール |Microsoft ドキュメント"
description: "このトピックでは、Linux に SQL Server Integration Services (SSIS) をインストールする方法について説明します。"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: cd81ffd71eb78a553703fc31650a0e60a8c513aa
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="install-sql-server-integration-services-ssis-on-linux"></a>Linux 上の SQL Server Integration Services (SSIS) のインストールします。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server Integration Services をインストールするには、この記事の手順に従います (`mssql-server-is`) on Linux です。 Linux 用の Integration Services のこのリリースでサポートされる機能については、次を参照してください。、 [Release Notes](sql-server-linux-release-notes.md)です。

お使いのプラットフォームを SQL Server の統合のサーバーをインストールします。

- [Ubuntu](#ubuntu)
- [Red Hat Enterprise Linux](#RHEL)

## <a name="ubuntu"></a>Ubuntu で SSIS をインストールします。
インストールする、 `mssql-server-is` Ubuntu でパッケージ化、これらの手順に従います。

1. パブリック リポジトリ鍵キーをインポートします。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Microsoft SQL Server Ubuntu リポジトリを登録します。

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

3. SQL Server Integration Services をインストールする次のコマンドを実行します。

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server-is
   ```

4. Integration Services をインストールすると、実行`ssis-conf`です。 詳細については、次を参照してください。 [ssis conf Linux での構成の SSIS](sql-server-linux-configure-ssis.md)です。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

5. 構成が完了したら、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新します。
既に存在する場合`mssql-server-is`インストールされている、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo apt-get install mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除します。
削除する`mssql-server-is`、次のコマンドを実行することができます。
```bash
sudo apt-get remove msssql-server-is
```

## <a name="RHEL"></a>RHEL に SSIS をインストールします。
インストールする、 `mssql-server-is` RHEL にパッケージ化、これらの手順に従います。

1. Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

1. SQL Server Integration Services をインストールする次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server-is
   ```


1. インストールが完了したら実行`ssis-conf`です。 詳細については、次を参照してください。 [ssis conf Linux での構成の SSIS](sql-server-linux-configure-ssis.md)です。

   ```bash
   sudo /opt/ssis/bin/ssis-conf setup
   ```

1. 構成を完了すると、パスを設定します。

   ```bash
   export PATH=/opt/ssis/bin:$PATH
   ```

### <a name="update-ssis"></a>SSIS を更新します。
既に存在する場合`mssql-server-is`インストールされている、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo yum update mssql-server-is
```

### <a name="remove-ssis"></a>SSIS を削除します。
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
