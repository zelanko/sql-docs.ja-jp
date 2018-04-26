---
title: SQL Server on Linux のリポジトリを構成する |Microsoft ドキュメント
description: 確認し、Linux 上の SQL Server 2017 のソース リポジトリを構成します。 ソース リポジトリでは、インストールとアップグレード中に適用されている SQL Server のバージョンに影響します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: f6983e361ff26f2c6a7e17b1706f414005d38a34
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>インストールして、Linux 上の SQL Server をアップグレードするためのリポジトリを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上の SQL Server 2017 インストールおよびアップグレードの適切なリポジトリを構成する方法について説明します。

> [!IMPORTANT]
> CTP または SQL Server 2017 年 1 の RC バージョンを以前インストールした場合は、一般公開 (GA) リポジトリを登録し、アップグレードまたは再インストールするこの記事で、手順を使用する必要があります。 SQL Server 2017 のプレビュー リリースはサポートされていませんし、期限切れになります。

## <a id="repositories"></a>リポジトリ

Linux に SQL Server をインストールするときは、Microsoft のリポジトリを構成する必要があります。 このリポジトリを使用して、データベース エンジンのパッケージを取得**mssql サーバー**、および SQL Server パッケージの関連します。 現在、次の 3 つの主要なリポジトリがあります。

| リポジトリ | 名前 | Description |
|---|---|---|
| **プレビュー** | **mssql-server** | CTP と RC のリリースの SQL Server のリポジトリをプレビューします。 SQL Server 2017 では、このリポジトリはサポートされていません。 |
| **CU** | **mssql-server-2017** | SQL Server 2017 累積的な更新プログラム (CU) リポジトリ。 |
| **GDR** | **mssql-server-2017-gdr** | 重要な更新プログラムのみの SQL Server 2017 GDR リポジトリ。 |

## <a id="cuversusgdr"></a> GDR と累積更新プログラム

ことが重要の各配布リポジトリの 2 つの主な種類があることに注意してください。

- **累積的な更新プログラム (CU)**:、累積的な更新プログラム (CU) リポジトリには、そのリリース以降、基本の SQL Server リリースおよびバグの修正や改善用のパッケージが含まれます。 累積的更新プログラムは、SQL Server 2017 などのリリース バージョンに固有です。 正規わかりませんがリリースされます。

- **GDR**: の GDR リポジトリには、そのリリース以降、基本の SQL Server リリースのみ重要な修正プログラムとセキュリティ更新プログラム用のパッケージが含まれています。 これらの更新プログラムは、次の CU リリースにも追加されます。

各 CU および GDR のリリースには、完全な SQL Server パッケージとそのリポジトリの以前のすべての更新が含まれています。 CU リリースに GDR のリリースから更新は、SQL Server 用に構成されているリポジトリを変更することによってサポートされています。 こともできます[ダウン グレード](sql-server-linux-setup.md#rollback)メジャー バージョン内で任意のリリースに (ex: 2017)。

> [!NOTE]
> CU GDR のリリースから更新できますリポジトリを変更することでいつでもリリースされます。 更新 CU から GDR リリースにリリースはサポートされていません。 

## <a id="configure"></a> リポジトリを構成します。

次のセクションでは、ことを確認して、次のサポートされているプラットフォームのリポジトリを構成する方法について説明します。

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> RHEL リポジトリを構成します。
Red Hat Enterprise Server (RHEL) でリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-rhel"></a>以前に構成したリポジトリ (RHEL) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 内のファイルを表示、 **/etc/yum.repos.d**ディレクトリが次のコマンド。

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. など、SQL Server ディレクトリを構成するファイルを探します**mssql server.repo**です。

3. ファイルの内容を出力します。

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. **名前**プロパティが構成されているリポジトリ。 テーブルを識別できる、[リポジトリ](#repositories)この記事のセクションです。

### <a name="remove-old-repository-rhel"></a>古いリポジトリ (RHEL) を削除します。
必要に応じて、次のコマンドを使用して古いリポジトリを削除します。

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

このコマンドは、前のセクションで指定されたファイルがという名前の前提としています。 **mssql server.repo**です。

### <a name="configure-new-repository-rhel"></a>新しいリポジトリ (RHEL) を構成します。
SQL Server のインストールとアップグレードに使用する新しいリポジトリを構成します。 任意のリポジトリを構成するのにには、次のコマンドのいずれかを使用します。

| リポジトリ | コマンド |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> SLES リポジトリを構成します。
SLES でリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-sles"></a>以前に構成したリポジトリ (SLES) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 使用して**zypper 情報**すべて以前に構成されたリポジトリに関する情報を取得します。

   ```bash
   sudo zypper info mssql-server
   ```

2. **リポジトリ**プロパティが構成されているリポジトリ。 テーブルを識別できる、[リポジトリ](#repositories)この記事のセクションです。

### <a name="remove-old-repository-sles"></a>古いリポジトリ (SLES) を削除します。
必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>新しいリポジトリ (SLES) を構成します。
SQL Server のインストールとアップグレードに使用する新しいリポジトリを構成します。 任意のリポジトリを構成するのにには、次のコマンドのいずれかを使用します。

| リポジトリ | コマンド |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Ubuntu リポジトリを構成します。
Ubuntu でリポジトリを構成するのにには、次の手順を使用します。

### <a name="check-for-previously-configured-repositories-ubuntu"></a>以前に構成したリポジトリ (Ubuntu) の確認します。
まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

1. 内容を表示、 **/etc/apt/sources.list**ファイル。

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Mssql サーバーのパッケージ URL を確認します。 テーブルを識別できる、[リポジトリ](#repositories)この記事のセクションです。

### <a name="remove-old-repository-ubuntu"></a>古いリポジトリ (Ubuntu) を削除します。
必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>新しいリポジトリ (Ubuntu) を構成します。
SQL Server のインストールとアップグレードに使用する新しいリポジトリを構成します。

1. パブリック リポジトリ鍵キーをインポートします。

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. 任意のリポジトリを構成するのにには、次のコマンドのいずれかを使用します。

   | リポジトリ | コマンド |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. 実行**apt-更新プログラムを取得**です。

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>次の手順

適切なリポジトリを構成した後に進むことができます[インストール](sql-server-linux-setup.md#platforms)または[更新](sql-server-linux-setup.md#upgrade)と SQL Server は、新しいリポジトリからパッケージを関連します。

> [!IMPORTANT]
> この時点などを使用してインストール記事のいずれかを選択した場合、[クイック スタート](sql-server-linux-setup.md#platforms)ターゲットのリポジトリが既に構成されていることに注意してください。 チュートリアルではその手順は繰り返されません。 これは、クイック スタート CU リポジトリを使用するために GDR リポジトリを構成する場合に特に当てはまります。

Linux に SQL Server 2017 をインストールする方法の詳細については、次を参照してください。 [Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。
