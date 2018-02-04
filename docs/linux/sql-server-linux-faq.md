---
title: "SQL Server on Linux に関する FAQ |Microsoft ドキュメント"
description: "この記事では、Linux で実行されている SQL Server に関するよく寄せられる質問に対する回答を提供します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: 2da90e6cdf49531980e9014075d7b094b61271fd
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server on Linux Frequently Asked Questions (FAQ)

次のセクションでは、SQL Server on Linux を実行しているに対して、一般的な質問と回答を提供します。

## <a name="general-questions"></a>一般的な質問

1. **Linux プラットフォームがサポートされますか。**

   SQL Server は Red Hat Enterprise Server、SUSE Linux Enterprise Server、および Ubuntu で現在サポートされています。 サポートされるバージョンに関する最新情報については、次を参照してください。[サポートされているプラットフォーム](sql-server-linux-setup.md#supportedplatforms)です。

1. **Linux でサポートされるは、SQL Server 機能ですか。**

   サポートされる機能と既知の問題の一覧については、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)です。

1. **SQL Server のサポート ポリシーとは何ですか。**

   サポート ポリシーを理解するのには、確認、 [for SQL Server の技術的なサポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)です。

1. **SQL Server の Windows のバック グラウンドに由来すればいます。Linux 上の SQL Server を使用する方法を習得するためのリソースはありますか。**

   [クイック スタート](sql-server-linux-setup.md#platforms)手順 Linux に SQL Server をインストールして、TRANSACT-SQL クエリを実行する方法について説明します。 その他のチュートリアルでは、SQL Server を使用して Linux 上で追加の手順を説明します。 ヒントのサードパーティの一覧は、次を参照してください。、 [Linux ヒント SQL Server の MSSQLTIPS 一覧](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/)です。

## <a name="installation"></a>インストール

1. **Linux サーバーにインストールされている SQL Server の取得方法**

   Microsoft SQL Server をインストールするためのパッケージ リポジトリを維持および yum、zypper などのネイティブのパッケージ マネージャーを使用してインストールをサポートしている apt とします。 すぐにインストールするのいずれかの操作を参照して、[クイック スタート](sql-server-linux-setup.md#platforms)です。

1. **Linux のサブシステムの Windows 10 上に SQL Server をインストールできますか。**

   不可。 現在、Windows 10 で実行されている Linux は SQL Server および関連ツールのサポートされているプラットフォームではできません。

1. **SQL Server 2017 はデータ ファイルの Linux ファイル システムを使用できますか。**

   現在 SQL Server on Linux は、ext4 および XFS をサポートします。 後で必要に応じて、他のファイル システムのサポートが追加されます。

1. **サーバーをインストールする SQL オフライン インストール パッケージをダウンロードできますか。**

   可能。 詳細については、内のリンクのダウンロード パッケージを参照してください、[リリース ノート](sql-server-linux-release-notes.md)です。 また、確認、[オフライン インストール手順](sql-server-linux-setup.md#offline)です。

1. **Linux 上の SQL Server の無人インストールを実行**

   可能。 無人インストールの詳細については、次を参照してください。 [Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md#unattended)です。 用のサンプル スクリプトを参照してください[Red Hat](sample-unattended-install-redhat.md)、 [SUSE Linux Enterprise Server](sample-unattended-install-suse.md)、および[Ubuntu](sample-unattended-install-ubuntu.md)です。 確認することも[このサンプル スクリプト](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/)SQL Server ユーザー諮問チームによって作成します。

## <a name="tools"></a>ツール

1. **使用できます、SQL Server Management Studio クライアント Windows Linux 上の SQL Server にアクセスしますか。**

   はい、Linux 上の SQL Server にアクセスする Windows 上で実行されるすべての既存のツールを使用することができます。 これらには、Microsoft SQL Server Management Studio (SSMS)、SQL Server Data Tools (SSDT) および OSS などのツールとサード パーティのツールが含まれます。

1. **Linux 上で実行される SSMS のようなツールはありますか。**

   新しい Microsoft SQL 操作 Studio (プレビュー) は、SQL Server を管理するためのクロスプラット フォーム ツールです。 詳細については、次を参照してください。 [Microsoft SQL 操作 Studio (プレビュー) は、どのような](../sql-operations-studio/what-is.md)します。

1. **Sqlcmd および bcp のようなコマンドは、Linux で利用可能ですか。**

   はい、 [sqlcmd および bcp](sql-server-linux-setup-tools.md)は Linux、macOS、および Windows でネイティブに使用できます。 さらに、新しい使用[mssql scripter](https://github.com/Microsoft/mssql-scripter)任意の場所を実行している SQL データベースに対して T-SQL スクリプトを生成するには、Linux、macOS、または Windows コマンド ライン ツールです。 また、プレビューのリリースを参照してください[mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)です。

1. **Linux でインスタンスの Windows で SSMS を介して接続されているときに、利用状況モニターを表示することが実行されているがしますか。**

   はい、Windows で SSMS を使用するには、リモートで接続してツール]/[などの機能を使用して Linux インスタンス上の利用状況モニター コマンドとして。

1. **どのようなツールは、Linux 上の SQL Server のパフォーマンスの監視に使用できるか。**

   使用することができます[システム動的管理ビュー (Dmv)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)をさまざまな種類の SQL Server、Linux プロセス情報などに関する情報を収集します。 使用することができます[クエリのストア](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)クエリのパフォーマンスを向上させるためにします。 組み込みなど、他のツール[パフォーマンス ダッシュ ボード](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)、リモートの SQL Server Management Studio (SSMS) Windows から作業します。

## <a name="administration"></a>管理

1. **Microsoft が Linux で、SQL Server 構成マネージャーのようにアプリを作成しましたか。**

   はい、SQL Server on Linux 用の構成ツールがある: [mssql conf](sql-server-linux-configure-mssql-conf.md)です。

1. **SQL Server on Linux は、同じホストに複数のインスタンスをサポートしますか。**

   複数の個別インスタンスを持つホストで複数のコンテナーを実行していることをお勧めします。 各コンテナーは、別のポートでリッスンする必要があります。 詳細については、次を参照してください。[複数の SQL Server のコンテナー実行](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers)です。

1. **Linux でサポートされている Active Directory 認証しますか。**

   可能。 詳細については、次を参照してください。 [Linux に SQL Server と Active Directory 認証](sql-server-linux-active-directory-authentication.md)です。

1. **Linux でサポートされているクラスタ リングと Always On はか。**

   Linux 上のペースには、フェールオーバー クラスタ リングと Linux での高可用性が実現されます。 詳細については、次を参照してください。[ビジネス継続性とデータベース復旧 - SQL Server on Linux](sql-server-linux-business-continuity-dr.md)です。

1. **Windows およびその逆の Linux からレプリケーションを構成することは?**

   読み取りのスケールのレプリカは、一方向のデータ レプリケーションの Windows と Linux の間で使用できます。

1. **Windows から Linux に SQL Server の旧バージョンで既存のデータベースを移行することは?**

   はい、[いくつかの方法](sql-server-linux-migrate-overview.md)これを実現するのです。

1. **できますデータの移行は my Oracle と他のデータベース エンジンの SQL Server on Linux にしますか。**

   可能。 SSMA は、いくつかのデータベース エンジンの種類からの移行をサポートしています: Microsoft Access、DB2、MySQL、Oracle、および SAP ASE (旧称 SAP Sybase ASE)。 SSMA の使用方法の例は、次を参照してください。 [Oracle スキーマを SQL Server Migration Assistant Linux での SQL Server 2017 に移行](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json)です。

1. **SQL Server のファイルに必要なアクセス許可しますか。**

   すべてのファイル、`/var/opt/mssql`ファイル フォルダーを所有する必要があります、 **mssql**ユーザーに属し、 **mssql**グループ。 両方の**mssql**ユーザーとグループは、すべてのファイルとディレクトリの読み取り/書き込みアクセス許可を持つ必要があります。 ファイルとディレクトリのアクセス許可に関連する次の特殊なシナリオに注意してください。

   * Mssql 所有者およびグループのアクセス許可は、マウントされているネットワーク共有 SQL Server のファイルの格納に使用する必要があります。
   * 既定以外のディレクトリにデータベース ファイルまたはバックアップを検索する場合も、そのディレクトリのアクセス許可を設定する必要があります。
   * 0022 から既定のルート umask を変更する場合は、インストール後に SQL Server の構成が失敗します。 SQL Server 起動アカウントに必要なアクセス許可を手動で適用して、必要があります。

1. **インストールされている mssql アカウントおよびグループから SQL Server のファイルとディレクトリの所有権を変更できますか。**

   既定のインストールからの SQL Server ディレクトリとファイルの所有権の変更はサポートされていません。 Mssql アカウントとグループは、SQL Server が具体的には使用され、対話型ログイン アクセス権がありません。

## <a name="next-steps"></a>次の手順

詳細については、Linux 上の SQL Server を実行して、次を参照してください。、 [Linux に SQL Server の概要](sql-server-linux-overview.md)です。