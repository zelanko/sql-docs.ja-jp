---
title: "Linux 上の SQL Server 2017 年 1 のインストール |Microsoft ドキュメント"
description: "インストール、更新、および Linux に SQL Server をアンインストールします。 このトピックでは、オンライン、オフライン、および無人のシナリオについて説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: c5bd1be5cbe08e9454b1640d9dd58584aa54955f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>Linux 上の SQL Server のインストールのガイダンス

このトピックでは、インストール、更新、および Linux に SQL Server 2017 をアンインストールする方法について説明します。 Red Hat Enterprise Linux (RHEL)、SUSE Linux Enterprise Server (SLES)、および Ubuntu では、SQL Server 2017 RC2 をサポートします。 Linux または Docker を Windows/ファルダ上の Docker エンジンで実行できる、Docker のイメージとして使用

> [!TIP]
> 手始めに、用のクイック スタート チュートリアルのいずれかにジャンプ[RHEL](quickstart-install-connect-red-hat.md)、 [SLES](quickstart-install-connect-suse.md)、 [Ubuntu](quickstart-install-connect-ubuntu.md)、または[Docker](quickstart-install-connect-docker.md)です。

## <a id="supportedplatforms"></a>サポートされているプラットフォーム

SQL Server 2017 は次の Linux プラットフォームでサポートされています。

| プラットフォーム | サポートされているバージョン | 取得
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [RHEL 7.3 を取得します。](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [SLES v12 SP2 を入手します。](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [Ubuntu 16.04 を取得します。](http://www.ubuntu.com/download/server)
| **Docker エンジン** | 1.8+ | [Docker を取得します。](http://www.docker.com/products/overview)

## <a id="system"></a>システム要件

SQL Server 2017 では、Linux の次のシステム要件があります。

|||
|-----|-----|
| **[メモリ]** | 3.25 GB |
| **ファイル システム** | **XFS**または**EXT4** (その他のファイル システム**BTRFS**、サポートされていません) |
| **ディスク領域** | 6 GB |
| **プロセッサ速度** | 2 GHz |
| **プロセッサ コア** | 2 コア |
| **プロセッサの種類** | x64 と互換性のあるのみ |

> [!NOTE]
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

## <a id="platforms"></a> SQL Server のインストール

コマンドラインから Linux に SQL Server をインストールできます。 手順については、次のクイック スタート チュートリアルのいずれかを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)

## <a id="upgrade"></a>SQL Server をアップグレードします。

アップグレードする、 **mssql サーバー** Linux でパッケージ化、プラットフォームに基づく次のコマンドのいずれかを使用します。

| プラットフォーム | パッケージの更新コマンド |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

これらのコマンドは、最新のパッケージをダウンロードし、下にあるバイナリ ファイルを置き換える`/opt/mssql/`です。 ユーザーがデータベースを生成し、システム データベースは、この操作には影響しません。

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

## <a id="unattended"></a>無人インストール

次のように、無人インストールを実行できます。

- 最初の手順に従って、[のクイック スタート チュートリアル](#platforms)リポジトリを登録し、SQL Server をインストールします。
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

かどうか、Linux コンピューターがアクセスできないで使用されるオンライン リポジトリに、[クイック スタート](#platforms)、パッケージ ファイルを直接ダウンロードできます。 これらのパッケージが Microsoft リポジトリ内にある[https://packages.microsoft.com](https://packages.microsoft.com)です。

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

データベースの作成および管理を開始するように SQL Server インスタンスに接続します。 開始するには、クイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)

