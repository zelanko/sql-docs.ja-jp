---
title: Linux 上の SQL Server のインストールのガイダンス |Microsoft Docs
description: インストール、更新、および Linux 上の SQL Server をアンインストールします。 この記事では、オンライン、オフライン、および無人のシナリオについて説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/06/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.openlocfilehash: ce9a2c9956ab4c40c2a5840f65bf8a630fb25065
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713004"
---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Linux 上の SQL Server のインストールのガイダンスについて

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、インストール、更新、および SQL Server 2017 と Linux 上の SQL Server 2019 プレビューをアンインストールするためのガイダンスを提供します。

> [!TIP]
> このガイドには、いくつかの展開シナリオ項目について説明します。 段階的インストール手順だけを検索する場合は、クイック スタートのいずれかに移動します。
> - [RHEL のクイック スタート](quickstart-install-connect-red-hat.md)
> - [SLES のクイック スタート](quickstart-install-connect-suse.md)
> - [Ubuntu のクイック スタート](quickstart-install-connect-ubuntu.md)
> - [Docker クイック スタート](quickstart-install-connect-docker.md)

よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](../linux/sql-server-linux-faq.md)します。

## <a id="supportedplatforms"></a> サポートされているプラットフォーム

SQL Server 2017 は、Red Hat Enterprise Linux (RHEL)、SUSE Linux Enterprise Server (SLES)、および Ubuntu でサポートされます。 また、Linux または Docker for Windows/ファルダ上の Docker エンジンで実行できる Docker イメージとしてサポートされています

| プラットフォーム | サポートされているバージョン | 取得
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 または 7.4 | [RHEL 7.4 を取得します。](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2 を入手します。](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Get Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Docker エンジン** | 1.8+ | [Docker を取得します。](http://www.docker.com/products/overview)

Microsoft を展開して、OpenShift と Kubernetes を使用して SQL Server のコンテナーの管理もサポートしています。

> [!NOTE]
> SQL Server をテストして、上記のディストリビューションの Linux ではサポートされています。 サポートされていないオペレーティング システムに SQL Server をインストールする場合は、確認、**サポート ポリシー**のセクション、 [for Microsoft SQL Server のテクニカル サポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)サポートの理解に影響します。

## <a id="system"></a> システム要件

SQL Server 2017 では、Linux の次のシステム要件があります。

|||
|-----|-----|
| **[メモリ]** | 2 GB |
| **[ファイル システム]** | **XFS**または**EXT4** (他のファイル システムでは、 **BTRFS**はサポートされていません) |
| **ディスク領域** | 6 GB |
| **プロセッサ速度** | 2 GHz |
| **プロセッサ コア** | 2 コア |
| **プロセッサの種類** | x64 互換のみ |

使用する場合**Network File System (NFS)** 、運用環境でのリモート共有には、次のサポート要件に注意してください。

- NFS のバージョンを使用して**4.2 以上**します。 以前のバージョンの NFS は、fallocate スパース ファイルの作成、最新のファイル システムに共通してなどの必要な機能をサポートしません。
- のみを検索、 **/var/opt/mssql** NFS マウント上のディレクトリ。 SQL Server のシステム バイナリなどの他のファイルがサポートされていません。
- NFS クライアントがリモート共有をマウントするときに、'nolock' オプションを使用することを確認します。

## <a id="repositories"></a> ソース リポジトリを構成します。

インストールまたは SQL Server をアップグレードするときは、構成済みの Microsoft リポジトリから最新バージョンの SQL Server を取得します。 クイック スタートを使用して、SQL Server 2017 Cumulative Update **CU**リポジトリ。 代わりに構成することができますが、 **GDR**リポジトリまたは**プレビュー (vNext)** リポジトリ。 リポジトリとその構成方法の詳細については、次を参照してください。[リポジトリを構成する SQL Server on Linux の](sql-server-linux-change-repo.md)します。

> [!IMPORTANT]
> CTP または SQL Server 2017 の RC バージョンを以前インストールした場合は、プレビューのリポジトリを削除する必要があり、一般公開 (GA) 1 つを登録します。 詳細については、次を参照してください。[リポジトリを構成する SQL Server on Linux の](sql-server-linux-change-repo.md)します。

## <a id="platforms"></a> SQL Server 2017 をインストールします。

コマンドラインから Linux 上の SQL Server 2017 をインストールできます。 手順については、次のクイック スタートのいずれかを参照してください。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

## <a id="sqlvnext"></a> SQL Server 2019 preview をインストールします。

SQL Server 2019 プレビューは、前のセクションで、同じのクイック スタートのリンクを使用して Linux にインストールできます。 ただし、登録する必要があります、**プレビュー (vNext)** リポジトリの代わりに、 **CU**リポジトリ。 クイック スタートでは、これを行う方法についてを説明します。  

インストールした後、最適なパフォーマンスの追加の構成の変更を検討してください。 詳細については、次を参照してください。[パフォーマンスのベスト プラクティスと SQL Server on Linux の構成ガイドライン](sql-server-linux-performance-best-practices.md)します。

## <a id="upgrade"></a> SQL Server を更新します。

更新する、 **mssql server**最新リリースにパッケージ化、お使いのプラットフォームに基づく次のコマンドのいずれかを使用します。

| プラットフォーム | パッケージの更新コマンド |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

これらのコマンドは、最新のパッケージをダウンロードし、下にあるバイナリを置き換えます`/opt/mssql/`します。 ユーザー データベースを生成して、システム データベースをこの操作では受けません。

> [!TIP]
> 場合する最初[、構成されているリポジトリを変更する](sql-server-linux-change-repo.md)、可能性があります、**更新**コマンドを SQL Server のバージョンをアップグレードします。 これは、2 つのリポジトリ間でアップグレードのパスがサポートされている場合、大文字と小文字のみです。

## <a id="rollback"></a> SQL Server のロールバック

ロールバックまたは SQL Server の以前のリリースにダウン グレードは、次の手順に従います。

1. ダウン グレードする SQL Server パッケージのバージョン番号を特定します。 パッケージ番号の一覧は、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)します。

1. SQL Server の以前のバージョンにダウン グレードします。 次のコマンドで置き換える`<version_number>`いずれかの手順で特定した SQL Server のバージョン番号。

   | プラットフォーム | パッケージの更新コマンド |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> SQL Server 2017 など、同じメジャー バージョン内でのリリースにダウン グレードすることのみサポートされます。

## <a id="versioncheck"></a> インストールされている SQL Server のバージョンを確認してください。

を、現在のバージョンとエディションの SQL Server on Linux を確認するには、次の手順を使用します。

1. インストールされていない場合は、インストール、 [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)します。

1. 使用**sqlcmd** SQL Server のバージョンとエディションを表示する TRANSACT-SQL コマンドを実行します。

   ```bash
   sqlcmd -S localhost -U SA -Q 'select @@VERSION'
   ```

## <a id="uninstall"></a> SQL Server をアンインストールします。

削除する、 **mssql server** Linux 上のパッケージ、お使いのプラットフォームに基づく次のコマンドのいずれかを使用します。

| プラットフォーム | パッケージの削除コマンド |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

パッケージを削除しても、生成されたデータベース ファイルは削除されません。 データベース ファイルを削除する場合は、次のコマンドを使用します。

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a> 無人インストール

次のように、無人インストールを実行できます。

- 最初の手順に従って、[クイック スタート](#platforms)リポジトリを登録し、SQL Server をインストールします。
- 実行すると`mssql-conf setup`設定[環境変数](sql-server-linux-configure-environment-variables.md)を使用して、 `-n` (プロンプトなし) オプション。

次の例では、構成した SQL Server の Developer edition、 **MSSQL_PID**環境変数。 使用許諾契約書を受け入れます (**ACCEPT_EULA**) および、SA ユーザーのパスワードを設定します (**MSSQL_SA_PASSWORD**)。 `-n`パラメーターは、構成値が環境変数から取得されたプロンプトのインストールを実行します。

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

その他のアクションを実行するスクリプトを作成することもできます。 たとえば、他の SQL Server パッケージをインストールする可能性があります。

詳細なサンプル スクリプトでは、次の例を参照してください。

- [Red Hat の無人インストール スクリプト](sample-unattended-install-redhat.md)
- [SUSE の無人インストール スクリプト](sample-unattended-install-suse.md)
- [Ubuntu の無人インストール スクリプト](sample-unattended-install-ubuntu.md)

## <a id="offline"></a> オフライン インストール

かどうか、Linux コンピューターがアクセスできない、オンラインのリポジトリで使用する、[のクイック スタート](#platforms)、パッケージ ファイルを直接ダウンロードすることができます。 これらのパッケージが、Microsoft リポジトリにある[ https://packages.microsoft.com](https://packages.microsoft.com)します。

> [!TIP]
> クイック スタートの手順で正常にインストールした場合は、ダウンロードしたり手動で SQL Server のパッケージをインストールする必要はありません。 このセクションでは、オフラインのシナリオ専用です。

1. **お使いのプラットフォーム用のデータベース エンジン パッケージ ダウンロード**します。 パッケージの詳細セクションでは、パッケージのダウンロード リンクを検索、[リリース ノート](sql-server-linux-release-notes.md)します。

1. **Linux コンピューターにダウンロードしたパッケージを移動**します。 Linux コンピューターに、パッケージを移動する方法の 1 つは、パッケージをダウンロードする別のコンピューターを使用した場合、 **scp**コマンド。

1. **データベース エンジン パッケージをインストール**します。 お使いのプラットフォームに基づいて、次のコマンドのいずれかを使用します。 この例では、パッケージのファイル名をダウンロードした正確な名前に置き換えます。

   | プラットフォーム | パッケージのインストール コマンド |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > (RHEL および SLES) の RPM パッケージをインストールすることも、`rpm -ivh`コマンドが、前の表のコマンドを自動的にインストールの依存関係から使用可能なリポジトリを承認された場合。

1. **解決するには依存関係がない**: 依存関係をこの時点で不足している必要があります。 それ以外の場合は、この手順をスキップすることができます。 Ubuntu の場合、それらの依存関係を含む承認済みのリポジトリにアクセスする場合、最も簡単なソリューションは、使用する、`apt-get -f install`コマンド。 このコマンドでは、SQL Server のインストールも完了します。 依存関係を手動で検査するには、次のコマンドを使用します。

   | プラットフォーム | 依存関係の一覧表示コマンド |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   不足している依存関係を解決するには後、mssql server パッケージを再インストールを試みます。

1. **SQL Server セットアップを完了**します。 使用**mssql conf** SQL Server セットアップを完了します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="licensing-and-pricing"></a>ライセンスと価格

SQL Server のライセンスは Linux と Windows で同じです。 SQL Server の詳細についてはライセンスと価格を参照してください[SQL Server のライセンス方法](https://www.microsoft.com/sql-server/sql-server-2017-pricing)します。

## <a name="optional-sql-server-features"></a>省略可能な SQL Server の機能

インストール後に、またインストールまたは、省略可能な SQL Server の機能を有効にできます。

- [SQL Server コマンド ライン ツール](sql-server-linux-setup-tools.md)
- [SQL Server エージェント](sql-server-linux-setup-sql-agent.md)
- [SQL Server フルテキスト検索](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services](sql-server-linux-setup-ssis.md)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

> [!TIP]
> よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)します。