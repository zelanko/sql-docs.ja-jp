---
title: Linux 上の SQL Server の設定の構成 |Microsoft ドキュメント
description: この記事では、mssql conf ツールを使用して Linux 上の SQL Server 2017 設定を構成する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.openlocfilehash: 1ec0af7954c1ec2b6398c0a703ce5a153b76f68f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Mssql conf ツールを使用して Linux 上の SQL Server を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

**mssql conf** Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu Server 2017 年 SQL と共にインストールされる構成スクリプトを示します。 このユーティリティを使用するには、次のパラメーターを設定します。

|||
|---|---|
| [エージェント](#agent) | SQL Server エージェントを有効にします。 |
| [[照合順序]](#collation) | Linux 上の SQL Server の新しい照合順序を設定します。 |
| [お客様のフィードバック](#customerfeedback) | SQL Server が Microsoft にフィードバックを送信するかどうかを選択します。 |
| [[データベース メール プロファイル]](#dbmail) | Linux 上の SQL Server の既定のデータベース メール プロファイルを設定します。 |
| [既定のデータ ディレクトリ](#datadir) | 新しい SQL Server データベース データ ファイル (.mdf) の既定のディレクトリを変更します。 |
| [既定のログ ディレクトリ](#datadir) | 新しい SQL Server データベースのログ (.ldf) ファイルの既定のディレクトリを変更します。 |
| [既定の master データベース ファイル ディレクトリ](#masterdatabasedir) | 既存の SQL インストールで master データベース ファイルの既定のディレクトリを変更します。|
| [既定の master データベース ファイル名](#masterdatabasename) | Master データベース ファイルの名前を変更します。 |
| [既定のダンプ ディレクトリ](#dumpdir) | 新しいメモリ ダンプおよびその他のトラブルシューティング ファイルの既定のディレクトリを変更します。 |
| [既定のエラー ログ ディレクトリ](#errorlogdir) | 新しい SQL Server エラー ログ、既定のプロファイラー トレース、システム正常性セッション XE、および Hekaton セッション XE ファイルの既定のディレクトリを変更します。 |
| [既定のバックアップ ディレクトリ](#backupdir) | 新しいバックアップ ファイルの既定のディレクトリを変更します。 |
| [ダンプの種類](#coredump) | 収集するダンプ メモリ ダンプ ファイルの種類を選択します。 |
| [高可用性](#hadr) | 可用性グループを有効にします。 |
| [監査のローカルのディレクトリ](#localaudit) | 設定、ローカルの監査ファイルを追加するディレクトリ。 |
| [ロケール](#lcid) | SQL server を使用するロケールを設定します。 |
| [メモリの制限](#memorylimit) | SQL Server のメモリの制限を設定します。 |
| [TCP ポート](#tcpport) | SQL Server が接続をリッスンする場所、ポートを変更します。 |
| [TLS](#tls) | トランスポート レベルのセキュリティを構成します。 |
| [トレース フラグ](#traceflags) | サービスを使用する予定のトレース フラグを設定します。 |

> [!TIP]
> これらの設定の一部は、環境変数で構成できます。 詳細については、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。

## <a name="usage-tips"></a>使用上のヒント

* Always On 可用性グループと共有ディスク クラスターでは、常に各ノードで同じ構成の変更をください。

* 共有ディスク クラスターのシナリオのしようとしないで再起動、 **mssql サーバー**変更を適用するサービスです。 SQL Server のアプリケーションとして実行します。 代わりに、オフラインおよびオンラインに戻る、リソースを取得します。

* Mssql-conf でを実行するこれらの例は、完全なパスを指定します。 **/opt/mssql/bin/mssql-conf**です。 代わりにそのパスに移動する場合は、現在のディレクトリのコンテキストで mssql conf を実行します。 **。/mssql conf**です。

## <a id="agent"></a> SQL Server エージェントを有効にします。

**Sqlagent.enabled**設定有効[SQL Server エージェント](sql-server-linux-run-sql-server-agent-job.md)です。 既定では、SQL Server エージェントは無効です。 場合**sqlagent.enabled**が存在しない mssql.conf 設定ファイルで、SQL Server が内部で SQL Server エージェントが有効になっていることを前提とします。

この設定を変更するには、次の手順を使用します。

1. SQL Server エージェントを有効にします。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="collation"></a> SQL Server 照合順序を変更します。

**セット照合**オプションがサポートされる照合順序のいずれかに照合順序の値を変更します。

1. 最初[任意のユーザー データベースをバックアップ](sql-server-linux-backup-and-restore-database.md)サーバーにします。

1. 使用して、 [sp_detach_db](../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)ストアド プロシージャ、ユーザー データベースをデタッチします。

1. 実行、**セット照合**オプションを選択し、指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Mssql conf ユーティリティは、指定された照合順序の値に変更し、サービスを再起動を試みます。 エラーがあるか、ロールバック、照合順序、以前の値にします。

1. ユーザー データベースのバックアップを復元します。

サポートされる照合順序の一覧は、実行、 [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)関数:`SELECT Name from sys.fn_helpcollations()`です。

## <a id="customerfeedback"></a> お客様のフィードバックを構成します。

**Telemetry.customerfeedback**設定か、SQL Server が Microsoft にフィードバックを送信するかどうかを変更します。 既定では、この値に設定**true**です。 値を変更するには、次のコマンドを実行します。

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**telemetry.customerfeedback**です。 指定して、次の例がお客様のフィードバックをオフに**false**です。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.customerfeedback false
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

詳細については、次を参照してください。 [for Linux に SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)です。

## <a id="datadir"></a> 既定のデータまたはログ ディレクトリの場所を変更します。

**Filelocation.defaultdatadir**と**filelocation.defaultlogdir**設定は、新しいデータベース ファイルとログ ファイルを作成する場所を変更します。 既定では、この場所は、/var/opt/mssql/data です。 これらの設定を変更するには、次の手順を使用します。

1. 新しいデータベースのターゲット ディレクトリ データおよびログ ファイルを作成します。 次の例は、新しい作成**tmp/データ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/data
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

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

1. ようになりました新規に作成されたデータベースのすべてのデータベース ファイルは、この新しい場所に格納されます。 新しいデータベースのログ (.ldf) ファイルの場所を変更したい場合は、次「セット」コマンドを使用できます。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultlogdir /tmp/log
   ```

1. このコマンドは、tmp/ログ ディレクトリが存在して、ユーザーとグループの下であることにも想定**mssql**です。


## <a id="masterdatabasedir"></a> Master データベース ファイル ディレクトリの既定の場所を変更します。

**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定の変更を SQL Server エンジンが master データベース ファイルを検索する場所です。 既定では、この場所は、/var/opt/mssql/data です。 

これらの設定を変更するには、次の手順を使用します。

1. 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/masterdatabasedir**ディレクトリ。

   ```bash
   sudo mkdir /tmp/masterdatabasedir
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
   ```

1. Mssql conf を使用して、マスター データ ファイルとログ ファイルの既定の master データベースのディレクトリを変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
   ```

1. SQL Server サービスを停止します。

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Master.mdf と masterlog.ldf を移動するには。 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf 
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
   ```

1. SQL Server サービスを開始します。

   ```bash
   sudo systemctl start mssql-server
   ```
   
> [!NOTE]
> SQL Server は、指定したディレクトリ内 master.mdf ファイルおよび mastlog.ldf ファイルを見つけることができません、指定したディレクトリ内のシステム データベースのテンプレートのコピーが自動的に作成されます、および SQL Server は正常に場合を起動します。 ただし、ユーザー データベース、サーバーのログイン、サーバー証明書、暗号化キー、SQL エージェント ジョブ、または古い SA ログインのパスワードなどのメタデータは、新しいマスター データベースでは更新されません。 SQL Server を停止し、新しい指定した場所に古い master.mdf および mastlog.ldf を移動し、引き続き既存のメタデータを使用する SQL Server を開始する必要があります。 


## <a id="masterdatabasename"></a> Master データベース ファイルの名前を変更します。

**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定の変更を SQL Server エンジンが master データベース ファイルを検索する場所です。 既定では、この場所は、/var/opt/mssql/data です。 これらの設定を変更するには、次の手順を使用します。

1. SQL Server サービスを停止します。

   ```bash
   sudo systemctl stop mssql-server
   ```

1. Mssql conf を使用して、マスター データ ファイルとログ ファイルの予想されるマスター データベースの名前を変更する、**設定**コマンド。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /var/opt/mssql/data/masternew.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.mastlogfile /var/opt/mssql/data /mastlognew.ldf
   ```

1. Master データベースのデータとログ ファイルの名前を変更します。 

   ```bash
   sudo mv /var/opt/mssql/data/master.mdf /var/opt/mssql/data/masternew.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /var/opt/mssql/data/mastlognew.ldf
   ```

1. SQL Server サービスを開始します。

   ```bash
   sudo systemctl start mssql-server
   ```



## <a id="dumpdir"></a> 既定のダンプ ディレクトリの場所を変更します。

**Filelocation.defaultdumpdir**設定の変更をメモリと SQL ダンプが生成される場所、クラッシュが発生するたびに既定の場所。 既定では、これらのファイルは/var/opt/mssql/log で生成されます。

この新しい場所を設定するには、次のコマンドを使用します。

1. 新しいダンプ ファイルのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/ダンプ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/dump
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

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

**Filelocation.errorlogfile**設定の変更を新しいエラー ログ、既定のプロファイラー トレース、システム正常性セッション XE および Hekaton セッション XE ファイルが作成される場所です。 既定では、この場所は、/var/opt/mssql/log です。 SQL エラー ログ ファイルが設定されているディレクトリでは、他のログの既定のログ ディレクトリになります。

これらの設定を変更します。

1. 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/ログ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/logs
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

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

**Filelocation.defaultbackupdir**設定の変更をバックアップ ファイルが生成される既定の場所。 既定では、これらのファイルは/var/opt/mssql/data で生成されます。

この新しい場所を設定するには、次のコマンドを使用します。

1. 新しいバックアップ ファイルのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/バックアップ**ディレクトリ。

   ```bash
   sudo mkdir /tmp/backup
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/backup
   sudo chgrp mssql /tmp/backup
   ```

1. Mssql conf を使用して、「セット」コマンドを使用して既定のバックアップ ディレクトリを変更します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set filelocation.defaultbackupdir /tmp/backup
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="coredump"></a> コア ダンプ設定を指定します。

SQL Server プロセスのいずれかで例外が発生する場合、SQL Server は、メモリ ダンプを作成します。

SQL Server では収集するメモリの種類を制御するダンプの 2 つのオプションがある: **coredump.coredumptype**と**coredump.captureminiandfull**です。 これらは、コア ダンプをキャプチャした 2 つのフェーズに関連します。 

最初のフェーズ キャプチャはによって制御されます、 **coredump.coredumptype**設定は、例外の中に生成されたダンプ ファイルの種類を決定します。 2 番目のフェーズは有効になっている場合、 **coredump.captureminiandfull**設定します。 場合**coredump.captureminiandfull**ダンプを true に設定されているファイルで指定された**coredump.coredumptype**が生成され、2 番目のミニ ダンプが生成もします。 設定**coredump.captureminiandfull** 2 番目のキャプチャを試行する場合は false を無効にします。

1. ミニと完全の両方のダンプをキャプチャするかどうかを判断、 **coredump.captureminiandfull**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    既定値: **false**

1. ダンプ ファイルの種類の指定、 **coredump.coredumptype**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    既定値: **miniplus**

    次の表に、考えられる**coredump.coredumptype**値。

    | 型 | Description |
    |-----|-----|
    | **mini** | ミニは、最小のダンプ ファイルの種類です。 スレッドとプロセスのモジュールを確認するのに、Linux システム情報を使用します。 ダンプには、ホスト環境のスレッドのスタックとモジュールのみが含まれています。 これは、メモリの間接参照またはグローバル変数には含まれません。 |
    | **miniplus** | MiniPlus がミニに似ていますが、追加のメモリが含まれています。 SQLPAL とダンプを次のメモリ領域を追加するホスト環境の内部構造を認識します。</br></br> さまざまなグローバル変数</br> -64 TB を超えるすべてのメモリ</br> -すべてのという名前で地域が見つかりません **/proc/$pid/マップ**</br> スレッド ウィンドウとスタックから間接メモリ</br> のスレッド情報</br> 関連付けられている Teb のおよび Peb</br> モジュール情報</br> VMM と VAD ツリー |
    | **filtered** | 減算に基づくフィルター処理された使用は、ここで、プロセス内のすべてのメモリが含まれる具体的には除外されていない限りをデザインします。 設計は、SQLPAL とダンプから特定の地域を除く、ホスト環境の内部構造を理解しています。
    | **full** | 完全をすべての領域を含む完全なプロセス ダンプ内にある **/proc/$pid/マップ**です。 これによって制御されない**coredump.captureminiandfull**設定します。 |

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

これを可用性グループでは使用する方法については、次の 2 つのトピックを参照してください。

- [Linux 上の SQL Server の可用性グループで常に構成します。](sql-server-linux-availability-group-configure-ha.md)
- [SQL Server on Linux の読み取りのスケールの可用性グループを構成します。](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a> 監査のローカル ディレクトリのセット

**Telemetry.userrequestedlocalauditdirectory**設定は、ローカルの監査を有効にし、ローカルの監査ログで、ディレクトリを設定できますが作成されます。

1. 新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/監査**ディレクトリ。

   ```bash
   sudo mkdir /tmp/audit
   ```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

   ```bash
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
   ```

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**telemetry.userrequestedlocalauditdirectory**:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

詳細については、次を参照してください。 [for Linux に SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)です。

## <a id="lcid"></a> SQL Server のロケールを変更します。

**Language.lcid**設定の変更をすべてサポートされている言語識別子 (LCID) に SQL Server のロケールです。 

1. 次の例は、フランス語にロケールを変更 (1036)。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a> メモリ制限を設定します。

**Memory.memorylimitmb** SQL Server にコントロールの量 (MB) で使用できる物理メモリを設定します。 既定では物理メモリの 80% です。

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**memory.memorylimitmb**です。 次の例では、使用可能なメモリを 3.25 GB (3328 MB) を SQL Server に変更します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a> TCP ポートを変更します。

**Network.tcpport**設定の変更を SQL Server が接続をリッスンする場所、TCP ポート。 既定では、このポートは 1433 に設定します。 ポートを変更するには、次のコマンドを実行します。

1. "Network.tcpport"を"set"コマンドを使用してルートとして mssql conf スクリプトを実行します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

1. SQL Server に接続するようになりました、ときに、ホスト名または IP アドレスの後に、コンマ (,) でカスタムのポートを指定する必要があります。 たとえば、SQLCMD で接続するには、次のコマンドを使用すると。

   ```bash
   sqlcmd -S localhost,<new_tcp_port> -U test -P test
   ```

## <a id="tls"></a> TLS の設定を指定します。

次のオプションは、Linux で実行されている SQL Server のインスタンスの TLS を構成します。

|オプション |Description |
|--- |--- |
|**network.forceencryption** |1 の場合、し[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]強制的にすべての接続を暗号化します。 既定では、このオプションは 0 です。 |
|**network.tlscert** |証明書への絶対パスがファイルを[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/certs/mssql.pem`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 |
|**network.tlskey** |秘密キーへの絶対パスがファイルを[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/private/mssql.key`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 |
|**network.tlsprotocols** |SQL Server でどの TLS のプロトコルが許可されているコンマ区切り一覧。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 常にしようとすると、最も強力な許可されているプロトコルをネゴシエートします。 クライアントが、許可されているすべてのプロトコルをサポートしていない場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]接続の試行を拒否します。  互換性のため、すべてのサポートされているプロトコルが既定 (1.2、1.1、1.0) で許可されます。  TLS 1.2 をサポートして、クライアント場合は、TLS 1.2 のみを許可することをお勧めします。 |
|**network.tlsciphers** |指定する暗号がによって許可[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]TLS 用です。 この文字列はに従って書式設定する必要があります[OpenSSL の暗号一覧形式](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html)です。 一般に、このオプションを変更する必要はありません。 <br /> 既定では、次の暗号は使用できます。 <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Kerberos keytab ファイルへのパス |

TLS の設定を使用しての例は、次を参照してください。 [Linux に SQL Server への接続の暗号化](sql-server-linux-encrypted-connections.md)です。

## <a id="traceflags"></a> トレース フラグを有効/無効にします。

これは、**トレース フラグ**オプションを有効または SQL Server サービスのスタートアップ トレース フラグを無効にします。 有効/無効にするには、トレース フラグは、次のコマンドを使用します。

1. 次のコマンドを使用してトレース フラグを有効にします。 たとえば、トレース フラグ 1234。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 on
   ```

1. 複数のトレース フラグを有効にするには、個別に指定すること。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 2345 3456 on
   ```

1. 同様の方法で、指定することと、追加することを 1 つまたは複数の有効なトレース フラグを無効にする、**オフ**パラメーター。

   ```bash
   sudo /opt/mssql/bin/mssql-conf traceflag 1234 2345 3456 off
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="remove-a-setting"></a>設定を削除します。

任意の設定がによる設定を解除する`mssql-conf set`、呼び出す**mssql conf**で、`unset`オプションと設定の名前。 これは、設定を消去します、実質的にその既定値に戻すこと。

1. 次の例では、クリア、 **network.tcpport**オプション。

   ```bash
   sudo /opt/mssql/bin/mssql-conf unset network.tcpport
   ```

1. SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="view-current-settings"></a>現在の設定を表示

いずれかを表示するように構成の内容を出力するには、次のコマンドを実行して、設定、 **mssql.conf**ファイル。

```bash
sudo cat /var/opt/mssql/mssql.conf
```

このファイルに表示されていないすべての設定が既定値を使用していることに注意してください。 次のセクションでは、サンプルを提供**mssql.conf**ファイル。

## <a name="mssqlconf-format"></a>mssql.conf 形式

次 **/var/opt/mssql/mssql.conf**ファイルは、各設定の例を示します。 この形式を使用してへの変更を手動で行うことができます、 **mssql.conf**必要に応じてファイルします。 場合は、ファイルを手動で変更しないでください、変更が適用される前に SQL Server を再起動する必要があります。 使用する、 **mssql.conf**ファイル Docker を使用する必要があります Docker [、データを永続化](sql-server-linux-configure-docker.md)です。 最初に完全な追加**mssql.conf**ホスト ディレクトリにファイルし、コンテナーを実行します。 この例は[お客様からのフィードバック](sql-server-linux-customer-feedback.md)です。

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

## <a name="next-steps"></a>次の手順

環境変数を使用してこれらの構成変更の一部を代わりに、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。

その他の管理ツールとシナリオには、「 [Linux 上の SQL Server の管理](sql-server-linux-management-overview.md)です。
