---
title: "Linux 上の SQL Server の設定の構成 |Microsoft ドキュメント"
description: "このトピックでは、mssql conf ツールを使用して Linux 上の SQL Server 2017 設定を構成する方法について説明します。"
author: luisbosquez
ms.author: lbosq
manager: jhubbard
ms.date: 06/16/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 06798dff-65c7-43e0-9ab3-ffb23374b322
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: a79e5c43dd8921ba2f30ca022d071648b26cdfb0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="configure-sql-server-on-linux-with-the-mssql-conf-tool"></a>Mssql conf ツールを使用して Linux 上の SQL Server を構成します。

**mssql conf** Red Hat Enterprise Linux、SUSE Linux Enterprise Server、および Ubuntu 用 SQL Server 2017 RC2 をインストールする構成スクリプトを示します。 このユーティリティを使用するには、次のパラメーターを設定します。

|||
|---|---|
| [[照合順序]](#collation) | Linux 上の SQL Server の新しい照合順序を設定します。 |
| [お客様のフィードバック](#customerfeedback) | SQL Server が Microsoft にフィードバックを送信するかどうかを選択します。 |
| [既定のデータ ディレクトリ](#datadir) | 新しい SQL Server データベース データ ファイル (.mdf) の既定のディレクトリを変更します。 |
| [既定のログ ディレクトリ](#datadir) | 新しい SQL Server データベースのログ (.ldf) ファイルの既定のディレクトリを変更します。 |
| [既定のダンプ ディレクトリ](#dumpdir) | 新しいメモリ ダンプおよびその他のトラブルシューティング ファイルの既定のディレクトリを変更します。 |
| [既定のバックアップ ディレクトリ](#backupdir) | 新しいバックアップ ファイルの既定のディレクトリを変更します。 |
| [ダンプの種類](#coredump) | 収集するダンプ メモリ ダンプ ファイルの種類を選択します。 |
| [高可用性](#hadr) | 可用性グループを有効にします。 |
| [監査のローカルのディレクトリ](#localaudit) | 設定、ローカルの監査ファイルを追加するディレクトリ。 |
| [ロケール](#lcid) | SQL server を使用するロケールを設定します。 |
| [メモリの制限](#memorylimit) | SQL Server のメモリの制限を設定します。 |
| [TCP ポート](#tcpport) | SQL Server が接続をリッスンする場所、ポートを変更します。 |
| [TLS](#tls) | トランスポート レベルのセキュリティを構成します。 |
| [トレース フラグ](#traceflags) | サービスを使用する予定のトレース フラグを設定します。 |

次のセクションでは、これらの各シナリオの mssql conf を使用する方法の例を紹介します。

> [!TIP]
> Mssql-conf でを実行するこれらの例は、完全なパスを指定します。 **/opt/mssql/bin/mssql-conf**です。 代わりにそのパスに移動する場合は、現在のディレクトリのコンテキストで mssql conf を実行します。 **。/mssql conf**です。

> [!NOTE]
> これらの設定の一部は、環境変数で構成できます。 詳細については、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。

## <a id="collation"></a>SQL Server 照合順序を変更します。

**セット照合**オプションがサポートされる照合順序のいずれかに照合順序の値を変更します。

1. 実行、**セット照合**オプションを選択し、指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-collation
   ```

1. Mssql conf ユーティリティは、指定された照合順序を使用してデータベースを復元し、サービスを再起動を試みます。 エラーがあるか、ロールバック、照合順序、以前の値にします。

サポートされる照合順序の一覧は、実行、 [sys.fn_helpcollations](../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)関数:`SELECT Name from sys.fn_helpcollations()`です。

## <a id="customerfeedback"></a>お客様のフィードバックを構成します。

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

## <a id="datadir"></a>既定のデータまたはログ ディレクトリの場所を変更します。

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

## <a id="dumpdir"></a>既定のダンプ ディレクトリの場所を変更します。

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

## <a id="backupdir"></a>既定のバックアップ ディレクトリの場所を変更します。

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

## <a id="coredump"></a>コア ダンプ設定を指定します。

SQL Server プロセスのいずれかで例外が発生する場合、SQL Server は、メモリ ダンプを作成します。

SQL Server では収集するメモリの種類を制御するダンプの 2 つのオプションがある: **coredump.coredumptype**と**coredump.captureminiandfull**です。 これらは、コア ダンプをキャプチャした 2 つのフェーズに関連します。 

最初のフェーズ キャプチャはによって制御されます、 **coredump.coredumptype**設定は、例外の中に生成されたダンプ ファイルの種類を決定します。 2 番目のフェーズは有効になっている場合、 **coredump.captureminiandfull**設定します。 場合**coredump.captureminiandfull**ダンプを true に設定されているファイルで指定された**coredump.coredumptype**が生成され、2 番目のミニ ダンプが生成もします。 設定**coredump.captureminiandfull** 2 番目のキャプチャを試行する場合は false を無効にします。

1. ミニと完全の両方のダンプをキャプチャするかどうかを判断、 **coredump.captureminiandfull**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.captureminiandfull <true or false>
    ```

    既定値:**は true。**

1. ダンプ ファイルの種類の指定、 **coredump.coredumptype**設定します。

    ```bash
    sudo /opt/mssql/bin/mssql-conf set coredump.coredumptype <dump_type>
    ```

    既定値: **miniplus**

    次の表に、考えられる**coredump.coredumptype**値。

    | 型 | Description |
    |-----|-----|
    | **ミニ** | ミニは、最小のダンプ ファイルの種類です。 スレッドとプロセスのモジュールを確認するのに、Linux システム情報を使用します。 ダンプには、ホスト環境のスレッドのスタックとモジュールのみが含まれています。 これは、メモリの間接参照またはグローバル変数には含まれません。 |
    | **miniplus** | MiniPlus がミニに似ていますが、追加のメモリが含まれています。 SQLPAL とダンプを次のメモリ領域を追加するホスト環境の内部構造を認識します。</br></br> さまざまなグローバル変数</br> -64 TB を超えるすべてのメモリ</br> -すべてのという名前で地域が見つかりません**/proc/$pid/マップ**</br> スレッド ウィンドウとスタックから間接メモリ</br> のスレッド情報</br> 関連付けられている Teb のおよび Peb</br> モジュール情報</br> VMM と VAD ツリー |
    | **フィルター処理** | 減算に基づくフィルター処理された使用は、ここで、プロセス内のすべてのメモリが含まれる具体的には除外されていない限りをデザインします。 設計は、SQLPAL とダンプから特定の地域を除く、ホスト環境の内部構造を理解しています。
    | **完全** | 完全をすべての領域を含む完全なプロセス ダンプ内にある**/proc/$pid/マップ**です。 これによって制御されない**coredump.captureminiandfull**設定します。 |

## <a id="hadr"></a>高可用性

**Hadr.hadrenabled** SQL Server インスタンスで可用性グループを有効にします。 次のコマンドでは、可用性グループを有効に設定して**hadr.hadrenabled**を 1 にします。 有効にする設定の SQL Server を再起動する必要があります。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

これを可用性グループでは使用する方法については、次の 2 つのトピックを参照してください。

- [Linux 上の SQL Server の可用性グループで常に構成します。](sql-server-linux-availability-group-configure-ha.md)
- [SQL Server on Linux の読み取りのスケールの可用性グループを構成します。](sql-server-linux-availability-group-configure-rs.md)

## <a id="localaudit"></a>監査のローカル ディレクトリのセット

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

## <a id="lcid"></a>SQL Server のロケールを変更します。

**Language.lcid**設定の変更をすべてサポートされている言語識別子 (LCID) に SQL Server のロケールです。 

1. 次の例は、フランス語にロケールを変更 (1036)。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="memorylimit"></a>メモリ制限を設定します。

**Memory.memorylimitmb** SQL Server にコントロールの量 (MB) で使用できる物理メモリを設定します。 既定では物理メモリの 80% です。

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**memory.memorylimitmb**です。 次の例では、使用可能なメモリを 3.25 GB (3328 MB) を SQL Server に変更します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
   ```

1. 変更を適用する SQL Server サービスを再起動します。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a id="tcpport"></a>TCP ポートを変更します。

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

## <a id="tls"></a>TLS の設定を指定します。

次のオプションは、Linux で実行されている SQL Server のインスタンスの TLS を構成します。

|オプション |Description |
|--- |--- |
|**network.forceencryption** |1 の場合、し[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]強制的にすべての接続を暗号化します。 既定では、このオプションは 0 です。 |
|**network.tlscert** |証明書への絶対パスがファイルを[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/certs/mssql.pem`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 |
|**network.tlskey** |秘密キーへの絶対パスがファイルを[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/private/mssql.key`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 |
|**network.tlsprotocols** |SQL Server でどの TLS のプロトコルが許可されているコンマ区切り一覧。 [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]常にしようとすると、最も強力な許可されているプロトコルをネゴシエートします。 クライアントが、許可されているすべてのプロトコルをサポートしていない場合[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]接続の試行を拒否します。  互換性のため、すべてのサポートされているプロトコルが既定 (1.2、1.1、1.0) で許可されます。  TLS 1.2 をサポートして、クライアント場合は、TLS 1.2 のみを許可することをお勧めします。 |
|**network.tlsciphers** |指定する暗号がによって許可[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]TLS 用です。 この文字列はに従って書式設定する必要があります[OpenSSL の暗号一覧形式](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html)です。 一般に、このオプションを変更する必要はありません。 <br /> 既定では、次の暗号は使用できます。 <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |
| **network.kerberoskeytabfile** |Kerberos keytab ファイルへのパス |

TLS の設定を使用しての例は、次を参照してください。 [Linux に SQL Server への接続の暗号化](sql-server-linux-encrypted-connections.md)です。

## <a id="traceflags"></a>トレース フラグを有効/無効にします。

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

## <a name="view-current-settings"></a>現在の設定を表示

明示的に構成されているすべての設定を表示する**mssql conf**、次のコマンドを実行します。

```bash
sudo cat /var/opt/mssql/mssql.conf
```

このファイルに表示されていないすべての設定が既定値を使用していることに注意してください。

## <a name="next-steps"></a>次の手順

環境変数を使用してこれらの構成変更の一部を代わりに、次を参照してください。[環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。

その他の管理ツールとシナリオには、「 [Linux 上の SQL Server の管理](sql-server-linux-management-overview.md)です。

