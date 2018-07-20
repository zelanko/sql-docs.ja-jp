---
title: 更新済み - SQL Server on Linux のドキュメント |Microsoft Docs
description: 最近変更されたドキュメントは、Microsoft SQL Server on Linux の更新されたコンテンツのスニペットを表示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: f7f1e437e0b9d4c2940293280ee2c5529da85e6c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082484"
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 時折不完全な書式設定の抜粋が表示されたり、ソース記事からマークダウンとして表示されたりすることがあります。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *対象領域:* &nbsp; **Microsoft SQL Server on Linux**します。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [Linux 上の SQL Server の active Directory 認証](sql-server-linux-active-directory-auth-overview.md)
2. [構成する SQL Server Always On 可用性グループで、Windows および Linux (クロス プラットフォーム)](sql-server-linux-availability-group-cross-platform.md)
3. [Linux 上の可用性グループに対して常に](sql-server-linux-availability-group-operate-ha.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切られて表示されます。 また、元の記事の中で、重要なマークダウン構文に覆われた抜粋が区切られて表示されることもあります。 したがってこれらの抜粋は、一般的なガイダンスとしてのみ使用されます。 抜粋からは、その記事をクリックして訪れるに足るものであるか、ということだけを知ることができます。

これらおよびその他の理由によって、これらの抜粋からコードをコピーせず、テキストの抜粋を確かな事実として受け取らないようにしてください。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [インストールして、Linux 上の SQL Server のアップグレードのためのリポジトリを構成します。](#TitleNum_1)
2. [Linux 上の SQL Server を mssql-conf ツールを構成します。](#TitleNum_2)
3. [Linux 上の SQL Server 2017 のリリース ノート](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-repositories-for-installing-and-upgrading-sql-server-on-linuxsql-server-linux-change-repomd"></a>1.&nbsp; [インストールして、Linux 上の SQL Server のアップグレードのためのリポジトリを構成します。](sql-server-linux-change-repo.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 72.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5ccaa0fcb8895f25c162e4e0494ad4872773de3 29a959be6ee7d58fe0c53e8f91bdd282fb2e6d29  (PR=5676  ,  Filename=sql-server-linux-change-repo.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- ファイルの内容を出力します。

```
   sudo cat /etc/yum.repos.d/mssql-server.repo
```

- **名前**プロパティが構成されているリポジトリです。 この記事の [リポジトリ] セクションでテーブルを識別できます。

**古いリポジトリ (RHEL) の削除します。**

必要に応じて、次のコマンドを使用して古いリポジトリを削除します。

```
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

このコマンドは、前のセクションで識別されるファイルの名前が前提としています。 **mssql server.repo**します。

**新しいリポジトリ (RHEL) を構成します。**

SQL Server のインストールとアップグレードのために使用する新しいリポジトリを構成します。 次のコマンドのいずれかを使用して、好みのリポジトリを構成します。

| リポジトリ | コマンド |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

**<a id="sles"></a> SLES リポジトリを構成します。**

SLES でリポジトリを構成するのにには、次の手順を使用します。

**以前に構成されたリポジトリ (SLES) の確認します。**

まず、SQL Server リポジトリが既に登録されているかどうかを確認します。

- 使用**zypper 情報**以前に構成された任意のリポジトリに関する情報を取得します。

```
   sudo zypper info mssql-server
```

- **リポジトリ**プロパティが構成されているリポジトリです。 この記事の [リポジトリ] セクションでテーブルを識別できます。

**古いリポジトリ (SLES) の削除します。**

必要に応じて、古いリポジトリを削除します。 以前に構成されたリポジトリの種類に基づいて、次のコマンドのいずれかを使用します。

| リポジトリ | 削除するコマンド |
|---|---|
| **プレビュー** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>2.&nbsp; [Linux 上の SQL Server を mssql-conf ツールを構成します。](sql-server-linux-configure-mssql-conf.md)

*更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 151.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3664c4d64ea4840dcbc718461ed04403cc486f30 89f708af45ce262057e967e9047f1328e19248ba  (PR=5676  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->




**<a id="masterdatabasedir"></a> Master データベース ファイル ディレクトリの既定の場所を変更します。**


**Filelocation.masterdatafile**と**filelocation.masterlogfile**設定では、SQL Server エンジンが master データベース ファイルを検索する場所の場所を変更します。 既定では、この場所は、/var/opt/mssql/data は。

これらの設定を変更するには、次の手順を使用します。

- 新しいエラー ログ ファイルのターゲット ディレクトリを作成します。 次の例では、作成、新しい **/tmp masterdatabasedir**ディレクトリ。

```
   sudo mkdir /tmp/masterdatabasedir
```

- 所有者とグループをディレクトリの変更、 **mssql**ユーザー。

```
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
```

- Mssql conf を使用して、マスター データとログ ファイルでの既定の master データベースのディレクトリを変更する、**設定**コマンド。

```
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
```

- SQL Server サービスを停止します。

```
   sudo systemctl stop mssql-server
```

- Master.mdf と masterlog.ldf を移動します。

```
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
```

- SQL Server サービスを開始するには。

```
   sudo systemctl start mssql-server
```

> [!NOTE]
> SQL Server でのファイル master.mdf および mastlog.ldf ファイルを指定されたディレクトリを見つけられない場合は、システム データベースのテンプレート化されたコピーが指定されたディレクトリに自動的に作成され、SQL Server は正常に起動します。 ただし、ユーザー データベース、サーバーのログイン、サーバー証明書、暗号化キー、SQL エージェント ジョブ、または古い SA ログインのパスワードなどのメタデータは、新しいマスター データベースでは更新されません。 SQL Server を停止して、古い master.mdf および mastlog.ldf を新しいの指定した場所に移動し、引き続き既存のメタデータを使用する SQL Server を開始する必要があります。



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

**<a id="CU6"></a> CU6 (2018 年 4 月)**


これは、SQL Server 2017 の累積的な更新プログラム 6 (CU6) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3025.34 です。 このリリースの機能強化と修正については、次を参照してください。 [ https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)します。

**パッケージの詳細**


手動またはオフラインのパッケージのインストールでの次の表の情報の RPM および Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat の RPM パッケージ | 14.0.3025.34-3 | [エンジンの RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) |
| SLES RPM パッケージ | 14.0.3025.34-3 | [mssql server エンジンの RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) |
| Debian パッケージを Ubuntu 16.04 | 14.0.3025.34-3 | [エンジンの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |







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

