---
title: SQL Server on Linux の FAQ |Microsoft Docs
description: この記事では、Linux で実行されている SQL Server についてよく寄せられる質問に対する回答を提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 448db7c77d26e06651e01a7e790917757aff0e9d
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713604"
---
# <a name="sql-server-on-linux-frequently-asked-questions-faq"></a>SQL Server on Linux Frequently Asked Questions (FAQ)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次のセクションでは、SQL Server on Linux を実行しているに対して、一般的な質問と回答を提供します。

## <a name="general-questions"></a>一般的な質問

1. **どのような Linux プラットフォームがサポートされますか。**

   Red Hat Enterprise Server、SUSE Linux Enterprise Server、および Ubuntu では、SQL Server が現在サポートされています。 また、docker コンテナーで実行もサポートされます。 サポートされているバージョンに関する最新情報については、次を参照してください。[サポートされているプラットフォーム](sql-server-linux-setup.md#supportedplatforms)します。

1. **SQL Server on Linux を他のプラットフォームで動作**でしょうか。

   SQL Server をテストして、上記のディストリビューションの Linux ではサポートされています。 他の Linux ディストリビューションは密接に関連し、SQL Server を実行できる可能性があります (たとえば、CentOS、密接に関連する Red Hat Enterprise Server)。 サポートされていないオペレーティング システムに SQL Server をインストールする場合は、確認しますが、**サポート ポリシー**のセクション、 [for Microsoft SQL Server のテクニカル サポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)サポートを理解するには影響します。 いくつかコミュニティに維持される Linux ディストリビューションには、基になるオペレーティング システムが問題である場合は、サポートを受ける形式的な方法はありません。 にも注意してください。

1. **どのように Linux 上のライセンスの機能ですか。**

   SQL Server では、Windows と Linux の両方の同様のライセンスします。 実際には、SQL Server のライセンスを取得して、そのライセンスを使用して、好みのプラットフォーム上に選択できます。 詳細については、次を参照してください。 [SQL Server のライセンス方法](https://www.microsoft.com/sql-server/sql-server-2017-pricing)します。

1. **Linux 上の SQL Server を Windows と同じですか。**

   Core for SQL Server データベース エンジンは、Windows 上にある Linux で同じです。 ただし、一部の機能は現在サポートされていません Linux 上。 Linux でサポートされていない機能の一覧は、次を参照してください。、[機能とサービスがサポートされていない](sql-server-linux-release-notes.md#Unsupported)します。 確認することも、[既知の問題](sql-server-linux-release-notes.md#known-issues)します。 これらのリストで指定されている場合を除き、他の SQL Server の機能とサービスは、Linux でサポートされます。

1. **SQL Server のサポート ポリシーとは何ですか。**

   サポート ポリシーについては、確認、 [for SQL Server 技術のサポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)します。

1. **SQL Server の Windows のバック グラウンドからです。Linux 上の SQL Server を使用する方法を確認するのに役立つリソースはありますか。**

   [クイック スタート](sql-server-linux-setup.md#platforms)Linux 上の SQL Server をインストールし、TRANSACT-SQL クエリを実行する方法の詳細な手順を説明します。 その他のチュートリアルでは、Linux 上の SQL Server を使用して追加についてを説明します。 ヒントのサードパーティの一覧は、次を参照してください。、 [SQL Server on Linux のヒントの一覧を MSSQLTIPS](https://www.mssqltips.com/sql-server-tip-category/226/sql-server-on-linux/)します。

## <a name="installation"></a>インストール

1. **Linux サーバーにインストールされている SQL Server を取得する方法はありますか**

   Microsoft SQL Server をインストールするためのパッケージ リポジトリを管理および yum、zypper などのネイティブのパッケージ マネージャーを使用してインストールをサポートし、apt します。 を迅速にインストールするには、のいずれかを表示、[クイック スタート](sql-server-linux-setup.md#platforms)します。

1. **Windows 10 の Linux サブシステム用に SQL Server をインストールできますか。**

   No. 現在、Windows 10 で実行されている Linux は SQL Server と関連ツールのサポートされているプラットフォームではできません。

1. **SQL Server はデータ ファイルに対して、どの Linux ファイル システムを使用できますか。**

   現在 SQL Server on Linux には、ext4、XFS がサポートしています。 今後必要に応じて、他のファイル システムのサポートが追加されます。

1. **SQL Server をオフラインでインストールするインストール パッケージをダウンロードできますか。**

   可能。 詳細については、パッケージのダウンロードのリンクを参照してください、[リリース ノート](sql-server-linux-release-notes.md)します。 また、確認、[オフライン インストールで手順](sql-server-linux-setup.md#offline)します。

1. **Linux に SQL Server の無人インストールを実行できますか。**

   可能。 無人インストールの詳細については、次を参照してください。 [Linux 上の SQL Server のインストールのガイダンスについて](sql-server-linux-setup.md#unattended)します。 サンプル スクリプトを参照してください。 [Red Hat](sample-unattended-install-redhat.md)、 [SUSE Linux Enterprise Server](sample-unattended-install-suse.md)、および[Ubuntu](sample-unattended-install-ubuntu.md)します。 確認することも[このサンプル スクリプト](https://blogs.msdn.microsoft.com/sqlcat/2017/10/03/unattended-install-and-configuration-for-sql-server-2017-on-linux/)SQL Server Customer Advisory チームによって作成します。

## <a name="tools"></a>ツール

1. **クライアント使用できます、SQL Server Management Studio で Windows SQL Server on Linux にアクセスするのにでしょうか。**

   はい、SQL Server on Linux へのアクセスに Windows 上で実行されるすべての既存のツールを使用することができます。 Microsoft SQL Server Management Studio (SSMS)、SQL Server Data Tools (SSDT) と OSS などのツールとサード パーティのツールが含まれます。

1. **Linux 上で実行される SSMS などのツールはありますか。**

   新しい Azure Data Studio (プレビュー) は、SQL Server を管理するためのクロスプラット フォーム ツールです。 詳細については、次を参照してください。 [Azure データ Studio (プレビュー) は](../azure-data-studio/what-is.md)します。

1. **Sqlcmd および bcp のようなコマンドは、Linux で利用可能ですか。**

   はい、 [sqlcmd および bcp](sql-server-linux-setup-tools.md)は Linux、macOS、および Windows でネイティブに利用できます。 さらに、新しい使用[mssql scripter](https://github.com/Microsoft/mssql-scripter)任意の場所を実行している SQL データベースに対して T-SQL スクリプトを生成するには、Linux、macOS、または Windows のコマンド ライン ツール。 また、リリースのプレビューを表示[mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)します。

1. **Linux でインスタンスの Windows 上の SSMS を通して接続したときの利用状況モニターを表示することを実行するでしょうか。**

   はい、Windows で SSMS を使用してリモートで接続でき、ツール]/[などの機能の使用の Linux インスタンスの利用状況モニターのコマンドとして。

1. **どのようなツールは、Linux 上の SQL Server のパフォーマンスの監視に使用できるでしょうか。**

   使用することができます[システム動的管理ビュー (Dmv)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)をさまざまな種類の SQL Server、Linux プロセス情報などに関する情報を収集します。 使用することができます[クエリ ストア](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)クエリのパフォーマンスを向上させるためにします。 組み込みなどの他のツールでは、[パフォーマンス ダッシュ ボード](https://blogs.msdn.microsoft.com/sql_server_team/new-in-ssms-performance-dashboard-built-in/)、リモートでの SQL Server Management Studio (SSMS) Windows から作業します。

   > [!TIP]
   > パフォーマンスを向上させる方法の 1 つでは、Linux オペレーティング システムと SQL Server インスタンスを適切に構成します。 詳細については、次を参照してください。[パフォーマンスのベスト プラクティスと SQL Server on Linux の構成ガイドライン](sql-server-linux-performance-best-practices.md)します。

## <a name="administration"></a>管理

1. **Microsoft が on Linux で、SQL Server 構成マネージャーのようにアプリを作成しますか。**

   はい、SQL Server on Linux 用の構成ツールがある: [mssql conf](sql-server-linux-configure-mssql-conf.md)します。

1. **SQL Server on Linux は、同じホストで複数のインスタンスをサポートしますか。**

   複数のコンテナーを個別のインスタンスが複数存在するホストで実行されていることをお勧めします。 各コンテナーは、別のポートでリッスンする必要があります。 詳細については、次を参照してください。[複数の SQL Server のコンテナーを実行](sql-server-linux-configure-docker.md#run-multiple-sql-server-containers)します。

1. **Linux 上の Active Directory 認証はサポートされますか。**

   可能。 詳細については、次を参照してください。 [SQL Server on Linux での Active Directory 認証](sql-server-linux-active-directory-authentication.md)します。

1. **Linux でサポートされているクラスタ リングと Always On のですか。**

   Linux 上の Pacemaker では、フェールオーバー クラスタ リングと Linux での高可用性が実現します。 詳細については、次を参照してください。[ビジネス継続性とデータベース復旧 - SQL Server on Linux](sql-server-linux-business-continuity-dr.md)します。

1. **Linux Windows からおよびその逆からレプリケーションを構成することはできますか。**

   読み取りスケール レプリカは、一方向のデータ レプリケーションの Windows と Linux で使用できます。

1. **Windows から Linux に SQL Server の以前のバージョンで既存のデータベースを移行することはできますか。**

   はい、[いくつかのメソッド](sql-server-linux-migrate-overview.md)これを実現するのです。

1. **移行できますデータ Oracle および他のデータベース エンジンから SQL Server on Linux でしょうか。**

   可能。 SSMA は、いくつかの種類のデータベース エンジンからの移行をサポートしています: Microsoft Access、DB2、MySQL、Oracle、および SAP ASE (旧称 SAP Sybase ASE の場合)。 SSMA を使用する方法の例は、次を参照してください。 [Oracle スキーマを SQL Server Migration Assistant を使った Linux 上の SQL Server に移行](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json)します。

1. **どのようなアクセス許可は、SQL Server のファイルに必要なでしょうか。**

   すべてのファイル、`/var/opt/mssql`ファイル フォルダーの所有する必要がある、 **mssql**ユーザーに属し、 **mssql**グループ。 両方の**mssql**ユーザーとグループには、すべてのファイルとディレクトリの読み取り/書き込みアクセス許可を持つようにします。 ファイルとディレクトリのアクセス許可に関連する次の特殊なシナリオに注意してください。

   * Mssql 所有者とグループのアクセス許可は、マウントされたネットワーク共有される SQL Server のファイルを格納する必要があります。
   * 既定以外のディレクトリにデータベース ファイルまたはバックアップを検索する場合は、そのディレクトリのアクセス許可も設定する必要があります。
   * 0022 から既定のルートの umask を変更する場合は、インストール後に SQL Server の構成が失敗します。 SQL Server 開始アカウントに必要なアクセス許可を手動で適用して、必要があります。

1. **インストールされている mssql アカウントとグループから SQL Server のファイルとディレクトリの所有権を変更できますか。**

   既定のインストールからの SQL Server ディレクトリとファイルの所有権を変更することはできません。 Mssql アカウントとグループは、SQL Server は具体的には使用され、対話型ログイン アクセス権がありません。

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]
