---
title: "Linux 上の SQL Server 2017 年 1 のインストール |Microsoft ドキュメント"
description: "インストール、更新、および Linux に SQL Server をアンインストールします。 このトピックでは、オンライン、オフライン、および無人のシナリオについて説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.workload: Active
ms.openlocfilehash: 180c8492531da7c3b9c15ebef28917b52e0869ce
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Linux 上の SQL Server のインストールのガイダンス

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックでは、インストール、更新、および Linux に SQL Server 2017 をアンインストールする方法について説明します。 Red Hat Enterprise Linux (RHEL)、SUSE Linux Enterprise Server (SLES)、および Ubuntu では、SQL Server 2017 をサポートします。 Linux または Docker を Windows/ファルダ上の Docker エンジンで実行できる、Docker のイメージとして使用

> [!TIP]
> 手始めのクイック スタートのいずれかにジャンプ[RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、 [Ubuntu](quickstart-install-connect-ubuntu.md)、または[Docker](quickstart-install-connect-docker.md)です。

## <a id="supportedplatforms"></a>サポートされているプラットフォーム

SQL Server 2017 は次の Linux プラットフォームでサポートされています。

| プラットフォーム | サポートされているバージョン | 取得
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 または 7.4 | [RHEL 7.4 を取得します。](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2 を入手します。](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ubuntu 16.04 を取得します。](http://www.ubuntu.com/download/server)
| **Docker エンジン** | 1.8+ | [Docker を取得します。](http://www.docker.com/products/overview)

Microsoft を展開して、OpenShift と Kubernetes を使用して SQL Server のコンテナーの管理をサポートします。

SQL Server 2017 の最新のサポート ポリシーで、次を参照してください。 [for Microsoft SQL Server の技術的なサポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)です。

## <a id="system"></a>システム要件

SQL Server 2017 では、Linux の次のシステム要件があります。

|||
|-----|-----|
| **[メモリ]** | 2 GB |
| **[ファイル システム]** | **XFS**または**EXT4** (その他のファイル システム**BTRFS**、サポートされていません) |
| **ディスク領域** | 6 GB |
| **プロセッサ速度** | 2 GHz |
| **プロセッサ コア** | 2 コア |
| **プロセッサの種類** | x64 と互換性のあるのみ |

使用する場合**Network File System (NFS)** 、実稼働環境でのリモートの共有は、次のサポート要件を注意してください。

- 使用して NFS version **4.2 以上**です。 NFS の古いバージョンでは、スパース ファイルの作成、最新のファイル システムに共通 fallocate など、必要な機能はできません。
- のみを検索、 **/var/opt/mssql** NFS マウント上のディレクトリ。 SQL Server システム バイナリなどその他のファイルはサポートされていません。
- NFS クライアントが、そのリモート共有をマウントするときに、'nolock' オプションを使用することを確認します。

## <a id="platforms"></a> SQL Server のインストール

コマンドラインから Linux に SQL Server をインストールできます。 手順については、次のクイック スタートのいずれかを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="upgrade"></a>SQL Server を更新します。

更新する、 **mssql サーバー**最新のリリースにパッケージ化、プラットフォームに基づく次のコマンドのいずれかを使用します。

| プラットフォーム | パッケージの更新コマンド |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

これらのコマンドは、最新のパッケージをダウンロードし、下にあるバイナリ ファイルを置き換える`/opt/mssql/`です。 ユーザーがデータベースを生成し、システム データベースは、この操作には影響しません。

## <a id="rollback"></a>SQL Server をロールバック

ロールバックまたは SQL Server の以前のリリースにダウン グレードは、次の手順に従います。

1. ダウン グレードする SQL Server パッケージのバージョン番号を識別します。 パッケージの番号の一覧は、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)です。

1. SQL Server の以前のバージョンにダウン グレードします。 次のコマンドで置き換える`<version_number>`いずれかの手順で特定した SQL Server のバージョン番号を持つ。

   | プラットフォーム | パッケージの更新コマンド |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> SQL Server 2017 など、同じメジャー バージョンのリリースにダウン グレードすることのみサポートされます。

## <a id="versioncheck"></a>インストールされている SQL Server のバージョンを確認します。

現在のバージョンと Linux に SQL Server のエディションを確認するには、次の手順を使用します。

1. インストールされていない場合は、インストール、 [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)です。

1. 使用して**sqlcmd** SQL Server のバージョンとエディションを表示する TRANSACT-SQL コマンドを実行します。

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a>SQL Server をアンインストールします。

削除する、 **mssql サーバー** Linux でパッケージ化、プラットフォームに基づく次のコマンドのいずれかを使用します。

| プラットフォーム | パッケージの削除コマンド |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

パッケージを削除しても、生成されたデータベース ファイルは削除されません。 データベース ファイルを削除する場合は、次のコマンドを使用します。

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="repositories"></a>ソース リポジトリを構成します。

インストールまたは SQL Server をアップグレードするときに、構成されている Microsoft リポジトリから SQL Server の最新バージョンを取得します。

### <a name="repository-options"></a>リポジトリのオプション

各配布用のリポジトリの 2 つの主な種類があります。

- **累積的な更新プログラム (CU)**:、累積的な更新プログラム (CU) リポジトリには、そのリリース以降、基本の SQL Server リリースおよびバグの修正や改善用のパッケージが含まれます。 累積的更新プログラムは、SQL Server 2017 などのリリース バージョンに固有です。 正規わかりませんがリリースされます。

- **GDR**: の GDR リポジトリには、そのリリース以降、基本の SQL Server リリースのみ重要な修正プログラムとセキュリティ更新プログラム用のパッケージが含まれています。 これらの更新プログラムは、次の CU リリースにも追加されます。

各 CU および GDR のリリースには、完全な SQL Server パッケージとそのリポジトリの以前のすべての更新が含まれています。 CU リリースに GDR のリリースから更新は、SQL Server 用に構成されているリポジトリを変更することによってサポートされています。 こともできます[ダウン グレード](#rollback)メジャー バージョン内で任意のリリースに (ex: 2017)。 更新 CU から GDR リリースにリリースはサポートされていません。

### <a name="check-your-configured-repository"></a>構成されているリポジトリを確認します。

どのようなリポジトリが構成されていることを確認する場合は、次のプラットフォームに依存する手法を使用します。

| プラットフォーム | 手順 |
|-----|-----|
| RHEL | 1.内のファイルを表示、 **/etc/yum.repos.d**ディレクトリ。`sudo ls /etc/yum.repos.d`<br/>2.など、SQL Server ディレクトリを構成するファイルを探します**mssql server.repo**です。<br/>3.ファイルの内容を出力します。`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4.**名前**プロパティが構成されているリポジトリ。|
| SLES | 1.コマンド `sudo zypper info mssql-server` を実行します。<br/>2.**リポジトリ**プロパティが構成されているリポジトリ。 |
| Ubuntu | 1.コマンド `sudo cat /etc/apt/sources.list` を実行します。<br/>2.Mssql サーバーのパッケージ URL を確認します。 |

リポジトリの URL の末尾は、リポジトリの種類を確認します。

- **mssql サーバー**: プレビュー リポジトリです。
- **mssql サーバー-2017**: CU リポジトリです。
- **mssql サーバー 2017 gdr**: GDR のリポジトリ。

### <a name="change-the-source-repository"></a>ソース リポジトリを変更します。

CU または GDR のリポジトリを構成するのには、次の手順を使用します。

> [!NOTE]
> [クイック スタート](#platforms)CU リポジトリを構成します。 これらのチュートリアルを実行する場合は、引き続き CU リポジトリを使用する次の手順を使用する必要はありません。 次の手順では、構成されているリポジトリを変更するために必要なのみです。

1. 必要に応じて、以前に構成のリポジトリを削除します。

   | プラットフォーム | リポジトリ | リポジトリの削除 コマンド |
   |---|---|---|
   | RHEL | **すべて** | `sudo rm -rf /etc/yum.repos.d/mssql-server.repo` |
   | SLES | **CTP** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
   | | **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
   | | **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|
   | Ubuntu | **CTP** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
   | | **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
   | | **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

1. **Ubuntu のみ**、パブリック リポジトリ鍵キーをインポートします。

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. 新しいリポジトリを構成します。

   | プラットフォーム | リポジトリ | コマンド |
   |-----|-----|-----|
   | RHEL | CU | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
   | RHEL | GDR | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |
   | SLES | CU  | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
   | SLES | GDR | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |
   | Ubuntu | CU | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)" && sudo apt-get update` |
   | Ubuntu | GDR | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)" && sudo apt-get update` |

1. [インストール](#platforms)または[更新](#upgrade)と SQL Server は、新しいリポジトリからパッケージを関連します。

   > [!IMPORTANT]
   > この時点などを使用してインストール チュートリアルのいずれかを選択した場合、[クイック スタート チュートリアル](#platforms)ターゲットのリポジトリを構成したことに注意してください。 チュートリアルではその手順は繰り返されません。 これは、クイック スタート チュートリアル CU リポジトリを使用するために GDR リポジトリを構成する場合に特に当てはまります。

## <a id="unattended"></a>無人インストール

次のように、無人インストールを実行できます。

- 最初の手順に従って、[クイック スタート](#platforms)リポジトリを登録し、SQL Server をインストールします。
- 実行すると`mssql-conf setup`設定、[環境変数](sql-server-linux-configure-environment-variables.md)を使用して、 `-n` (プロンプトは表示されません) オプション。

次の例の構成で SQL Server の Developer edition、 **MSSQL_PID**環境変数。 使用許諾契約も受け入れます (**ACCEPT_EULA**) SA ユーザー パスワードを設定し、(**MSSQL_SA_PASSWORD**)。 `-n`パラメーターは、構成値が環境変数から引き出されます unprompted インストールを実行します。

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

その他のアクションを実行するスクリプトを作成することもできます。 たとえば、他の SQL Server パッケージをインストールする可能性があります。

詳細のサンプル スクリプトは、次の例を参照してください。

- [Red Hat で無人インストール用スクリプト](sample-unattended-install-redhat.md)
- [SUSE 無人インストール用スクリプト](sample-unattended-install-suse.md)
- [Ubuntu 無人インストール用スクリプト](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>オフライン インストール

かどうか、Linux コンピューターがアクセスできないで使用されるオンライン リポジトリに、[クイック スタート](#platforms)、パッケージ ファイルを直接ダウンロードできます。 これらのパッケージは、Microsoft リポジトリ [https://packages.microsoft.com](https://packages.microsoft.com) にあります。

> [!TIP]
> クイック スタートの手順に正常にインストールした場合は、ダウンロードしたり、次のパッケージを手動でインストールする必要はありません。 このセクションでは、オフラインのシナリオでのみです。

1. **パッケージをダウンロードする、データベース エンジンには、プラットフォームの**します。 パッケージのダウンロード リンクが記載されて、パッケージの詳細 セクションの[リリース ノート](sql-server-linux-release-notes.md)です。

1. **Linux コンピューターにダウンロードしたパッケージを移動**です。 パッケージのダウンロードに、別のコンピューターを使用した場合、Linux コンピューターに、パッケージを移動する方法の 1 つはでは、 **scp**コマンド。

1. **データベース エンジンのパッケージをインストール**です。 プラットフォームに基づいて、次のコマンドのいずれかを使用します。 この例では、パッケージのファイル名をダウンロードした正確な名前に置き換えます。

   | プラットフォーム | パッケージの削除 コマンド |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > RPM パッケージ (RHEL、SLES) をインストールすることも、`rpm -ivh`コマンドが、前の表のコマンドを自動的にインストールの依存関係から使用可能なリポジトリが承認された場合。

1. **見つからない依存関係を解決するには**: 見つからない依存関係をこの時点でする必要があります。 それ以外の場合は、この手順をスキップすることができます。 Ubuntu でそれらの依存関係を含む承認済みのリポジトリにアクセスする場合、最も簡単なソリューションを使用して、`apt-get -f install`コマンド。 このコマンドでは、SQL Server のインストールも完了します。 依存関係を手動で調査するには、するには、次のコマンドを使用します。

   | プラットフォーム | 依存関係の一覧表示コマンド |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   見つからない依存関係を解決するには後、mssql サーバー パッケージを再インストールを試みます。

1. **SQL Server セットアップの完了**です。 使用して**mssql conf** SQL Server セットアップを完了します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>次の手順

インストールが完了したら、他の省略可能な SQL Server パッケージをインストールすることもできます。

- [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)
- [SQL Server エージェント](sql-server-linux-setup-sql-agent.md)
- [SQL Server フルテキスト検索](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

データベースの作成および管理を開始するように SQL Server インスタンスに接続します。 開始するには、クイック スタートを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
