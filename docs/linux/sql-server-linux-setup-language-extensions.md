---
title: Linux 上の SQL Server マシン言語拡張機能 (Java) のインストール |Microsoft Docs
description: Red Hat、Ubuntu、SUSE には、SQL Server の言語拡張機能 (Java) をインストールする方法をについて説明します。
author: dphansen
ms.author: davidph
manager: cgronlun
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d25739fb4f2ef104ba86c8e9124162e67fd8553
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65995080"
---
# <a name="install-sql-server-2019-language-extensions-java-on-linux"></a>Linux 上の SQL Server 2019 言語拡張機能 (Java) のインストールします。

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md)以降の SQL Server 2019 このプレビュー リリースでは Linux オペレーティング システム上で動作します。 Java 言語の拡張機能をインストールするには、この記事の手順に従います。 

言語拡張機能は、データベース エンジンへのアドオンです。 できますが、[データベース エンジンと言語の拡張機能を同時にインストール](#install-all)、インストールしてより多くのコンポーネントを追加する前に、問題を解決できるように、まず、SQL Server データベース エンジンを構成することをお勧めします。 

Java 拡張機能パッケージの場所は、SQL Server Linux ソース リポジトリでいます。 データベース エンジンのインストールのソース リポジトリが既に構成されている場合は実行できます、 **mssql server extensibility java**同じリポジトリの登録を使用して、インストール コマンドをパッケージ化します。

言語拡張機能は、Linux コンテナーでもサポートされます。 言語拡張機能の構築済みのコンテナーは提供されませんを使用して SQL Server のコンテナーから 1 つを作成することができます、 [GitHub で入手できるテンプレートの例](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices)します。

## <a name="uninstall-previous-ctp"></a>以前の CTP をアンインストールします。

パッケージ一覧は、最近 CTP のリリース、結果としてパッケージ数が少ない経由で変更されました。 CTP をアンインストールすることをお勧めします。 2.x CTP 3.0 をインストールする前に、前のすべてのパッケージを削除します。 複数のバージョンのサイド バイ サイドでインストールがサポートされていません。

### <a name="1-confirm-package-installation"></a>1.パッケージのインストールを確認します。

最初の手順として以前のインストールの有無を確認することがあります。 次のファイルは、既存のインストールを示す: checkinstallextensibility.sh、exthost、スタート パッド。

```bash
ls /opt/microsoft/mssql/bin
```

### <a name="2-uninstall-previous-ctp-2x-packages"></a>2.以前の CTP 2.x のパッケージをアンインストールします。

最小のパッケージ レベルでアンインストールします。 下位レベルのパッケージに依存するすべてのアップ ストリーム パッケージが自動的にアンインストールされます。

  + Java 統合の場合は、削除**mssql server extensibility java**

パッケージを削除するためのコマンドは、次の表に表示されます。

| プラットフォーム  | パッケージの削除コマンド | 
|-----------|----------------------------|
| RHEL  | `sudo yum remove msssql-server-extensibility-java` |
| SLES  | `sudo zypper remove msssql-server-extensibility-java` |
| Ubuntu    | `sudo apt-get remove msssql-server-extensibility-java`|

### <a name="3-proceed-with-ctp-30-install"></a>3.CTP 3.0 のインストールを続行します。

この記事の手順を使用して、オペレーティング システムの最上位のパッケージ レベルでインストールします。

各 OS 固有のインストール手順については、一連の*最上位のパッケージ レベル*か**例 1 - フル インストール**、パッケージの完全なセットまたは**例 2 - 最小限のインストール**最小限の数の実行可能なインストールに必要なパッケージです。

1. パッケージ マネージャーと構文を使用して、Linux ディストリビューションのインストール コマンドを実行します。 

   + [RedHat](#RHEL)
   + [Ubuntu](#ubuntu)
   + [SUSE](#suse)

## <a name="prerequisites"></a>前提条件

+ Linux バージョンである必要があります[SQL Server でサポートされている](sql-server-linux-release-notes-2019.md#supported-platforms)、Docker エンジンは含まれません。 サポートされているバージョンは次のとおりです。

   + [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ T-SQL コマンドを実行するためのツールが必要です。 クエリ エディターは、インストール後の構成と検証の必要があります。 お勧め[Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download?view=sql-server-2017#get-azure-data-studio-for-linux)Linux で実行されている無料でダウンロードします。

## <a name="package-list"></a>パッケージの一覧

インターネットに接続されたデバイスで、パッケージがダウンロードされ、各オペレーティング システム、パッケージ インストーラーを使用して、データベース エンジンとは別にインストールされています。 次の表では、すべての利用可能なパッケージについて説明します。

| パッケージ名 | 適用先 | 説明 |
|--------------|----------|-------------|
|mssql-server-extensibility  | すべての言語 | 機能拡張フレームワークを Java コードを実行するために使用します。 |
|mssql-server-extensibility-java | Java | Java の実行環境を読み込むための Java 拡張機能。 その他のライブラリや Java のパッケージはありません。 |

<a name="RHEL"></a>

## <a name="install-language-extensions"></a>言語拡張機能をインストールします。

言語の拡張機能と Java Linux のインストールでインストールできます**mssql server extensibility java**します。 インストールするときに**mssql server extensibility java**がインストールされていない場合に、パッケージが JRE 8 に自動的にインストールされます。 JVM のパスは、という JRE_HOME 環境変数にそれも追加されます。

> [!Note]
> インターネットに接続されたサーバーでパッケージの依存関係がダウンロードされ、メイン パッケージのインストールの一部としてインストールします。 サーバーがインターネットに接続されていない場合は、詳細についてを参照してください、[オフライン セットアップ](#offline-install)します。

### <a name="redhat-install-command"></a>RedHat インストール コマンド

次のコマンドを使用して red Hat には、java 言語の拡張機能をインストールできます。

> [!Tip]
> 実行可能であれば、`yum clean all`をインストールする前に、システム上のパッケージを更新します。

```bash
# Install as root or sudo
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

### <a name="ubuntu-install-command"></a>Ubuntu のインストール コマンド

Java 用の言語拡張機能は、次のコマンドを使用して、Ubuntu をインストールできます。

> [!Tip]
> 実行可能であれば、`apt-get update`をインストールする前に、システム上のパッケージを更新します。 さらに、Ubuntu のいくつかの docker イメージでは、https の apt トランスポート オプションがあります。 これをインストールするには使用`apt-get install apt-transport-https`します。

```bash
# Install as root or sudo
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

### <a name="suse-install-command"></a>SUSE のインストール コマンド

次のコマンドを使用した SUSE での Java 言語の拡張機能をインストールできます。

```bash
# Install as root or sudo
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>インストール後の構成 (必須)

1. Linux 上のアクセス許可の付与

    外部ライブラリを使用している場合は、この手順を実行する必要はありません。 作業に推奨される方法は、外部ライブラリを使用しています。 Jar ファイルから外部ライブラリの作成については、次を参照してください[CREATE EXTERNAL LIBRARY。](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

    外部ライブラリを使用していない場合は、jar で Java クラスを実行するアクセス許可を持つ SQL Server を指定する必要があります。

    読み取りを許可し、jar ファイルへのアクセスを実行するには、次を実行**chmod** jar ファイルをコマンド。 常に SQL Server を使用する場合、クラス ファイルを jar に配置することをお勧めします。 Jar の作成については、次を参照してください。 [jar ファイルを作成する方法](https://docs.microsoft.com/sql/language-extensions/how-to/create-a-java-jar-file-from-class-files)します。

    ```cmd
    chmod ug+rx <MyJarFile.jar>
    ```

    Jar ファイルを読み取り/実行 mssql_satellite アクセス許可を付与する必要があります。

    ```cmd
    chown mssql_satellite:mssql_satellite <MyJarFile.jar>
    ```

    追加の構成は、主に、 [mssql-conf ツール](sql-server-linux-configure-mssql-conf.md)します。

2. SQL Server サービスを実行するために使用する mssql ユーザー アカウントを追加します。 以前のセットアップを実行していない場合に必要です。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

3. 発信ネットワーク アクセスを有効にします。 既定では、発信ネットワーク アクセスが無効です。 送信要求を有効にするには、"outboundnetworkaccess"mssql-conf ツールを使用してブール型プロパティを設定します。 詳細については、次を参照してください。 [mssql-conf での Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md#mlservices-outbound-access)します。

   ```bash
   # Run as SUDO or root
   # Enable outbound requests over the network
   sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1
   ```

4. SQL Server スタート パッド サービスと、INI ファイルの更新された値を読み取るデータベース エンジンのインスタンスを再起動します。 再起動のメッセージを通知する、拡張機能に関連する設定を変更するたびにします。  

   ```bash
   systemctl restart mssql-launchpadd

   systemctl restart mssql-server.service
   ```

5. Azure Data Studio または SQL Server Management Studio (Windows のみ) などの別のツールを使用して外部スクリプトの実行を有効にする Transact SQL を実行します。

   ```bash
   EXEC sp_configure 'external scripts enabled', 1
   RECONFIGURE WITH OVERRIDE
   ```

6. 再起動、`mssql-launchpadd`もう一度サービスを提供します。

## <a name="verify-installation"></a>インストールの確認

Java と機能の統合は、ライブラリは含まれませんが、実行することができます`grep -r JRE_HOME /etc`JAVA_HOME 環境変数の作成を確定します。

インストールの検証、システムを実行する T-SQL スクリプトの実行をストアド プロシージャの Java の呼び出し。 このタスクは、クエリ ツールを必要があります。 Azure Data Studio をお勧めします。 その他のよく使用されるツールは、SQL Server Management Studio や PowerShell など Windows 専用です。 これらのツールを Windows コンピューターがある場合は、データベース エンジンの Linux インストールへの接続に使用します。

<a name="install-all"></a>

## <a name="full-install-of-sql-server-and-language-extensions"></a>SQL Server および言語拡張機能のフル インストール

インストールして、Java のパッケージとデータベース エンジンをインストールするコマンドのパラメーターを追加して、1 つの手順で、データベース エンジンと Machine Learning サービスを構成します。

1. データベース エンジン、および言語拡張機能が含まれるコマンドラインを提供します。

  Java のデータベース エンジンへの拡張機能のインストールに追加できます。

  ```bash
  sudo yum install -y mssql-server mssql-server-extensibility-java 
  ```

3. ライセンス契約に同意し、インストール後の構成を完了します。 使用して、 **mssql conf**このタスクのためのツール。

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

  データベース エンジンのライセンス契約に同意し、エディションを選択して、管理者パスワードを設定するメッセージが表示されます。 

4. サービスを再起動するように求められた場合。

  ```bash
  sudo systemctl restart mssql-server.service
  ```

## <a name="unattended-installation"></a>無人インストール

使用して、[無人インストール](https://docs.microsoft.com/sql/linux/sql-server-linux-setup#unattended)データベース エンジン、mssql server extensibility java のパッケージを追加します。

<a name="offline-install"></a>


## <a name="offline-installation"></a>オフライン インストール

に従って、[オフライン インストール](sql-server-linux-setup.md#offline)パッケージをインストールする方法の手順を実行します。 ダウンロード サイトを見つけて、以下のパッケージの一覧を使用して特定のパッケージをダウンロードします。

> [!Tip]
> パッケージの管理ツールのいくつか提供するのに役立つコマンドは、パッケージの依存関係を判断します。 Yum を使用して`sudo yum deplist [package]`します。 使用して、ubuntu、`sudo apt-get install --reinstall --download-only [package name]`続けて`dpkg -I [package name].deb`します。

#### <a name="download-site"></a>ダウンロード サイト

パッケージをダウンロードする[ https://packages.microsoft.com/](https://packages.microsoft.com/)します。 すべての Java のパッケージは、データベース エンジンのパッケージと同じ場所にします。 

#### <a name="redhat7-paths"></a>Red Hat 7/パス

|||
|--|----|
| mssql/機能拡張-java パッケージ | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |

#### <a name="ubuntu1604-paths"></a>Ubuntu 16.04/パス

|||
|--|----|
| mssql/機能拡張-java パッケージ | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |

#### <a name="suse12-paths"></a>SUSE 12/パス

|||
|--|----|
| mssql/機能拡張-java パッケージ | [https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |

#### <a name="package-list"></a>パッケージの一覧

どの拡張機能によってを使用するには、特定の言語のために必要なパッケージをダウンロードします。 正確なファイル名は、サフィックスにプラットフォームの情報を含めるが、次のファイル名を取得するファイルを決定するための十分にする必要があります。

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000
```

## <a name="limitations-in-ctp-releases"></a>CTP のリリースでの制限事項

Linux 上の言語拡張機能と Java の拡張機能では、まだアクティブな開発中です。 次の機能はプレビュー バージョンではまだ使用できません。

+ 暗黙の認証は現在 Linux で使用可能なデータまたはその他のリソースにアクセスする実行中の Java からサーバーに接続することはできませんが、現時点で。


### <a name="resource-governance"></a>リソース ガバナンス

Linux および Windows の間の類似性がある[リソース ガバナンス](../t-sql/statements/create-external-resource-pool-transact-sql.md)の外部リソース プールの統計情報は[sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md)が現在Linux 上のさまざまな単位です。 ユニットは、今後の CTP で揃います。
 
| 列名   | 説明 | Linux 上の値 | 
|---------------|--------------|---------------|
|peak_memory_kb | 最大リソース プールに使用されるメモリ量。 | Linux では、この統計は、値が memory.max_usage_in_bytes CGroups メモリ サブシステムからソースします。 |
|write_io_count | IOs のリソース ガバナー統計がリセットされた後に発行された書き込みの合計。 | Linux では、この統計は、書き込みの行に値が blkio.throttle.io_serviced CGroups blkio サブシステムからソースします。 | 
|read_io_count | 読み取りリソース ガバナー統計がリセットされた後に発行された Io の合計。 | Linux では、この統計情報は読み取り行の値が blkio.throttle.io_serviced は、CGroups blkio サブシステムからソースします。 | 
|total_cpu_kernel_ms | 累積的な CPU ユーザー カーネル時間 (リソース ガバナー統計がリセットされた後のミリ秒単位)。 | Linux では、この統計は、ユーザーの行に値が cpuacct.stat CGroups cpuacct サブシステムからソースします。 |  
|total_cpu_user_ms | リソース ガバナー統計がリセットされた後のミリ秒単位で累積的な CPU ユーザー時間。| Linux では、この統計は、システムの行の値に値が cpuacct.stat は、CGroups cpuacct サブシステムからソースします。 | 
|active_processes_count | 要求の時点で実行されている外部プロセスの数。| Linux では、この統計は、値が pids.current GGroups pid サブシステムからソースします。 | 

## <a name="next-steps"></a>次のステップ

Java 開発者は、簡単な例で作業を開始し、SQL Server での Java のしくみの基礎について説明します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: Java での正規表現の使用](../language-extensions/tutorials/search-for-string-using-regular-expressions-in-java.md)