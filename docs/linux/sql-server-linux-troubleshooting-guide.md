---
title: SQL Server on Linux のトラブルシューティング |Microsoft ドキュメント
description: SQL Server 2017 を使用して Linux 上のトラブルシューティングのヒントを提供します。
author: annashres
ms.author: anshrest
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 99636ee8-2ba6-4316-88e0-121988eebcf9S
ms.workload: On Demand
ms.openlocfilehash: 2be739569e240bfecd7e18fecae52a6f15d24e0f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshoot-sql-server-on-linux"></a>SQL Server on Linux をトラブルシューティングします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Linux または、Docker コンテナーで実行されている Microsoft SQL Server のトラブルシューティングを行う方法について説明します。 SQL Server on Linux のトラブルシューティングを行うときにサポートされる機能の既知の制限事項を確認するのに注意してください、 [SQL Server on Linux のリリース ノート](sql-server-linux-release-notes.md)です。

> [!TIP]
> よく寄せられる質問に対する回答については、次を参照してください。、 [SQL Server on Linux に関する FAQ](sql-server-linux-faq.md)です。

## <a id="connection"></a> 接続エラーをトラブルシューティングします。
Linux SQL Server への接続に問題が発生した場合は、いくつかを確認します。 

- サーバー名または IP アドレスが、クライアント コンピューターから到達可能であることを確認します。

   > [!TIP]
   > Ubuntu コンピューターの IP アドレスを検索するには、次の例のように ifconfig コマンドを実行することができます。
   >
   >   ```bash
   >   sudo ifconfig eth0 | grep 'inet addr'
   >   ```
   > Red Hat では、次の例のように、ip アドレスを使用できます。
   >
   >   ```bash
   >   sudo ip addr show eth0 | grep "inet"
   >   ```
   > この手法の 1 つの例外は、Azure Vm に関連しています。 Azure vm で[Azure ポータルで VM のパブリック IP を見つける](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#connect)です。

- 該当する場合は、ファイアウォール上の SQL Server ポート (既定は 1433) が開かれていることを確認します。

- Azure vm であることを確認、 [SQL Server の既定ポートのネットワーク セキュリティ グループ ルール](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine#remote)です。

- ユーザー名とパスワードを含まないこと誤りがないか、余分なスペースか不適切な大文字小文字の区別を確認します。

- 次の例のようにサーバー名でプロトコルとポート番号を明示的に設定しようとしています: **tcp:servername、1433**です。

- 接続エラーとタイムアウトもネットワーク接続の問題があります。 接続情報とネットワーク接続を確認した後、再度接続を再試行してください。

## <a name="manage-the-sql-server-service"></a>SQL Server サービスを管理します。

次のセクションでは、開始、停止、再開、および SQL Server サービスの状態を確認する方法を示します。 

### <a name="manage-the-mssql-server-service-in-red-hat-enterprise-linux-rhel-and-ubuntu"></a>Red Hat Enterprise Linux (RHEL) および Ubuntu で mssql サーバー サービスを管理します。 

このコマンドを使用して SQL Server サービスの状態を確認します。

   ```bash
   sudo systemctl status mssql-server
   ```

停止、開始、または必要に応じて、次のコマンドを使用して、SQL Server サービスを再起動することができます。

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl start mssql-server
   sudo systemctl restart mssql-server
   ```

### <a name="manage-the-execution-of-the-mssql-docker-container"></a>Mssql Docker コンテナーの実行を管理します。

次のコマンドを実行して最新作成された SQL Server の Docker コンテナーの状態およびコンテナーの ID を取得できます (下の ID が、**コンテナー ID**列)。

   ```bash
   sudo docker ps -l
   ```
   
停止または、必要に応じて、次のコマンドを使用して、SQL Server サービスを再起動できます。
   
   ```bash
   sudo docker stop <container ID>
   sudo docker restart <container ID>
   ```

> [!TIP]
> Docker の詳細のトラブルシューティングのヒントを参照してください。[トラブルシューティング SQL Server の Docker コンテナー](sql-server-linux-configure-docker.md#troubleshooting)です。

## <a name="access-the-log-files"></a>ログ ファイルにアクセスします。
   
Linux と Docker の両方のインストールに/var/opt/mssql/log/errorlog ファイルを SQL Server エンジンのログです。 このディレクトリを参照する 'superuser' モードである必要があります。

ここで、ログ:/var/オプトイン/mssql/セットアップ-< タイムスタンプのインストール時刻を表す > 'vim' のように、utf-16 の互換性のあるツールを使用して、エラー ログ ファイルを参照するか、次のように 'cat'。 

   ```bash
   sudo cat errorlog
   ```

場合は、変換することも、ファイルを utf-8 に注意してお読みに 'more' または 'less、次のコマンド。
   
   ```bash
   sudo iconv –f UTF-16LE –t UTF-8 <errorlog> -o <output errorlog file>
   ```
## <a name="extended-events"></a>拡張イベント

拡張イベントは、SQL コマンドを使用して照会できます。  拡張イベントの詳細についてはあります[ここ](https://technet.microsoft.com/en-us/library/bb630282.aspx):

## <a name="crash-dumps"></a>クラッシュ ダンプ 

Linux のログ ディレクトリにダンプを探します。 Linux のコアはダンプ/var/opt/mssql/log ディレクトリの下のチェック (. tar.gz2 拡張機能) または SQL ミニダンプ (拡張子は .mdmp)

コア ダンプの 
   ```bash
   sudo ls /var/opt/mssql/log | grep .tar.gz2 
   ```

SQL ダンプの 
   ```bash
   sudo ls /var/opt/mssql/log | grep .mdmp 
   ```
   
## <a name="start-sql-server-in-minimal-configuration-or-in-single-user-mode"></a>最小構成で、またはシングル ユーザー モードで SQL Server を起動します。

### <a name="start-sql-server-in-minimal-configuration-mode"></a>最小構成モードで SQL Server を起動します。
設定値によりサーバーが起動できないとき (たとえば使用できるメモリが不足している場合) などに便利です。
  
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -f
   ```

### <a name="start-sql-server-in-single-user-mode"></a>シングル ユーザー モードで SQL Server を起動します。
特定の状況では、スタートアップ オプションと m を使用して、シングル ユーザー モードで SQL Server のインスタンスを起動する必要があります。 たとえば、サーバーの構成オプションを変更したり、破損した master データベースや他のシステム データベースを復旧したりすることがあります。 たとえば、サーバー構成オプションを変更または破損した master データベースまたはその他のシステム データベースを復元する可能性があります。   

シングル ユーザー モードで SQL Server を起動します。
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m
   ```

SQLCMD でのシングル ユーザー モードで SQL Server を起動します。
   ```bash
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
   ```
  
> [!WARNING]  
>  スタートアップに関する将来の問題を防ぐため、Linux 上の SQL Server は "mssql" ユーザーで起動してください。 たとえば、"sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]" などとします。 

別のユーザーと、SQL Server を開始している誤って場合、は、systemd で SQL Server を開始する前に 'mssql' ユーザーに SQL Server データベース ファイルの所有権を変更する必要があります。 たとえば、'mssql' ユーザーに/var/opt/mssql 下にあるすべてのデータベース ファイルの所有権を変更するに次のコマンドを実行します。

   ```bash
   chown -R mssql:mssql /var/opt/mssql/
   ```

## <a name="common-issues"></a>一般的な問題

1. リモート SQL Server インスタンスに接続することはできません。

   記事の「トラブルシューティング」を参照してください[Linux に SQL Server への接続](#connection)です。

2. エラー: ホスト名は 15 文字である必要があります以下です。

   これは、Debian パッケージの SQL Server をインストールしようとするコンピューターの名前が 15 文字より長いときに発生する既知の問題です。 現在、マシンの名前を変更する以外の回避策はありません。 これを実現する方法の 1 つでは、ホスト名のファイルを編集し、コンピューターを再起動します。 次[web サイトのガイド](http://www.cyberciti.biz/faq/ubuntu-change-hostname-command/)これについて詳しく説明します。

3. システム管理者 (SA) パスワードをリセットしています。

   システム管理者 (SA) パスワードを忘れてしまった何らかの理由でリセットする必要があるか、以下の手順を実行します。

   > [!NOTE]
   > 次の手順では、SQL Server サービスを一時的に停止します。

   ホスト端末にログインし、次のコマンドを実行し、SA パスワードをリセットする指示に従います。

   ```bash
   sudo systemctl stop mssql-server
   sudo /opt/mssql/bin/mssql-conf setup
   ```

4. [パスワード] に特殊文字を使用します。

   SQL Server ログイン パスワードでいくつかの文字を使用する場合は、Linux ターミナルで使用するときにエスケープする必要があります。 $ をエスケープする必要があります、円記号を使用していつでもは、ターミナル コマンド/シェル スクリプトで使用されます。

   機能しません。

   ```bash
   sudo sqlcmd -S myserver -U sa -P Test$$
   ```

   動作:

   ```bash
   sqlcmd -S myserver -U sa -P Test\$\$
   ```

   リソース:[特殊文字](http://tldp.org/LDP/abs/html/special-chars.html)
   [Escaping](http://tldp.org/LDP/abs/html/escapingsection.html)

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
