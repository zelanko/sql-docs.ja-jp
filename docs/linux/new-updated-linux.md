---
title: 更新済み - SQL Server on Linux docs |Microsoft ドキュメント
description: 最近変更したドキュメントについては、Microsoft SQL Server on Linux の更新されたコンテンツのスニペットを表示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 3b7ed71be06ee7e485236fa0e244e47bb77b3b70
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334016"
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *サブジェクト領域:* &nbsp; **Microsoft SQL Server on Linux**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [Linux 上の SQL Server の active Directory 認証](sql-server-linux-active-directory-auth-overview.md)
2. [構成する SQL Server Always On 可用性グループを Windows および Linux (プラットフォーム) 間に](sql-server-linux-availability-group-cross-platform.md)
3. [Linux 上の可用性グループに対して常に実行します。](sql-server-linux-availability-group-operate-ha.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [インストールして、Linux 上の SQL Server をアップグレードするためのリポジトリを構成します。](#TitleNum_1)
2. [Mssql conf ツールを使用して Linux 上の SQL Server を構成します。](#TitleNum_2)
3. [Linux 上の SQL Server 2017 のリリース ノート](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-repositories-for-installing-and-upgrading-sql-server-on-linuxsql-server-linux-change-repomd"></a>1.&nbsp; [インストールして、Linux 上の SQL Server をアップグレードするためのリポジトリを構成します。](sql-server-linux-change-repo.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 72.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5ccaa0fcb8895f25c162e4e0494ad4872773de3 29a959be6ee7d58fe0c53e8f91bdd282fb2e6d29  (PR=5676  ,  Filename=sql-server-linux-change-repo.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- ファイルの内容を出力します。

```
   sudo cat /etc/yum.repos.d/mssql-server.repo
```

- **名前**プロパティが構成されているリポジトリ。 この記事の [リポジトリ] セクションでテーブルを識別できます。

**古いリポジトリ (RHEL) を削除します。**

必要に応じて、次のコマンドを使用して古いリポジトリを削除します。

```
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

このコマンドは、前のセクションで指定されたファイルがという名前の前提としています。 **mssql server.repo**です。

**新しいリポジトリ (RHEL) を構成します。**

SQL Server のインストールとアップグレードに使用する新しいリポジトリを構成します。 任意のリポジトリを構成するのにには、次のコマンドのいずれかを使用します。

| リポジトリ | コマンド |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

**<a id="sles"></a> SLES リポジトリを構成します。**

SLES でリポジトリを構成するのにには、次の手順を使用します。

**以前に構成したリポジトリ (SLES) の確認します。**

まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

- 使用して**zypper 情報**すべて以前に構成されたリポジトリに関する情報を取得します。

```
   sudo zypper info mssql-server
```

- **リポジトリ**プロパティが構成されているリポジトリ。 この記事の [リポジトリ] セクションでテーブルを識別できます。

**古いリポジトリ (SLES) を削除します。**

必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>2.&nbsp; [Mssql conf ツールを使用して Linux 上の SQL Server を構成します。](sql-server-linux-configure-mssql-conf.md)

*最終更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 151.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3664c4d64ea4840dcbc718461ed04403cc486f30 89f708af45ce262057e967e9047f1328e19248ba  (PR=5676  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->




**<a id="masterdatabasedir"></a> Master データベース ファイル ディレクトリの既定の場所を変更します。**


**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定の変更を SQL Server エンジンが master データベース ファイルを検索する場所です。 既定では、この場所は、/var/opt/mssql/data です。

これらの設定を変更するには、次の手順を使用します。

- 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/masterdatabasedir**ディレクトリ。

```
   sudo mkdir /tmp/masterdatabasedir
```

- 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

```
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
```

- Mssql conf を使用して、マスター データ ファイルとログ ファイルの既定の master データベースのディレクトリを変更する、**設定**コマンド。

```
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
```

- SQL Server サービスを停止します。

```
   sudo systemctl stop mssql-server
```

- Master.mdf と masterlog.ldf を移動するには。

```
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
```

- SQL Server サービスを開始します。

```
   sudo systemctl start mssql-server
```

> [!NOTE]
> SQL Server は、指定したディレクトリ内 master.mdf ファイルおよび mastlog.ldf ファイルを見つけることができません、指定したディレクトリ内のシステム データベースのテンプレートのコピーが自動的に作成されます、および SQL Server は正常に場合を起動します。 ただし、ユーザー データベース、サーバーのログイン、サーバー証明書、暗号化キー、SQL エージェント ジョブ、または古い SA ログインのパスワードなどのメタデータは、新しいマスター データベースでは更新されません。 SQL Server を停止し、新しい指定した場所に古い master.mdf および mastlog.ldf を移動し、引き続き既存のメタデータを使用する SQL Server を開始する必要があります。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>3.&nbsp; [Linux 上の SQL Server 2017 のリリース ノート](sql-server-linux-release-notes.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 367d112a9427bbdd18e0e52cc82264dd169c91ae 63a67be08fa39ece778cf9ca0b9746dd28694574  (PR=5676  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- [SQL Server エージェントを有効にする]

**<a id="CU6"></a> CU6 (年 2018年 4 月)**


これは、SQL Server 2017 の累積的な更新プログラム 6 (CU6) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3025.34 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)です。

**パッケージの詳細**


手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3025.34-3 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) |
| SLES RPM パッケージ | 14.0.3025.34-3 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) |
| Ubuntu 16.04 Debian パッケージ | 14.0.3025.34-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域

- [新規 + 更新 (11 + 6): &nbsp; &nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (18 + 0): &nbsp; &nbsp;**SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (218 + 14):**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (14 + 0): &nbsp; &nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (3 + 2): &nbsp; &nbsp; **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (3 + 3): &nbsp; &nbsp; **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (7 + 10): &nbsp; &nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (1 + 3): &nbsp; &nbsp; **SQL Operations Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **Tools for SQL** に関するドキュメント](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域

- [新規 + 更新 (0 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../samples/new-updated-samples.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)

