---
title: SQL Server on Linux をトラブルシューティングします。
description: Linux 上の SQL Server を使用するためには、トラブルシューティングのヒントを提供します。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 05/01/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.openlocfilehash: 507b8e590a359df9a2abf53531dbddf7cca814ea
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833112"
---
# <a name="troubleshoot-sql-server-on-linux"></a>SQL Server on Linux をトラブルシューティングします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Linux または Docker コンテナーで実行されている Microsoft SQL Server のトラブルシューティングを行う方法について説明します。 SQL Server on Linux のトラブルシューティングを行うときにサポートされている機能と既知の制限事項を確認する注意してください、 [SQL Server on Linux リリース ノート](sql-server-linux-release-notes.md)します。

> [!TIP]
> よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)します。

## <a id="connection"></a> 接続エラーをトラブルシューティングします。
Linux、SQL Server への接続に問題が発生した場合は、いくつかを確認します。

- 使用してローカルで接続できない場合**localhost**、代わりに、IP アドレス 127.0.0.1 を使用してください。 できますを**localhost**このアドレスに正しくマップされていません。

- サーバー名または IP アドレスが、クライアント コンピューターから到達可能であることを確認します。

   > [!TIP]
   > Ubuntu コンピューターの IP アドレスを検索するには、次の例のように、ifconfig コマンドを実行できます。
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Red Hat などの次の例に示す ip アドレスを使用することができます。
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > この手法の 1 つの例外は、Azure Vm に関連しています。 Azure vm では、 [、Azure portal で VM のパブリック IP の検出](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect)します。

- 該当する場合は、ファイアウォール上の SQL Server ポート (既定は 1433) を開いていることを確認します。

- Azure Vm の場合があることを確認、[既定の SQL Server ポートのネットワーク セキュリティ グループ ルール](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote)します。

- ユーザー名とパスワードがないこと、入力ミスや余分なスペースや不適切な大文字小文字の区別を確認します。

- 次の例のようにサーバー名でプロトコルとポート番号を明示的に設定しようとしています: **tcp:servername、1433**します。

- 接続エラーとタイムアウトもネットワーク接続の問題があります。 ネットワーク接続、接続情報を確認したら、接続を再試行します。

## <a name="manage-the-sql-server-service"></a>SQL Server サービスを管理します。

次のセクションでは、開始、停止、再起動、および SQL Server サービスの状態を確認する方法を示します。 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Red Hat Enterprise Linux (RHEL) および Ubuntu mssql server サービスを管理します。 

このコマンドを使用して SQL Server サービスの状態を確認します。

   ```bash
   sudo systemctl status mssql-server
   ```

停止、起動、または、必要に応じて、次のコマンドを使用して、SQL Server サービスを再起動できます。

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Mssql Docker コンテナーの実行を管理します。

次のコマンドを実行して最新に作成した SQL Server の Docker コンテナーの状態およびコンテナーの ID を取得できます (下の ID が、**コンテナー ID**列)。

   ```bash
   sudo docker ps -l
   ```
   
停止または、必要に応じて、次のコマンドを使用して、SQL Server サービスを再起動できます。
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Docker のトラブルシューティングの詳細のヒントを参照してください。[トラブルシューティングの SQL Server の Docker コンテナー](sql-server-linux-configure-docker.md#troubleshooting)します。

## <a name="access-the-log-files"></a>ログ ファイルにアクセスします。
   
Linux と Docker の両方のインストールに/var/opt/mssql/log/errorlog ファイルを SQL Server エンジンのログ。 このディレクトリを参照する 'スーパー ユーザー' モードである必要があります。

ここで、インストーラーによって記録: var/選択/mssql/セットアップ/-< インストールの時刻を表す時刻のタイムスタンプ > 'vim' のような任意の utf-16 互換性のあるツールを使用して、エラー ログ ファイルを参照するか、次のように 'cat'。 

   ```bash
   sudo cat errorlog
   ```

場合は、変換することも、ファイルを utf-8 を使用して読み取る次のコマンドで ' 以下' または '詳細'。
   
   ```bash
   sudo iconv -f UTF-16LE -t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>拡張イベント

拡張イベントは、SQL コマンドを使用して照会できます。  拡張イベントに関する詳細が見つかります[ここ](https://technet.microsoft.com/library/bb630282.aspx):

## <a name="crash-dumps"></a>クラッシュ ダンプ 

Linux でのログ ディレクトリにダンプを探します。 Linux のコア ダンプの/var/opt/mssql/log ディレクトリの下のチェック (. tar.gz2 拡張機能) または SQL ミニダンプ (拡張子は .mdmp)

コア ダンプの 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

SQL ダンプの 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>最小限の構成またはシングル ユーザー モードで SQL Server を起動します。

### <a name="start-sql-server-in-minimal-configuration-mode"></a>最小構成モードで SQL Server を起動します。
設定値によりサーバーが起動できないとき (たとえば使用できるメモリが不足している場合) などに便利です。
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>シングル ユーザー モードで SQL Server を起動します。
特定の状況では、-m スタートアップ オプションを使用して、シングル ユーザー モードで SQL Server のインスタンスを起動する必要があります。 たとえば、サーバーの構成オプションを変更したり、破損した master データベースや他のシステム データベースを復旧したりすることがあります。 たとえば、サーバー構成オプションを変更または破損した master データベースまたは他のシステム データベースを回復する場合します。   

シングル ユーザー モードで SQL Server を起動します。
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

SQLCMD を使用したシングル ユーザー モードで SQL Server を起動します。
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  スタートアップに関する将来の問題を防ぐため、Linux 上の SQL Server は "mssql" ユーザーで起動してください。 たとえば、"sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]" などとします。 

別のユーザーと誤って SQL Server を開始した場合は、systemd で SQL Server を開始する前に、'mssql' ユーザーに SQL Server データベース ファイルの所有権を変更する必要があります。 たとえば、'mssql' ユーザーには、/var/opt/mssql 下のすべてのデータベース ファイルの所有権を変更するに次のコマンドを実行します。

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="rebuild-system-databases"></a>システム データベースを再構築します。
最後の手段として、master の再構築することもでき、モデル データベースが既定のバージョンに戻します。

> [!WARNING]
> 次の手順は**すべての SQL Server システム データの削除**に構成されています。 これには、ユーザー データベース (ただし、ユーザー データベース自体ではなく) に関する情報が含まれます。 システム データベースは、次のように格納されているその他の情報も削除されます。 マスター _ キーは、マスター、SA ログインのパスワード、msdb からジョブに関連する情報、msdb、および sp_configure オプションからデータベース メールの情報に読み込まれたすべての証明書。 影響を理解した場合にのみ使用します。

1. SQL Server を停止します。

   ```bash
   sudo systemctl stop mssql-server
   ```

1. 実行**sqlservr**で、**セットアップを強制する-** パラメーター。 

   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr --force-setup
   ```
   
   > [!WARNING]
   > 前述の警告を参照してください。 また、としてこれを実行する必要があります、 **mssql**ユーザーは、ここに示すようにします。

1. 「回復が完了しました」のメッセージを確認した後は、CTRL キーを押しながら C キーを押します。 これは SQL Server をシャット ダウンされます。

1. SA パスワードを再構成します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set-sa-password
   ```
   
1. SQL Server を起動し、サーバーを再構成します。 これには、復元または任意のユーザー データベースを再アタッチが含まれます。

   ```bash
   sudo systemctl start mssql-server
   ```

## <a name="improve-performance"></a>パフォーマンスを向上させる

データベースの設計、ハードウェア、およびワークロードの需要をなど、パフォーマンスに影響を与える多くの要素があります。 パフォーマンスを向上させるために検索する場合は、この記事でベスト プラクティスを確認して開始[パフォーマンスのベスト プラクティスと SQL Server on Linux の構成ガイドライン](sql-server-linux-performance-best-practices.md)します。 パフォーマンスの問題のトラブルシューティングに利用できるツールの一部について説明します。

- [クエリ ストア](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [システム動的管理ビュー (Dmv)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [SQL Server Management Studio でのパフォーマンスのダッシュ ボード](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)

## <a name="common-issues"></a>一般的な問題

1. リモート SQL Server インスタンスに接続することはできません。

   記事のトラブルシューティングのセクションを参照してください。 [SQL Server on Linux への接続](#connection)します。

2. ERROR:ホスト名は 15 文字である必要がありますまたはそれ以下。

   これは、SQL Server の Debian パッケージをインストールしようとするマシンの名前が 15 文字より長いときに発生する既知の問題です。 現在、マシンの名前を変更する以外の回避策はありません。 これを実現する方法の 1 つは、ホスト名のファイルを編集し、マシンを再起動することです。 次[web サイトのガイド](https://www.cyberciti.biz/faq/ubuntu-change-hostname-command/)これを詳しく説明します。

3. システム管理者 (SA) パスワードをリセットしています。

   システム管理者 (SA) パスワードを忘れてしまった何らかの理由でリセットする必要があるか、以下の手順を実行します。

   > [!NOTE]
   > 次の手順では、SQL Server サービスを一時的に停止します。

   ホスト ターミナルにログインし、次のコマンドを実行して、SA のパスワードをリセットする指示に従います。

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. パスワードに特殊文字を使用します。

   一部の文字では、SQL Server ログイン パスワードを使用する場合は、ターミナルでの Linux コマンドを使用するときに、円記号でエスケープする必要があります。 たとえば、エスケープする必要ありますドル記号 ($) を使用するときにいつでもターミナル、コマンド シェル/スクリプトで。

   機能しません。

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   機能:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   リソース:[特殊文字](https://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](https://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
