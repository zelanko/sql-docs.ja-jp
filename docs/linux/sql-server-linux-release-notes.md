---
title: "Linux 上の SQL Server 2017 のリリース ノート |Microsoft ドキュメント"
description: "このトピックでは、リリース ノートが含まれていて、Linux で実行されている SQL Server 2017 の機能をサポートします。 リリース ノートは、RC2 と以前のバージョンで含まれます。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/07/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: baa5826e9722bfb23afacf729d80bebf88985ed3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 のリリース ノート

次のリリース ノートは、Linux で実行されている SQL Server 2017 に適用されます。 このリリースでは、Linux 用の SQL Server データベース エンジン機能の多くをサポートします。 次のトピックは、各リリースでは、最新のリリースでは、RC2 以降のセクションに分割されます。 サポートされるプラットフォーム、ツール、機能、および既知の問題の各セクションの情報を参照してください。

次の表は、このトピックで説明される SQL Server 2017 のリリースを一覧表示します。

| リリース | バージョン | リリース日 |
|-----|-----|-----|
| [RC2](#RC2) | 14.0.900.75 | 8-2017 |
| [RC1](#RC1) | 14.0.800.90 | 7-2017 |
| [CTP 2.1](#ctp21) | 14.0.600.250 | 5-2017 |
| [(CTP 2.0)](#ctp20) | 14.0.500.272 | 4-2017 |
| [CTP 1.4](#ctp14) | 14.0.405.198 | 3-2017 |
| [CTP 1.3](#ctp13) | 14.0.304.138 | 2-2017 |
| [CTP 1.2](#ctp12) | 14.0.200.24 | 1-2017 |
| [CTP 1.1](#ctp11) | 14.0.100.187 | 12-2016 |
| [CTP 1.0](#ctp10) | 14.0.1.246 | 11-2016 |

## <a id="RC2"></a>RC2 (2017 年 8 月)

このリリースの SQL Server エンジンのバージョンは、14.0.900.75 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で 1.5 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細

パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありませんに注意してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.900.75-1 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.900.75-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.900.75-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.900.75-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.900.75-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.900.75-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.900.75-1_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [Windows 用 SQL Server Management Studio (SSMS)](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 |

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス

次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | トランザクション レプリケーション |
| &nbsp; | マージ レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | サード パーティ製の接続で分散クエリ |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| &nbsp; | バッファー プール拡張 |
| **SQL Server エージェント** |  サブシステム: CmdExec、PowerShell、キュー リーダーは、SSIS、SSAS、SSRS |
| &nbsp; | 警告 |
| &nbsp; | ログ リーダー エージェント (Log Reader Agent) |
| &nbsp; | 変更データ キャプチャ |
| &nbsp; | 管理対象のバックアップ |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | 拡張キー管理 |
| **サービス** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題

次のセクションでは、Linux 上の SQL Server 2017 RC2 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般

- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**: の言語を変更、 **sa**を使用してログイン、 **ALTER LOGIN**ステートメントです。

#### <a name="databases"></a>データベース

- Mssql conf ユーティリティでは、master データベースを移動できません。 Mssql 構成とその他のシステム データベースを移動することができます。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

- 特定のアルゴリズム (暗号スイート) トランスポート層セキュリティ (TLS) は、Linux に SQL Server では正しく機能しません。 これは、結果、SQL Server に接続するときに問題と同様に高可用性グループ レプリカ間の接続を確立する接続が失敗します。

   - **解像度**: 変更、 **mssql.conf**構成スクリプトを SQL Server on Linux は、次の手順を実行して問題のある暗号スイートを無効にします。

      1. 次の/var/opt/mssql/mssql.conf に追加します。

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

      1. 次のコマンドでは、SQL Server を再起動します。
   
      ```
      sudo systemctl restart mssql-server
      ```

- インメモリ OLTP を使用して Windows 上の SQL Server 2014 データベースは、Linux 上の SQL Server 2017 に復元することはできません。 インメモリ OLTP を使用する SQL Server 2014 データベースを復元するに最初にデータベースをアップグレードを SQL Server 2016 または Windows 上の SQL Server 2017 移動の前に SQL server on Linux のバックアップ/復元またはデタッチとアタッチを使用して。

#### <a name="remote-database-files"></a>リモートのデータベース ファイル

- このリリースでは、NFS サーバー上のデータベース ファイルをホストすることはできません。 これは、NFS を使用して、共有ディスクに対してフェールオーバー クラスタ リングのデータベースと非クラスター化インスタンスに含まれています。 今後のリリースで NFS サーバーのサポートを有効にすると現在取り組んでいます。

#### <a name="localization"></a>ローカライズ

- ロケールが英語 (en_us) のセットアップ中にでない場合は、bash セッションとターミナルで utf-8 のエンコードを使用する必要があります。 ASCII エンコーディングを使用する場合は、次のようなエラーを参照してください可能性があります。

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Utf-8 エンコードを使用できない場合は、MSSQL_LCID 環境変数を使用して、選択された言語を指定するセットアップを実行します。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
Linux では、SSIS パッケージを実行できます。 詳細については、次の記事を参照してください。
-   [Linux の SSIS サポート ブログの投稿 announcing](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)です。
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

このリリースに関する次の既知の問題に注意してください。

- **Mssql サーバーが**Ubuntu と Red Hat Enterprise Linux (RHEL) のこのリリースではパッケージがサポートされています。

- Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

- Linux で SSIS パッケージを実行すると、このリリースでは、次の機能はサポートされていません。
  - SSIS カタログ データベース
  - SQL エージェントがスケジュールされているパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS のスケール アウト
  - SSIS 用 azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターはサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="RC1"></a>RC1 (2017 年 7 月)
このリリースの SQL Server エンジンのバージョンは、14.0.800.90 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありませんに注意してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.800.90-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.800.90-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.800.90-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.800.90-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.800.90-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.800.90-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.800.90-2_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [Windows 用 SQL Server Management Studio (SSMS)](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 |

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | トランザクション レプリケーション |
| &nbsp; | マージ レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | Machine Learning サービス |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **SQL Server エージェント** |  サブシステム: CmdExec、PowerShell、キュー リーダーは、SSIS、SSAS、SSRS |
| &nbsp; | 警告 |
| &nbsp; | ログ リーダー エージェント (Log Reader Agent) |
| &nbsp; | 変更データ キャプチャ |
| &nbsp; | 管理対象のバックアップ |
| **高可用性** | データベース ミラーリング  |
| &nbsp; | 可用性グループのローリング アップグレード |
| **セキュリティ** | 拡張キー管理 |
| **サービス** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
次のセクションでは、Linux 上の SQL Server 2017 RC1 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**: の言語を変更、 **sa**を使用してログイン、 **ALTER LOGIN**ステートメントです。

#### <a name="databases"></a>データベース

- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="remote-database-files"></a>リモートのデータベース ファイル

- このリリースでは、NFS サーバー上のデータベース ファイルをホストすることはできません。 これは、NFS を使用して、共有ディスクに対してフェールオーバー クラスタ リングのデータベースと非クラスター化インスタンスに含まれています。 今後のリリースで NFS サーバーのサポートを有効にすると現在取り組んでいます。

#### <a name="cross-platform-availability-groups-and-distributed-availability-groups"></a>クロス プラットフォームの可用性グループと分散型可用性グループ

- 既知の問題により Windows と Linux の両方でホストされているインスタンス上のレプリカを可用性グループを作成するが動作していないこのリリースでします。 これには、分散型可用性グループが含まれます。 修正プログラムは今後のリリース候補のビルドで使用できます。 

#### <a name="server-collation"></a>[サーバー照合順序]

- ときに、上書き、MSSQL_COLLATION を使用してまたはローカライズ (英語以外) のインストールを実施する際に可能であれば、ダンプを生成するサーバー照合順序を設定しようとしています。 SQL Server でデッドロックがヒットします。 セットアップは、しかしサーバー照合順序が設定されていない正常に完了しません。 回避策を実行するだけです。/mssql conf セット-照合順序が表示されたら目的の照合順序名を入力 (行では、エラー ログで照合順序名が見つかりません:"... に既定の照合順序を変更しようとしています")。 
 
#### <a name="localization"></a>ローカライズ

- ロケールが英語 (en_us) のセットアップ中にでない場合は、bash セッションとターミナルで utf-8 のエンコードを使用する必要があります。 ASCII エンコーディングを使用する場合は、次のようなエラーを参照してください可能性があります。

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Utf-8 エンコードを使用できない場合は、MSSQL_LCID 環境変数を使用して、選択された言語を指定するセットアップを実行します。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name = "fci"></a>共有ディスク クラスター インスタンスのアップグレード

RC1 では、クラスター リソースのエージェントは、Windows 上のフェールオーバー クラスター インスタンスで行われるように、仮想サーバー名を設定します。 RC1 より前`@@servername`特定のノードが返される共有ディスク クラスター フェールオーバー後に名前`@@servername`別の値が返されます。 RC1 では、リソースがクラスターに追加されたときにリソース名を持つ共有ディスク クラスター インスタンスのサーバー名が更新されます。 このため、クラスターは、次の手順と同様に、アップグレード中に手動フェールオーバー後に、SQL Server を再起動して必要があります。

1. 最初にセカンダリ (パッシブ) のクラスター ノードをアップグレードします。
   - アップグレード**mssql サーバー**パッケージです。
   - アップグレード**mssql サーバー-ha**パッケージです。
1. 手動でアップグレード済みのノードにフェールオーバーします。
   `pcs resource move <resourceName>`
   - リソース エージェント実際、期待されるサーバー名を確認するために、リソースが最初に失敗します。 必要なサーバー名が変更されます。
   - クラスターには、同じノード上の SQL Server リソースが再起動します。 これにより、サーバー名が更新されます。
1. その他のノードをアップグレードします。 
   - アップグレード**mssql サーバー**パッケージです。
   - アップグレード**mssql サーバー-ha**パッケージです。
1. 手動のリソースの移動によって追加された制約を削除します。 参照してください[フェールオーバー クラスターを手動で](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md#failManual)です。
2. 必要な場合、元のプライマリ ノードにフェールバックします。 

#### <a name="availability-group"></a>可用性グループ

Linux では、RC1 へのローリング SQL Server 2017 CTP 2.1 のアップグレードはサポートされません。 セカンダリ レプリカをアップグレードした後は、プライマリ レプリカがアップグレードされるまで、プライマリ レプリカから切断されます。 Microsoft が将来のリリースでこの問題を解決しようとしています。

#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- **Mssql サーバーが**パッケージがこのリリースで SUSE でサポートされていません。 Ubuntu と Red Hat Enterprise Linux (RHEL) でサポートされています。

- Linux で SSIS パッケージを実行すると、このリリースでは、次の機能はサポートされていません。
  - SSIS カタログ データベース
  - SQL エージェントがスケジュールされているパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS のスケール アウト
  - SSIS 用 azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

Linux 上の SSIS の詳細については、次の記事を参照してください。
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターはサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp21"></a>CTP 2.1 (2017 年 5 月)
このリリースの SQL Server エンジンのバージョンは、14.0.600.250 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE]
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありません。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.600.250-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.600.250-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.600.250-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.600.250-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.600.250-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.600.250-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.600.250-2_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [Windows 用 SQL Server Management Studio (SSMS)](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (1.12) |

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
次のセクションでは、Linux 上の SQL Server 2017 CTP 2.1 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**: の言語を変更、 **sa**を使用してログイン、 **ALTER LOGIN**ステートメントです。

#### <a name="databases"></a>データベース
- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="always-on-availability-group"></a>Always On 可用性グループ
- `sys.fn_hadr_backup_is_preffered_replica`に対しては機能しません`CLUSTER_TYPE=NONE`または`CLUSTER_TYPE=EXTERNAL`WSFC でレプリケートされたクラスターのレジストリに依存しているためにキーを使用できません。 別の関数で同様の機能を提供に取り組んでいます。 

#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

#### <a name="sql-agent"></a>SQL エージェント
- 次のコンポーネントおよびサブシステムの SQL エージェント ジョブの現在サポートされていない Linux 上。

    - サブシステム: CmdExec、PowerShell、レプリケーション ディストリビューターが、スナップショット、マージ、キュー リーダーは、SSIS、SSAS、SSRS
    - 警告
    - データベース メール
    - ログ リーダー エージェント (Log Reader Agent) 
    - 変更データ キャプチャ

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

  - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

#### <a name="ssis"></a> SQL Server Integration Services (SSIS)
Linux では、SSIS パッケージを実行できます。 詳細については、次を参照してください。、 [Linux の SSIS サポート ブログの投稿 announcing](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)です。 このリリースに関する次の既知の問題に注意してください。

- **Mssql サーバーが**パッケージが Ubuntu でこの時点でのみサポートされています。

- Linux 上の SSIS パッケージを実行するときに、次の機能がサポートされていません。
  - SSIS カタログ DB
  - SQL エージェントによってパッケージの実行のスケジュール設定します。
  - [Windows 認証]
  - サード パーティのコンポーネント
  - サード パーティ製の ODBC ドライバー
  - ODBC 接続マネージャー、ソース、および変換先 (Linux CTP 2.1 の更新に関する SSIS によるサポート)
  - 変更データ キャプチャ (CDC)
  - Scale Out
  - Azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

Linux CTP 2.1 の更新で、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターはサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp20"></a>CTP 2.0 (2017 年 4 月)
このリリースの SQL Server エンジンのバージョンは、14.0.500.272 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS と 16.10 | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありませんに注意してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.500.272-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.500.272-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.500.272-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |
| Ubuntu 16.10 Debian パッケージ | 14.0.500.272-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.2.1 より) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
次のセクションは、Linux 上の SQL Server 2017 CTP 2.0 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**: の言語を変更、 **sa**を使用してログイン、 **ALTER LOGIN**ステートメントです。

#### <a name="databases"></a>データベース
- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="always-on-availability-group"></a>Always On 可用性グループ
- つまり、可用性グループが事前 CTP2.0 パッケージで作成された - ペース クラスター リソースとして追加 - すべての HA 構成は、新しいパッケージとの下位互換性でがありません。 以前に構成したクラスター化されたリソースをすべて削除し、新しい可用性グループを作成`CLUSTER_TYPE=EXTERNAL`です。 参照してください[Always On 構成する可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)です。
- 可用性グループで作成された`CLUSTER_TYPE=NONE`アップグレード後に、クラスター内のリソースが仕事を続けるには追加されません。 読み取りスケールのシナリオに使用します。 参照してください[Linux に SQL Server の読み取りスケール可用性グループを構成する](sql-server-linux-availability-group-configure-rs.md)です。
- `sys.fn_hadr_backup_is_preffered_replica`に対しては機能しません`CLUSTER_TYPE=NONE`または`CLUSTER_TYPE=EXTERNAL`WSFC でレプリケートされたクラスターのレジストリに依存しているためにキーを使用できません。 別の関数で同様の機能を提供に取り組んでいます。 

#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

- 韓国語のワード ブレーカーは、読み込みに数秒かかり、初回使用時にエラーを生成します。 この最初のエラーの後に、通常どおりにします。

#### <a name="sql-agent"></a>SQL エージェント
- 次のコンポーネントおよびサブシステムの SQL エージェント ジョブの現在サポートされていない Linux 上。

    - サブシステム: CmdExec、PowerShell、レプリケーション ディストリビューターが、スナップショット、マージ、キュー リーダーは、SSIS、SSAS、SSRS
    - 警告
    - データベース メール
    - ログ リーダー エージェント (Log Reader Agent) 
    - 変更データ キャプチャ

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターはサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp14"></a>CTP 1.4 (2017 年 3 月)
このリリースの SQL Server エンジンのバージョンは、14.0.405.198 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS と 16.10 | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 以下のインストール ガイドで手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありません。
-   [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
-   [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
-   [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.405.200-1 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.405.200-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.405.200-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |
| Ubuntu 16.10 Debian パッケージ | 14.0.405.200-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.2.1 より) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
次のセクションは、Linux 上の SQL Server 2017 CTP 1.4 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- コマンドを実行できません`ALTER SERVICE MASTER KEY REGENERATE`です。 SQL Server が不安定になると、既知のバグがあります。 サービス マスター _ キーを再生成する必要がある場合、データベース ファイルをバックアップをアンインストールし、SQL Server を再インストールしてください、データベース ファイルを再度復元します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- Linux でのいくつかのタイム ゾーン名は、Windows タイム ゾーン名に正確にマップされません。

    - **解像度**: TZID 列からタイム ゾーン名を使用して、' のマッピング: 上の Windows のセクションでテーブル、 [Unicode.org ドキュメント ページ](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)です。

- SQL Server エンジンでは、CR LF (Windows 形式の行の書式設定) で終了するテキスト ファイルの行が必要です。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- すべてのログ ファイルと、エラー ログは、utf-16 でエンコードします。

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- **CREATE ASSEMBLY**ファイルを使用しようとするときは機能しません。 使用して、 **FROM\<ビット\>**メソッド代わりに今のところです。 

#### <a name="databases"></a>データベース
- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="always-on-availability-group"></a>Always On 可用性グループ
- Always On 可用性グループ HA パッケージ (mssql サーバー-ha) をアップグレードした後、CTP 1.3 を使用して作成された Linux 上のクラスター化されたリソースは失敗します。 

   - **解像度**: HA パッケージをアップグレードする前に、クラスター リソース パラメーターを設定`notify=true`です。 
   
      - 次の例は、という名前のリソースをクラスター リソース パラメーターを設定**ag1** RHEL または Ubuntu: 

      ```bash
      sudo pcs resource update ag1-master notify=true
      ```

      - SLES の更新を追加する可用性グループ リソース構成`notify=true`です。  

      ```bash
      crm configure edit ms-ag_cluster 
      ```

      追加`notify=true`リソースの構成を保存します。

- Always On 可用性グループで Linux される場合がありますデータが失われる場合、レプリカが同期コミット モードでします。 Linux ディストリビューションに応じて、詳細を参照してください。 

   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

- 韓国語のワード ブレーカーは、読み込みに数秒かかり、初回使用時にエラーを生成します。 この最初のエラーの後に、通常どおりにします。

#### <a name="sql-agent"></a>SQL エージェント
- 次のコンポーネントおよびサブシステムの SQL エージェント ジョブの現在サポートされていない Linux 上。
    - サブシステム: CmdExec、PowerShell、レプリケーション ディストリビューターが、スナップショット、マージ、キュー リーダーは、SSIS、SSAS、SSRS
    - 警告
    - データベース メール
    - ログ配布
    - ログ リーダー エージェント (Log Reader Agent) 
    - 変更データ キャプチャ

#### <a name="in-memory-oltp"></a>インメモリ OLTP
- インメモリ OLTP データベースは、/var/opt/mssql ディレクトリにのみ作成できます。 詳細については、次を参照してください。、 [、インメモリ OLTP トピック](sql-server-linux-performance-get-started.md#use-in-memory-oltp)です。

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターがサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- ファイル ブラウザーがだけに制限は、"c:\\"var/に解決されることを選択/mssql/Linux 上のスコープです。 その他のパスを使用する UI 操作のスクリプトを生成し、c: を置き換える\\Linux パスのパス。 SSMS で、スクリプトを手動で実行しています。

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp13"></a>CTP 1.3 (2017 年 2 月)
このリリースの SQL Server エンジンのバージョンは、14.0.304.138 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS と 16.10 | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で最大 1 TB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 」の手順を使用する場合に、これらをダウンロードする必要はありませんが直接パッケージ化、[環境向けインストール ガイド](sql-server-linux-setup.md)です。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.304.138-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[mssql サーバー-ha 高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[mssql サーバー-fts フル テキスト検索 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.304.138-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[mssql サーバー-ha 高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[mssql サーバー-fts フル テキスト検索 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.304.138-1 | [mssql server エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[mssql サーバー-ha 高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[mssql サーバー-fts フル テキスト検索 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |
| Ubuntu 16.10 Debian パッケージ | 14.0.304.138-1 | [mssql server エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[mssql サーバー-ha 高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[mssql サーバー-fts フル テキスト検索 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio - Release Candidate 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.2.1 より) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server エージェント |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
以降のセクションでは、Linux 上の SQL Server 2017 CTP 1.3 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- コマンドを実行できません`ALTER SERVICE MASTER KEY REGENERATE`です。 SQL Server が不安定になると、既知のバグがあります。 サービス マスター _ キーを再生成する必要がある場合、データベース ファイルをバックアップをアンインストールし、SQL Server を再インストールしてください、データベース ファイルを再度復元します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- Linux でのいくつかのタイム ゾーン名は、Windows タイム ゾーン名に正確にマップされません。

    - **解像度**: TZID 列からタイム ゾーン名を使用して、' のマッピング: 上の Windows のセクションでテーブル、 [Unicode.org ドキュメント ページ](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)です。

- SQL Server エンジンでは、CR LF (Windows 形式の行の書式設定) で終了するテキスト ファイルの行が必要です。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- すべてのログ ファイルと、エラー ログは、utf-16 でエンコードします。

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- **CREATE ASSEMBLY**ファイルを使用しようとするときは機能しません。 使用して、 **FROM\<ビット\>**メソッド代わりに今のところです。 

#### <a name="databases"></a>データベース
- TempDB データ ファイルとログ ファイルの場所を変更することはサポートされていません。

- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

- Always On 可用性グループで Linux される場合がありますデータが失われる場合、レプリカが同期コミット モードでします。 参照先 
 
   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   
#### <a name="full-text-search"></a>フルテキスト検索
- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

- 韓国語のワード ブレーカーは、読み込みに数秒かかり、初回使用時にエラーを生成します。 この最初のエラーの後に、通常どおりにします。

#### <a name="in-memory-oltp"></a>インメモリ OLTP
- インメモリ OLTP データベースは、/var/opt/mssql ディレクトリにのみ作成できます。 詳細については、次を参照してください。、 [、インメモリ OLTP トピック](sql-server-linux-performance-get-started.md#use-in-memory-oltp)です。  

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 ファイルをマップする相対パスを使用して、"/tmp/sqlpackage./ <code/> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd と BCP & ODBC 
- SQL Server コマンド ライン ツール (mssql ツール) と ODBC ドライバー (移動) は、カスタムの unixODBC ドライバー マネージャーによって異なります。 これにより、以前にインストールされた unixODBC ドライバー マネージャーがある場合、競合をします。 

    - **解像度**: Ubuntu での競合は自動的に解決します。 既存の unixODBC ドライバー マネージャーをアンインストールするにはメッセージが表示されたら、'y' と入力し、インストールを続行します。 既存の unixODBC ドライバー マネージャーを手動で削除する必要が、Hat でを使用して`yum remove unixODBC`です。 おは、開発中 RHEL、SUSE におけるこの制限を修正する必要がある更新プログラムをすぐにします。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターがサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- SQL Server エージェントがまだサポートされていません。 したがって、SSMS で SQL Server エージェント機能は、現時点で Linux で動作しないしません。

- ファイル ブラウザーがだけに制限は、"c:\\"var/に解決されることを選択/mssql/Linux 上のスコープです。 その他のパスを使用する UI 操作のスクリプトを生成し、c: を置き換える\\Linux パスのパス。 SSMS で、スクリプトを手動で実行しています。

- 保持するログ ファイルの数を変更できません。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp12-ctp-12-january-2017"></a><a id="ctp12">CTP 1.2 (2017 年 1 月)
このリリースの SQL Server エンジンのバージョンは、14.0.200.24 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS と 16.10 | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンだけだったこの時点で最大 256 GB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 」の手順を使用する場合に、これらをダウンロードする必要はありませんが直接パッケージ化、[環境向けインストール ガイド](sql-server-linux-setup.md)です。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| RPM パッケージ | 14.0.200.24-2 | [mssql サーバー 14.0.200.24-2 エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.200.24-2.x86_64.rpm)</br>[mssql server 14.0.200.24-2 の高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.200.24-2.x86_64.rpm) | 
| Debian パッケージ | 14.0.200.24-2 | [mssql サーバー 14.0.200.24-2 エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.200.24-2_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.2) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | フルテキスト検索  |
| &nbsp; | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | Always On 可用性グループ |
| &nbsp; | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server エージェント |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
以降のセクションでは、Linux 上の SQL Server 2017 CTP 1.2 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- コマンドを実行できません`ALTER SERVICE MASTER KEY REGENERATE`です。 SQL Server が不安定になると、既知のバグがあります。 サービス マスター _ キーを再生成する必要がある場合、データベース ファイルをバックアップをアンインストールし、SQL Server を再インストールしてください、データベース ファイルを再度復元します。

- リソース名 SQL リソース ocf:sql:fci から ocf:mssql:fci に変更します。 検索できる共有ディスク フェールオーバー クラスターの構成の詳細について[ここ](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure)です。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- Linux でのいくつかのタイム ゾーン名は、Windows タイム ゾーン名に正確にマップされません。

    - **解像度**: TZID 列からタイム ゾーン名を使用して、' のマッピング: 上の Windows のセクションでテーブル、 [Unicode.org ドキュメント ページ](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)です。

- SQL Server エンジンでは、CR LF (Windows 形式の行の書式設定) で終了するテキスト ファイルの行が必要です。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- すべてのログ ファイルと、エラー ログは、utf-16 でエンコードします。

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- **CREATE ASSEMBLY**ファイルを使用しようとするときは機能しません。 使用して、 **FROM\<ビット\>**メソッド代わりに今のところです。 

#### <a name="databases"></a>データベース
- TempDB データ ファイルとログ ファイルの場所を変更することはサポートされていません。

- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="in-memory-oltp"></a>インメモリ OLTP
- インメモリ OLTP データベースは、/var/opt/mssql ディレクトリにのみ作成できます。 これらのデータベースが必要もあります、"c:\\"参照される場合に表記されます。 詳細については、次を参照してください。、 [、インメモリ OLTP トピック](sql-server-linux-performance-get-started.md#use-in-memory-oltp)です。  

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd と BCP & ODBC 
- 以前のバージョンの SQL Server コマンド ライン ツール (mssql ツール) および ODBC ドライバー (移動) がある場合は、カスタム unixODBC ドライバー マネージャー (unixODBC utf16) がインストールされている可能性があります。 今後使用しないカスタム ドライバー マネージャーとは、この競合の可能性があります。 

    - **解像度**: Ubuntu と SLES では、競合は自動的に解決します。 既存の unixODBC ドライバー マネージャーをアンインストールするにはメッセージが表示されたら、'y' と入力し、インストールを続行します。 Hat では、既存の unixODBC ドライバー マネージャーを手動で削除する必要を使用して`yum remove unixODBC-utf16 unixODBC-utf16-devel`インストールを再試行してください。
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターがサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- SQL Server エージェントがまだサポートされていません。 したがって、SSMS で SQL Server エージェント機能は、現時点で Linux で動作しないしません。

- ファイル ブラウザーがだけに制限は、"c:\\"var/に解決されることを選択/mssql/Linux 上のスコープです。 その他のパスを使用する UI 操作のスクリプトを生成し、c: を置き換える\\Linux パスのパス。 SSMS で、スクリプトを手動で実行しています。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp11-ctp-11-december-2016"></a><a id="ctp11">CTP 1.1 (2016 年 12 月)
このリリースの SQL Server エンジンのバージョンは、14.0.100.187 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS と 16.10 | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンだけだったこの時点で最大 256 GB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 」の手順を使用する場合に、これらをダウンロードする必要はありませんが直接パッケージ化、[環境向けインストール ガイド](sql-server-linux-setup.md)です。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| RPM パッケージ | 14.0.100.187-1 | [mssql サーバー 14.0.100.187-1 エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.100.187-1.x86_64.rpm)</br>[mssql server 14.0.100.187-1 の高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.100.187-1.x86_64.rpm) | 
| Debian パッケージ | 14.0.100.187-1 | [mssql サーバー 14.0.100.187-1 エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.100.187-1_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.2) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | フルテキスト検索  |
| &nbsp; | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | Always On 可用性グループ |
| &nbsp; | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server エージェント |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
以降のセクションでは、Linux 上の SQL Server 2017 CTP 1.1 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- コマンドを実行できません`ALTER SERVICE MASTER KEY REGENERATE`です。 SQL Server が不安定になると、既知のバグがあります。 サービス マスター _ キーを再生成する必要がある場合、データベース ファイルをバックアップをアンインストールし、SQL Server を再インストールしてください、データベース ファイルを再度復元します。

- リソース名 SQL リソース ocf:sql:fci から ocf:mssql:fci に変更します。 検索できる共有ディスク フェールオーバー クラスターの構成の詳細について[ここ](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure)です。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- Linux でのいくつかのタイム ゾーン名は、Windows タイム ゾーン名に正確にマップされません。

    - **解像度**: TZID 列からタイム ゾーン名を使用して、' のマッピング: 上の Windows のセクションでテーブル、 [Unicode.org ドキュメント ページ](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)です。

- SQL Server エンジンでは、CR LF (Windows 形式の行の書式設定) で終了するテキスト ファイルの行が必要です。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- すべてのログ ファイルと、エラー ログは、utf-16 でエンコードします。

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- **CREATE ASSEMBLY**ファイルを使用しようとするときは機能しません。 使用して、 **FROM\<ビット\>**メソッド代わりに今のところです。 

#### <a name="databases"></a>データベース
- TempDB データ ファイルとログ ファイルの場所を変更することはサポートされていません。

- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="in-memory-oltp"></a>インメモリ OLTP
- インメモリ OLTP データベースは、/var/opt/mssql ディレクトリにのみ作成できます。 これらのデータベースが必要もあります、"c:\"表記と呼ばれます。 詳細については、次を参照してください。、 [、インメモリ OLTP トピック](sql-server-linux-performance-get-started.md#use-in-memory-oltp)です。  

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用するには、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd と BCP & ODBC 
- SQL Server コマンド ライン ツール (mssql ツール) と ODBC ドライバー (移動) は、カスタムの unixODBC ドライバー マネージャーによって異なります。 これにより、以前にインストールされた unixODBC ドライバー マネージャーがある場合、競合をします。 

    - **解像度**: Ubuntu での競合は自動的に解決します。 既存の unixODBC ドライバー マネージャーをアンインストールするにはメッセージが表示されたら、'y' と入力し、インストールを続行します。 既存の unixODBC ドライバー マネージャーを手動で削除する必要が、Hat でを使用して`yum remove unixODBC`です。 おは、開発中 RHEL、SUSE におけるこの制限を修正する必要がある更新プログラムをすぐにします。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターがサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- SQL Server エージェントがまだサポートされていません。 したがって、SSMS で SQL Server エージェント機能は、現時点で Linux で動作しないしません。

- ファイル ブラウザーがだけに制限は、"c:\\"var/に解決されることを選択/mssql/Linux 上のスコープです。 その他のパスを使用する UI 操作のスクリプトを生成し、c: を置き換える\\Linux パスのパス。 SSMS で、スクリプトを手動で実行しています。

v

![分割バー グラフィック](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp10-ctp-10-november-2016"></a><a id="ctp10">CTP 1.0 (2016 年 11 月)
このリリースの SQL Server エンジンのバージョンは、14.0.1.246 です。

### <a name="supported-platforms"></a>サポートされているプラットフォーム 

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.2 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS | EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンだけだったこの時点で最大 256 GB のメモリをテストします。

### <a name="package-details"></a>パッケージの詳細
パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 」の手順を使用する場合に、これらをダウンロードする必要はありませんが直接パッケージ化、[環境向けインストール ガイド](sql-server-linux-setup.md)です。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| RPM パッケージ | 14.0.1.246-6 | [mssql サーバー 14.0.1.246-6 エンジン RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.1.246-6.x86_64.rpm)</br>[mssql server 14.0.1.246-6 の高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.1.246-6.x86_64.rpm) | 
| Debian パッケージ | 14.0.1.246-6 | [mssql サーバー 14.0.1.246-6 エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.1.246-6_amd64.deb) |

### <a name="supported-client-tools"></a>サポートされているクライアント ツール

| ツール | 最小バージョン |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio - リリース候補 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)で、 [mssql 拡張機能](https://aka.ms/mssql-marketplace) | 最新 (0.1.5) |

> [!NOTE] 
> 指定されたバージョンの SQL Server Management Studio と SQL Server Data Tools のバージョン以上はリリース候補、そのため、実稼働環境で使用するため推奨されません。

### <a name="unsupported-features-and-services"></a>サポートされていない機能とサービス
次の機能とサービスは現時点では Linux で使用できません。 プレビュー プログラムの毎月の反復の更新中に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | フルテキスト検索  |
| &nbsp; | レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| **高可用性** | Always On 可用性グループ |
| &nbsp; | データベース ミラーリング  |
| **セキュリティ** | Active Directory 認証 |
| &nbsp; | [Windows 認証] |
| &nbsp; | 拡張キー管理 |
| &nbsp; | SSL または TLS をユーザーに指定された証明書の使用 |
| **サービス** | SQL Server エージェント |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | マスター データ サービス |

### <a name="known-issues"></a>既知の問題
以降のセクションでは、Linux 上の SQL Server 2017 CTP1 のこのリリースの既知の問題を記述します。

#### <a name="general"></a>全般
- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- Linux でのいくつかのタイム ゾーン名は、Windows タイム ゾーン名に正確にマップされません。

    - **解像度**: TZID 列からタイム ゾーン名を使用して、' のマッピング: 上の Windows のセクションでテーブル、 [Unicode.org ドキュメント ページ](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)です。

- SQL Server エンジンでは、CR LF (Windows 形式の行の書式設定) で終了するテキスト ファイルの行が必要です。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- すべてのログ ファイルと、エラー ログは、utf-16 でエンコードします。

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- **CREATE ASSEMBLY**ファイルを使用しようとするときは機能しません。 使用して、 **FROM\<ビット\>**メソッド代わりに今のところです。

#### <a name="databases"></a>データベース
- TempDB データ ファイルとログ ファイルの場所を変更することはサポートされていません。

- Mssql conf ユーティリティを使用してシステム データベースを移動することはできません。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 分散トランザクションがサポートされている SQL Server を SQL Server。

#### <a name="in-memory-oltp"></a>インメモリ OLTP
- インメモリ OLTP データベースは、/var/opt/mssql ディレクトリにのみ作成できます。 これらのデータベースが必要もあります、"c:\\"参照される場合に表記されます。 詳細については、次を参照してください。、 [、インメモリ OLTP トピック](sql-server-linux-performance-get-started.md#use-in-memory-oltp)です。  

#### <a name="sqlpackage"></a>SqlPackage
- SqlPackage を使用して、ファイルの絶対パスを指定する必要があります。 "/Tmp sqlpackage 下のファイルの相対パスを使用してマップされます。\<コード \> /システム/system32"フォルダーです。 

    - **解像度**: 絶対ファイル パスを使用します。

- SqlPackage を持つファイルの場所を示しています、"c:\\"プレフィックス。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd と BCP & ODBC 
- SQL Server コマンド ライン ツール (mssql ツール) と ODBC ドライバー (移動) は、カスタムの unixODBC ドライバー マネージャーによって異なります。 これにより、以前にインストールされた unixODBC ドライバー マネージャーがある場合、競合をします。 

    - **解像度**: Ubuntu での競合は自動的に解決します。 既存の unixODBC ドライバー マネージャーをアンインストールするにはメッセージが表示されたら、'y' と入力し、インストールを続行します。 既存の unixODBC ドライバー マネージャーを手動で削除する必要が、Hat でを使用して`yum remove unixODBC`です。 おは、開発中 RHEL、SUSE におけるこの制限を修正する必要がある更新プログラムをすぐにします。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターがサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- SQL Server エージェントがまだサポートされていません。 したがって、SSMS で SQL Server エージェント機能は、現時点で Linux で動作しないしません。

- ファイル ブラウザーがだけに制限は、"c:\\"var/に解決されることを選択/mssql/Linux 上のスコープです。 その他のパスを使用する UI 操作のスクリプトを生成し、c: を置き換える\\Linux パスのパス。 SSMS で、スクリプトを手動で実行しています。

### <a name="next-steps"></a>次の手順

開始するには、次のクイック スタート チュートリアルを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

