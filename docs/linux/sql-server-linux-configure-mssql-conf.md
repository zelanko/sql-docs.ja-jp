---
title: Linux 上の SQL Server の設定を構成します。
description: この記事では、mssql-conf ツールを使用して、Linux 上の SQL Server の設定を構成する方法について説明します。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: 57e43f3afd9c46e3b49e4f1f07ab3038359c8c50
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834005"
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Linux 上の SQL Server を mssql-conf ツールを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

**mssql conf** Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu 用 SQL Server 2017 をインストールする構成スクリプトです。 このユーティリティを使用するには、次のパラメーターを設定します。

|||
|---|---|
| [エージェント](#agent) | SQL Server エージェントを有効にします。 |
| [[照合順序]](#collation) | Linux 上の SQL Server の新しい照合順序を設定します。 |
| [お客様からのフィードバック](#customerfeedback) | SQL Server が Microsoft にフィードバックを送信するかどうかを選択します。 |
| [[データベース メール プロファイル]](#dbmail) | Linux 上の SQL Server の既定のデータベース メール プロファイルを設定します。 |
| [既定のデータ ディレクトリ](#datadir) | 新しい SQL Server データベースのデータ ファイル (.mdf) の既定のディレクトリを変更します。 |
| [既定のログ ディレクトリ](#datadir) | 新しい SQL Server データベースのログ (.ldf) ファイルの既定のディレクトリを変更します。 |
| [既定のマスター データベース ディレクトリ](#masterdatabasedir) | Master データベースとログ ファイルの既定のディレクトリを変更します。|
| [既定の master データベース ファイル名](#masterdatabasename) | Master データベース ファイルの名前を変更します。 |
| [既定のダンプ ディレクトリ](#dumpdir) | 新しいメモリ ダンプおよびその他のトラブルシューティング ファイルの既定のディレクトリを変更します。 |
| [既定のエラー ログ ディレクトリ](#errorlogdir) | 新しい SQL Server エラー ログ、Profiler の既定のトレース、システム正常性セッション XE、および Hekaton セッション XE ファイルの既定のディレクトリを変更します。 |
| [既定のバックアップ ディレクトリ](#backupdir) | 新しいバックアップ ファイルの既定のディレクトリを変更します。 |
| [ダンプの種類](#coredump) | 収集するダンプ メモリ ダンプ ファイルの種類を選択します。 |
| [高可用性](#hadr) | 可用性グループを有効にします。 |
| [Local Audit ディレクトリ](#localaudit) | Local Audit ファイルを追加するディレクトリを設定します。 |
| [ロケール](#lcid) | 使用する SQL Server のロケールを設定します。 |
| [メモリの制限](#memorylimit) | SQL Server のメモリ制限を設定します。 |
| [TCP ポート](#tcpport) | SQL Server が接続をリッスンするポートを変更します。 |
| [TLS](#tls) | トランスポート レベルのセキュリティを構成します。 |
| [トレース フラグ](#traceflags) | サービスが使用しているトレース フラグを設定します。 |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

**mssql conf**と共にインストールされる構成スクリプトは、 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu します。 このユーティリティを使用するには、次のパラメーターを設定します。

|||
|---|---|
| [エージェント](#agent) | SQL Server エージェントを有効にします。 |
| [[照合順序]](#collation) | Linux 上の SQL Server の新しい照合順序を設定します。 |
| [お客様からのフィードバック](#customerfeedback) | SQL Server が Microsoft にフィードバックを送信するかどうかを選択します。 |
| [[データベース メール プロファイル]](#dbmail) | Linux 上の SQL Server の既定のデータベース メール プロファイルを設定します。 |
| [既定のデータ ディレクトリ](#datadir) | 新しい SQL Server データベースのデータ ファイル (.mdf) の既定のディレクトリを変更します。 |
| [既定のログ ディレクトリ](#datadir) | 新しい SQL Server データベースのログ (.ldf) ファイルの既定のディレクトリを変更します。 |
| [既定の master データベース ファイル ディレクトリ](#masterdatabasedir) | 既存の SQL インストール上の master データベース ファイルの既定のディレクトリを変更します。|
| [既定の master データベース ファイル名](#masterdatabasename) | Master データベース ファイルの名前を変更します。 |
| [既定のダンプ ディレクトリ](#dumpdir) | 新しいメモリ ダンプおよびその他のトラブルシューティング ファイルの既定のディレクトリを変更します。 |
| [既定のエラー ログ ディレクトリ](#errorlogdir) | 新しい SQL Server エラー ログ、Profiler の既定のトレース、システム正常性セッション XE、および Hekaton セッション XE ファイルの既定のディレクトリを変更します。 |
| [既定のバックアップ ディレクトリ](#backupdir) | 新しいバックアップ ファイルの既定のディレクトリを変更します。 |
| [ダンプの種類](#coredump) | 収集するダンプ メモリ ダンプ ファイルの種類を選択します。 |
| [高可用性](#hadr) | 可用性グループを有効にします。 |
| [Local Audit ディレクトリ](#localaudit) | Local Audit ファイルを追加するディレクトリを設定します。 |
| [ロケール](#lcid) | 使用する SQL Server のロケールを設定します。 |
| [メモリの制限](#memorylimit) | SQL Server のメモリ制限を設定します。 |
| [Microsoft 分散トランザクション コーディネーター](#msdtc) | 構成し、Linux 上の MSDTC をトラブルシューティングします。 |
| [MLServices Eula](#mlservices-eula) | Mlservices パッケージの R と Python の Eula を受け入れます。 SQL Server 2019 のみに適用されます。|
| [outboundnetworkaccess](#mlservices-outbound-access) |発信ネットワーク アクセスを有効にする[mlservices](sql-server-linux-setup-machine-learning.md) R、Python、および Java の拡張機能。|
| [TCP ポート](#tcpport) | SQL Server が接続をリッスンするポートを変更します。 |
| [TLS](#tls) | トランスポート レベルのセキュリティを構成します。 |
| [トレース フラグ](#traceflags) | サービスが使用しているトレース フラグを設定します。 |

::: moniker-end

> [!TIP]
> これらの設定の一部は、環境変数を構成できます。 詳細については、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)します。

## <a name="usage-tips"></a>使用上のヒント

* Always On 可用性グループと共有ディスク クラスターでは、常に各ノードで同じ構成の変更を行います。

* 共有ディスク クラスターのシナリオをしようとしないで再起動、 **mssql server**変更を適用するサービス。 SQL Server のアプリケーションとして実行します。 代わりに、オフラインとオンラインに復帰し、リソースを実行します。

* これらの例の完全なパスを指定することで mssql conf を実行する: **/opt/mssql/bin/mssql-conf**します。 代わりにそのパスに移動することを選択した場合は、現在のディレクトリのコンテキストで mssql conf を実行します。 **。/mssql conf**します。

## <a id="agent"></a> SQL Server エージェントを有効にします。

**Sqlagent.enabled**できます[SQL Server エージェント](sql-server-linux-run-sql-server-agent-job.md)します。 既定では、SQL Server エージェントが無効になっています。 場合**sqlagent.enabled**が存在しない mssql.conf 設定ファイルでは、SQL Server が内部的に SQL Server エージェントが無効になっていることを想定します。

この設定を変更するには、次の手順を使用します。

1. SQL Server エージェントを有効にします。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

2. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> SQL Server 照合順序を変更します。

**照合順序のセット**オプションがサポートされる照合順序のいずれかに照合順序の値を変更します。

1. 最初[任意のユーザー データベースをバックアップ](sql-server-linux-backup-and-restore-database.md)サーバーにします。

1. 使用して、 [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)ストアド プロシージャをユーザー データベースをデタッチします。

1. 実行、**照合順序のセット**オプションを選択し、指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Mssql conf ユーティリティは、指定された照合順序の値に変更し、サービスを再起動を試みます。 エラーがあるか、ロールバック、照合順序を元の値。

1. ユーザー データベースのバックアップを復元します。

サポートされる照合順序の一覧は、実行、 [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)関数:`SELECT Name from sys.fn_helpcollations()`します。

## <a id="customerfeedback"></a> お客様のフィードバックを構成します。

**Telemetry.customerfeedback**設定かどうか、SQL Server が Microsoft にフィードバックを送信するかどうかを変更します。 既定では、この値に設定**true**すべてのエディション。 値を変更するには、次のコマンドを実行します。

> [!IMPORTANT]
> いないオフにできますお客様からのフィードバックを無料の SQL Server、Express、および Developer エディション。

1. Mssql conf スクリプトをルートとして実行、**設定**コマンドを**telemetry.customerfeedback**します。 指定することで、次の例がお客様からのフィードバックをオフに**false**します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

詳細については、次を参照してください。 [Linux 上の SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)と[SQL Server のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=868444)します。

## <a id="datadir"></a> 既定のデータまたはログのディレクトリの場所を変更します。

**Filelocation.defaultdatadir**と**filelocation.defaultlogdir**設定は、新しいデータベースとログ ファイルを作成する場所を変更します。 既定では、この場所は、/var/opt/mssql/data は。 これらの設定を変更するには、次の手順を使用します。

1. 新しいデータベースのターゲット ディレクトリのデータとログ ファイルを作成します。 次の例では、作成、新しい**tmp/データ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/data
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/data
   sudo chgrp mssql /tmp/data
   ```

1. Mssql conf を使用してで既定のデータ ディレクトリを変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdatadir /tmp/data
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

1. ようになりました作成された新しいデータベースのすべてのデータベース ファイルは、この新しい場所に格納されます。 新しいデータベースのログ (.ldf) ファイルの場所を変更する場合は、"set"を次のコマンドを使用できます。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. このコマンドは、tmp/ログ ディレクトリが存在して、[ユーザーとグループ] であるにも想定**mssql**します。


## <a id="masterdatabasedir"></a> Master データベース ファイル ディレクトリの既定の場所を変更します。

**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定では、SQL Server エンジンが master データベース ファイルを検索する場所の場所を変更します。 既定では、この場所は、/var/opt/mssql/data は。

これらの設定を変更するには、次の手順を使用します。

1. 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例では、作成、新しい **/tmp masterdatabasedir**ディレクトリ。

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Mssql conf を使用して、マスター データとログ ファイルでの既定の master データベースのディレクトリを変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

   > [!NOTE]
   > マスター データとログ ファイルを移動するには、だけでなく他のすべてのシステム データベースの既定の場所も移動します。

1. SQL Server サービスを停止します。

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Master.mdf と masterlog.ldf を移動します。

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. SQL Server サービスを開始するには。

   ```bash
   sudo systemctl start mssql-server
   ```

   > [!NOTE]
   > SQL Server でのファイル master.mdf および mastlog.ldf ファイルを指定されたディレクトリを見つけられない場合は、システム データベースのテンプレート化されたコピーが指定されたディレクトリに自動的に作成され、SQL Server は正常に起動します。 ただし、ユーザー データベース、サーバーのログイン、サーバー証明書、暗号化キー、SQL エージェント ジョブ、または古い SA ログインのパスワードなどのメタデータは、新しいマスター データベースでは更新されません。 SQL Server を停止して、古い master.mdf および mastlog.ldf を新しいの指定した場所に移動し、引き続き既存のメタデータを使用する SQL Server を開始する必要があります。
 
## <a id="masterdatabasename"></a> Master データベース ファイルの名前を変更します。

**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定では、SQL Server エンジンが master データベース ファイルを検索する場所の場所を変更します。 これはマスター データベースとログ ファイルの名前を変更するのにも使用することができます。 

これらの設定を変更するには、次の手順を使用します。

1. SQL Server サービスを停止します。

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Mssql conf を使用して、マスター データとログ ファイルでの予想されるマスター データベースの名前を変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data/mastlognew.ldf
   ```

   > [!IMPORTANT]
   > のみ、master データベースの名前を変更し、ログ ファイルを SQL Server が正常に開始後できます。 最初の実行前に SQL Server には、master.mdf および mastlog.ldf という名前のファイルが必要です。

1. Master データベースのデータとログ ファイルの名前を変更します。 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. SQL Server サービスを開始するには。

   ```bash
   sudo systemctl start mssql-server
   ```

## <a id="dumpdir"></a> 既定のダンプ ディレクトリの場所を変更します。

**Filelocation.defaultdumpdir**設定では、クラッシュが発生するたびに、メモリと SQL のダンプ生成ここ既定の場所を変更します。 既定では、これらのファイルは、/var/opt/mssql/log で生成されます。

この新しい場所を設定するには、次のコマンドを使用します。

1. 新しいダンプ ファイルのターゲット ディレクトリを作成します。 次の例では、作成、新しい**tmp/ダンプ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/dump
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/dump
   sudo chgrp mssql /tmp/dump
   ```

1. Mssql conf を使用してで既定のデータ ディレクトリを変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultdumpdir /tmp/dump
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="errorlogdir"></a> 既定のエラー ログ ファイル ディレクトリ場所を変更します。

**Filelocation.errorlogfile**設定では、新しいエラー ログ、既定のプロファイラー トレース、システム正常性セッション XE および Hekaton XE セッション ファイルを作成する場所を変更します。 既定では、この場所は、/var/opt/mssql/log は。 SQL エラー ログ ファイルが設定されているディレクトリでは、その他のログの既定のログ ディレクトリになります。

これらの設定を変更するには。

1. 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例では、作成、新しい**tmp/ログ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/logs
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/logs
   sudo chgrp mssql /tmp/logs
   ```

1. Mssql conf を使用してで既定のエラー ログ ファイル名を変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.errorlogfile /tmp/logs/errorlog
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```


## <a id="backupdir"></a> 既定のバックアップ ディレクトリの場所を変更します。

**Filelocation.defaultbackupdir**設定では、バックアップ ファイルが生成される既定の場所を変更します。 既定では、これらのファイルは、/var/opt/mssql/data で生成されます。

この新しい場所を設定するには、次のコマンドを使用します。

1. 新しいバックアップ ファイルのターゲット ディレクトリを作成します。 次の例では、作成、新しい**tmp/バックアップ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/backup
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. "Set"コマンドを使用して既定のバックアップ ディレクトリを変更するのにには、mssql conf を使用します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> コア ダンプの設定を指定します。

SQL Server プロセスのいずれかで例外が発生する場合、SQL Server には、メモリ ダンプが作成されます。

SQL Server では収集するメモリの種類を制御するダンプ用は 2 つのオプションがあります: **coredump.coredumptype**と**coredump.captureminiandfull**します。 これらは、2 つのコア ダンプのキャプチャのフェーズに関連します。 

最初のフェーズのキャプチャがによって制御される、 **coredump.coredumptype**設定で、例外の中に生成されたダンプ ファイルの種類を決定します。 2 番目のフェーズは有効になっている場合、 **coredump.captureminiandfull**設定します。 場合**coredump.captureminiandfull**ダンプを true に設定されているファイルで指定された**coredump.coredumptype**が生成し、2 つ目のミニ ダンプが生成されます。 設定**coredump.captureminiandfull** 2 番目のキャプチャしようとする場合は false を無効にします。

1. 使用してダンプをミニと完全の両方をキャプチャするかどうかを決定、 **coredump.captureminiandfull**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    既定値: **false**

1. 使用したダンプ ファイルの種類を指定、 **coredump.coredumptype**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    既定値: **miniplus**

    次の表に、考えられる**coredump.coredumptype**値。

    | 型 | 説明 |
    |-----|-----|
    | **mini** | ミニは、ダンプ ファイルの最小の種類です。 スレッドとプロセスのモジュールを判断するのに Linux のシステム情報を使用します。 ダンプには、ホスト環境のスレッドのスタックとモジュールが含まれています。 メモリの間接参照またはグローバル変数は含まれません。 |
    | **miniplus** | MiniPlus は、mini に似ていますが、追加のメモリが含まれています。 SQLPAL とダンプを次のメモリ領域の追加、ホスト環境の内部構造を認識するには。</br></br> -さまざまなグローバル変数</br> -64 TB を超えるすべてのメモリ</br> -All という名前のリージョンにある **/proc/$pid/マップ**</br> スレッドとスタックからの間接メモリ</br> のスレッド情報</br> 関連付けられている Teb のおよび Peb</br> -モジュールの情報</br> VMM と VAD ツリー |
    | **filtered** | 具体的には除外されていないプロセス内のすべてのメモリが含まれるには、減算に基づくフィルター処理された使用してデザインします。 デザインは、SQLPAL とダンプから特定のリージョンを除く、ホスト環境の内部を理解しています。
    | **full** | 完全な完全なプロセス ダンプを含むすべてのリージョンにある **/proc/$pid/マップ**します。 これによって制御されない**coredump.captureminiandfull**設定します。 |

## <a id="dbmail"></a> Linux 上の SQL Server の既定のデータベース メール プロファイルを設定します。

**Sqlpagent.databasemailprofile**電子メール アラートの既定のデータベース メール プロファイルを設定することができます。

```bash
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile <profile_name>
```
## <a id="hadr"></a> 高可用性

**Hadr.hadrenabled** SQL Server インスタンスで可用性グループを有効にします。 次のコマンドでは、可用性グループを有効に設定して**hadr.hadrenabled**を 1 にします。 有効にする設定の SQL Server を再起動する必要があります。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

この可用性グループでの使用方法については、次の 2 つのトピックを参照してください。

- [SQL Server on Linux の可用性グループで常に構成します。](sql-server-linux-availability-group-configure-ha.md)
- [SQL Server on Linux の読み取りスケール可用性グループを構成します。](sql-server-linux-availability-group-configure-rs.md)


## <a id="localaudit"></a> 監査のローカル ディレクトリのセット

**Telemetry.userrequestedlocalauditdirectory**設定は、Local Audit を有効にし、Local Audit がログ記録ディレクトリを設定できますが作成されます。

1. 新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例では、作成、新しい**tmp/監査**ディレクトリ。

   ```bash
   sudo mkdir /tmp/audit
   ```

1. 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. Mssql conf スクリプトをルートとして実行、**設定**コマンドを**telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

詳細については、次を参照してください。 [Linux 上の SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)します。

## <a id="lcid"></a> SQL Server のロケールを変更します。

**Language.lcid**任意のサポートされている言語識別子 (LCID) に変更、SQL Server のロケールを設定します。 

1. 次の例は、フランス語にロケールを変更 (1036)。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> メモリ制限を設定します。

**Memory.memorylimitmb**コントロール、量 (MB) で使用できる物理メモリを SQL Server に設定します。 既定では、物理メモリの 80% です。

1. Mssql conf スクリプトをルートとして実行、**設定**コマンドを**memory.memorylimitmb**します。 次の例では、使用可能なメモリを 3.25 GB (3328 MB) を SQL Server に変更します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="msdtc"></a> MSDTC を構成します。

**Network.rpcport**と**distributedtransaction.servertcpport** Microsoft 分散トランザクション コーディネーター (MSDTC) を構成する設定が使用されます。 これらの設定を変更するには、次のコマンドを実行します。

1. Mssql conf スクリプトをルートとして実行、**設定**"network.rpcport"のコマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport <rcp_port>
   ```

2. "Distributedtransaction.servertcpport"設定を設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport <servertcpport_port>
   ```

これらの値を設定するだけでなくもルーティングを構成して、ポート 135 に関するファイアウォールを更新する必要があります。 これを行う方法の詳細については、次を参照してください。 [Linux で MSDTC を構成する方法](sql-server-linux-configure-msdtc.md)します。

Mssql conf を監視し、MSDTC をトラブルシューティングする際の他のいくつかの設定があります。 次の表は、これらの設定を簡単に説明します。 使用の詳細については、Windows のサポートの記事で詳細をご覧ください。 [MS DTC の診断トレースを有効にする方法](https://support.microsoft.com/help/926099/how-to-enable-diagnostic-tracing-for-ms-dtc-on-a-windows-based-compute)します。

| mssql-conf setting | 説明 |
|---|---|
| distributedtransaction.allowonlysecurerpccalls | 分散トランザクションの唯一の RPC 呼び出しをセキュリティで保護を構成します。 |
| distributedtransaction.fallbacktounsecurerpcifnecessary | 分散型のみ RPC 呼び出しのセキュリティを構成します。 |トランザクション
| distributedtransaction.maxlogsize | DTC トランザクション ログ ファイルのサイズ (MB 単位)。 既定値は 64 MB です。 |
| distributedtransaction.memorybuffersize | トレースを格納する循環バッファー サイズ。 このサイズを mb 単位では、既定値は 10 MB |
| distributedtransaction.servertcpport | MSDTC rpc サーバー ポート |
| distributedtransaction.trace_cm | 接続マネージャーでのトレース |
| distributedtransaction.trace_contact | プールの連絡先と連絡先をトレースします。 |
| distributedtransaction.trace_gateway | トレースのゲートウェイのソース |
| distributedtransaction.trace_log | ログのトレース |
| distributedtransaction.trace_misc | その他のカテゴリに分類されるトレース |
| distributedtransaction.trace_proxy | MSDTC プロキシで生成されるトレース |
| distributedtransaction.trace_svc | サービスと .exe ファイルのスタートアップをトレースします。 |
| distributedtransaction.trace_trace | トレース インフラストラクチャ自体 |
| distributedtransaction.trace_util | 複数の場所から呼び出されるトレース ユーティリティのルーチン |
| distributedtransaction.trace_xa | XA トランザクション マネージャー (XATM) のトレース ソース |
| distributedtransaction.tracefilepath | トレース ファイルを保存するフォルダー |
| distributedtransaction.turnoffrpcsecurity | 有効にするか、分散トランザクションの RPC セキュリティを無効にします。 |

::: moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-eula"></a> MLServices Eula に同意します。

追加[machine learning の R または Python パッケージ](sql-server-linux-setup-machine-learning.md)R と Python のオープン ソース ディストリビューションのライセンス条項に同意することがエンジン、データベースに必要です。 次の表では、すべての使用可能なコマンドまたは mlservices Eula に関連するオプションを列挙します。 同じ使用許諾契約書パラメーターは、インストールされている内容に応じて R、Python に使用されます。

```bash
# For all packages: database engine and mlservices
# Setup prompts for mlservices EULAs, which you need to accept
sudo /opt/mssql/bin/mssql-conf setup

# Add R or Python to an existing installation
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml

# Alternative valid syntax
# Adds the EULA section to the INI and sets acceptulam to yes
sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y

# Rescind EULA acceptance and removes the setting
sudo /opt/mssql/bin/mssql-conf unset EULA accepteulaml
```

直接使用許諾契約書への同意を追加することも、 [mssql.conf ファイル](#mssql-conf-format):

```ini
[EULA]
accepteula = Y
accepteulaml = Y
```
:::moniker-end
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="mlservices-outbound-access"></a> 発信ネットワーク アクセスを有効にします。

R、Python、および Java の拡張機能の発信ネットワーク アクセス、 [SQL Server Machine Learning Services](sql-server-linux-setup-machine-learning.md)機能が既定で無効になっています。 送信要求を有効にするには、設定"outboundnetworkaccess"mssql 会議を使用してブール型プロパティ

プロパティを設定した後は、INI ファイルから、更新された値を読み取る SQL Server スタート パッド サービスを再起動します。 再起動のメッセージを通知する、拡張機能に関連する設定を変更するたびにします。

```bash
# Adds the extensibility section and property.
# Sets "outboundnetworkaccess" to true.
# This setting is required if you want to access data or operations off the server.
sudo /opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 1

# Turns off network access but preserves the setting
/opt/mssql/bin/mssql-conf set extensibility outboundnetworkaccess 0

# Removes the setting and rescinds network access
sudo /opt/mssql/bin/mssql-conf unset extensibility.outboundnetworkaccess
```

直接"outboundnetworkaccess"を追加することも、 [mssql.conf ファイル](#mssql-conf-format):

```ini
[extensibility]
outboundnetworkaccess = 1
```
:::moniker-end

## <a id="tcpport"></a> TCP ポートを変更します。

**Network.tcpport**設定では、SQL Server が接続をリッスンする TCP ポートを変更します。 既定では、このポートは 1433 に設定されます。 ポートを変更するには、次のコマンドを実行します。

1. "Network.tcpport"の"set"コマンドを使用して root として mssql conf スクリプトを実行します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

2. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

3. これで、SQL Server に接続して、ときに、ホスト名または IP アドレスの後、コンマ (,) でカスタム ポートを指定する必要があります。 たとえば、SQLCMD で接続するには、次のコマンドを使用します。

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> TLS の設定を指定します。

次のオプションは、Linux で実行されている SQL Server のインスタンスの TLS を構成します。

|オプション |説明 |
|--- |--- |
|**network.forceencryption** |1 の場合、し[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]強制的にすべての接続を暗号化します。 既定では、このオプションには 0 です。 |
|**network.tlscert** |ファイルを証明書への絶対パス[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)](TLS) を使用します。 例: `/etc/ssl/certs/mssql.pem`  証明書ファイルは、mssql アカウントによってアクセス可能である必要があります。 Microsoft を使用して、ファイルへのアクセスを制限することをお勧め`chown mssql:mssql <file>; chmod 400 <file>`します。 |
|**network.tlskey** |ファイルの秘密キーへの絶対パス[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)](TLS) を使用します。 例:`/etc/ssl/private/mssql.key`  証明書ファイルは、mssql アカウントによってアクセス可能である必要があります。 Microsoft を使用して、ファイルへのアクセスを制限することをお勧め`chown mssql:mssql <file>; chmod 400 <file>`します。 |
|**network.tlsprotocols** |SQL Server でどの TLS のプロトコルが許可されているコンマ区切りリスト。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 常に許可されている最も強力なプロトコルをネゴシエートましょう。 クライアントが、許可されている任意のプロトコルをサポートしていない場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]接続の試行を拒否します。  互換性のため、(1.2、1.1, 1.0) の既定ですべてのサポートされているプロトコルを許可します。  クライアントが TLS 1.2 をサポートしている場合、TLS 1.2 のみを許可することをお勧めします。 |
|**network.tlsciphers** |許可されている暗号を指定します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (TLS)。 この文字列の書式を設定ごと[OpenSSL の暗号一覧形式](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html)します。 一般に、このオプションを変更する必要はありません。 <br /> 既定では、次の暗号は使用できます。 <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Kerberos keytab ファイルへのパス |

TLS の設定を使用しての例は、次を参照してください。 [Linux 上の SQL Server への接続の暗号化](sql-server-linux-encrypted-connections.md)します。

## <a id="traceflags"></a> トレース フラグを有効/無効にします。

これは、**トレース フラグ**オプションを有効または SQL Server サービスのスタートアップ トレース フラグを無効にします。 有効または無効にするには、トレース フラグは、次のコマンドを使用します。

1. 次のコマンドを使用してトレース フラグを有効にします。 たとえば、トレース フラグ 1234。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. 個別に指定することで、複数のトレース フラグを有効にできます。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. 同様の方法で有効になっている 1 つまたは複数のトレース フラグを無効に指定して追加、**オフ**パラメーター。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>設定を削除します。

すべての設定が使用した設定を解除する`mssql-conf set`、呼び出す**mssql conf**で、`unset`オプションと設定の名前。 これは、実質的にその既定値に戻す、設定を消去します。

1. 次の例では、クリア、 **network.tcpport**オプション。

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>現在の設定の表示

いずれかを表示するように構成の内容を出力するには、次のコマンドを実行して、設定、 **mssql.conf**ファイル。

```bash
sudo cat /var/opt/mssql/mssql.conf
```

このファイルに表示されていないすべての設定が既定値を使用していることに注意してください。 次のセクションで、サンプル**mssql.conf**ファイル。


## <a id="mssql-conf-format"></a> mssql.conf format

次 **/var/opt/mssql/mssql.conf**ファイルは、各設定の例を示します。 変更を手動で行うこの形式を使用することができます、 **mssql.conf**に応じてファイルします。 場合は、ファイルを手動で変更しないでください、変更が適用される前に SQL Server を再起動する必要があります。 使用する、 **mssql.conf**ファイル Docker を使用する必要があります Docker[のデータを保存](sql-server-linux-configure-docker.md)します。 最初に完全な追加**mssql.conf**ホスト ディレクトリにファイルを開き、コンテナーを実行します。 この例は[お客様からのフィードバック](sql-server-linux-customer-feedback.md)します。

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

```ini
[EULA]
accepteula = Y

[coredump]
captureminiandfull = true
coredumptype = full

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

```ini
[EULA]
accepteula = Y
accepteulaml = Y

[coredump]
captureminiandfull = true
coredumptype = full

[distributedtransaction]
servertcpport = 51999

[filelocation]
defaultbackupdir = /var/opt/mssql/data/
defaultdatadir = /var/opt/mssql/data/
defaultdumpdir = /var/opt/mssql/data/
defaultlogdir = /var/opt/mssql/data/

[hadr]
hadrenabled = 0

[language]
lcid = 1033

[memory]
memorylimitmb = 4096

[network]
forceencryption = 0
ipaddress = 10.192.0.0
kerberoskeytabfile = /var/opt/mssql/secrets/mssql.keytab
rpcport = 13500
tcpport = 1401
tlscert = /etc/ssl/certs/mssql.pem
tlsciphers = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA
tlskey = /etc/ssl/private/mssql.key
tlsprotocols = 1.2,1.1,1.0

[sqlagent]
databasemailprofile = default
errorlogfile = /var/opt/mssql/log/sqlagentlog.log
errorlogginglevel = 7

[telemetry]
customerfeedback = true
userrequestedlocalauditdirectory = /tmp/audit

[traceflag]
traceflag0 = 1204
traceflag1 = 2345
traceflag = 3456
```

::: moniker-end

## <a name="next-steps"></a>次のステップ

代わりにこれらの構成変更の一部を環境変数を使用して、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)します。

その他の管理ツールやシナリオでは、次を参照してください。 [Linux 上の SQL Server の管理](sql-server-linux-management-overview.md)します。
