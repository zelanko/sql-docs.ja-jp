---
title: SQL Server 2017 と 2019 の Linux のリポジトリを構成する |Microsoft Docs
description: 確認し、SQL Server 2019 と SQL Server 2017 on Linux のソース リポジトリを構成します。 ソース リポジトリでは、インストールとアップグレード中に適用されている SQL Server のバージョンに影響します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 5aee3ea6a744c15afce8055d153959b8db9ac66d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713214"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>インストールして、Linux 上の SQL Server のアップグレードのためのリポジトリを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux での SQL Server 2017 および SQL Server 2019 のインストールとアップグレードのための適切なリポジトリを構成する方法について説明します。

> [!TIP]
> SQL Server 2019 CTP 2.0 は、使用できるようになりました! お試しください、この記事を使用して、新しい構成**mssql-サーバー-プレビュー**リポジトリ。 」の手順に従ってをインストールし、[インストール ガイド](sql-server-linux-setup.md)します。

## <a id="repositories"></a>リポジトリ

Linux 上の SQL Server をインストールするときに、Microsoft リポジトリを構成する必要があります。 このリポジトリを使用して、データベース エンジン パッケージを取得して**mssql server**、および SQL Server パッケージに関連します。 現在は、次の 3 つのメイン リポジトリがあります。

| リポジトリ | 名前 | 説明 |
|---|---|---|
| **プレビュー (2017)** | **mssql-server** | SQL Server 2017 ctp 版と RC リポジトリ (廃止)。 |
| **プレビュー (2019)** | **mssql-サーバー-プレビュー** | SQL Server 2019 ctp 版と RC のリポジトリ。 |
| **CU** | **mssql-server-2017** | SQL Server 2017 Cumulative Update (CU) のリポジトリ。 |
| **GDR** | **mssql-server-2017-gdr** | 重要な更新プログラムのみの SQL Server 2017 の GDR リポジトリ。 |

## <a id="cuversusgdr"></a> GDR ではなく、累積更新プログラム

2 つの主な種類の各ディストリビューションのリポジトリがあることに注意する必要があります。

- **累積的な更新プログラム (CU)**:、累積的な更新プログラム (CU) のリポジトリには、そのリリース以降ベースの SQL Server リリースとバグ修正や改善のパッケージが含まれています。 累積的更新プログラムは、SQL Server 2017 などのリリース バージョンに固有です。 これらは、一定のリズムでリリースされます。

- **GDR**:、GDR リポジトリには、そのリリース以降、基底の SQL Server リリースとのみ重要な修正プログラムとセキュリティ更新プログラム用のパッケージが含まれています。 これらの更新プログラムは、[次へ] の CU リリースにも追加されます。

各 CU と GDR のリリースには、完全な SQL Server パッケージとそのリポジトリの以前の更新プログラムが含まれています。 SQL Server 用に構成されているリポジトリを変更することで、GDR のリリースから CU リリースへの更新はサポートされています。 できます[ダウン グレード](sql-server-linux-setup.md#rollback)メジャー バージョン内の任意のリリースに (例: 2017)。

> [!NOTE]
> CU GDR のリリースから更新することができますのリポジトリを変更することで、いつでもリリースされます。 更新 CU から GDR のリリースのリリースはサポートされていません。 

## <a id="configure"></a> リポジトリを構成します。

次のセクションでは、ことを確認して、次のサポートされているプラットフォームのリポジトリを構成する方法について説明します。

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> RHEL リポジトリを構成します。
Red Hat Enterprise Server (RHEL) のリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-rhel"></a>以前に構成されたリポジトリ (RHEL) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 内のファイルを表示、 **/etc/yum.repos.d**次のコマンドでディレクトリ。

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. など、SQL Server ディレクトリを構成するファイルを探して**mssql server.repo**します。

3. ファイルの内容を出力します。

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. **名前**プロパティが構成されているリポジトリです。 テーブルを識別することができます、[リポジトリ](#repositories)この記事の「します。

### <a name="remove-old-repository-rhel"></a>古いリポジトリ (RHEL) の削除します。
必要に応じて、次のコマンドを使用して古いリポジトリを削除します。

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

このコマンドは、前のセクションで識別されるファイルの名前が前提としています。 **mssql server.repo**します。

### <a name="configure-new-repository-rhel"></a>新しいリポジトリ (RHEL) を構成します。
SQL Server のインストールとアップグレードのために使用する新しいリポジトリを構成します。 次のコマンドのいずれかを使用して、好みのリポジトリを構成します。

| リポジトリ | バージョン | コマンド |
|---|---|---|
| **プレビュー (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> SLES リポジトリを構成します。
SLES でリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-sles"></a>以前に構成されたリポジトリ (SLES) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 使用**zypper 情報**以前に構成された任意のリポジトリに関する情報を取得します。

   ```bash
   sudo zypper info mssql-server
   ```

2. **リポジトリ**プロパティが構成されているリポジトリです。 テーブルを識別することができます、[リポジトリ](#repositories)この記事の「します。

### <a name="remove-old-repository-sles"></a>古いリポジトリ (SLES) の削除します。
必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **プレビュー (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>新しいリポジトリ (SLES) を構成します。
SQL Server のインストールとアップグレードのために使用する新しいリポジトリを構成します。 次のコマンドのいずれかを使用して、好みのリポジトリを構成します。

| リポジトリ | バージョン | コマンド |
|---|---|---|
| **プレビュー (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Ubuntu のリポジトリを構成します。
Ubuntu でリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-ubuntu"></a>以前に構成されたリポジトリ (Ubuntu) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 内容を表示、 **/etc/apt/sources.list**ファイル。

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Mssql server 用のパッケージの URL を確認します。 テーブルを識別することができます、[リポジトリ](#repositories)この記事の「します。

### <a name="remove-old-repository-ubuntu"></a>古いリポジトリ (Ubuntu) を削除します。
必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **プレビュー (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>新しいリポジトリ (Ubuntu) を構成します。
SQL Server のインストールとアップグレードのために使用する新しいリポジトリを構成します。

1. パブリック リポジトリの GPG キーをインポートします。

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. 次のコマンドのいずれかを使用して、好みのリポジトリを構成します。

   | リポジトリ | バージョン | コマンド |
   |---|---|---|
   | **プレビュー (2019)** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. 実行**apt get 更新**します。

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>次の手順

適切なリポジトリを構成した後に進んで[インストール](sql-server-linux-setup.md#platforms)または[更新](sql-server-linux-setup.md#upgrade)および SQL Server は、新しいリポジトリからパッケージを関連します。

> [!IMPORTANT]
> など、インストールの記事のいずれかを使用する場合、この時点で、[クイック スタート](sql-server-linux-setup.md#platforms)ターゲットのリポジトリが既に構成されていることに注意してください。 チュートリアルでは、そのステップを繰り返さないでください。 クイック スタート CU リポジトリを使用するため、GDR リポジトリを構成する場合は特にそうです。

Linux 上の SQL Server 2017 をインストールする方法の詳細については、次を参照してください。 [Linux 上の SQL Server のインストールのガイダンスについて](sql-server-linux-setup.md)します。