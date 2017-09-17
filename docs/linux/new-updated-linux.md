---
title: "更新済み - SQL Server on Linux docs |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、Microsoft SQL Server on Linux の更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 9e6b139e45ccb5184255eabedfb0f809ff64fd2b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017-07-18** &nbsp;対&nbsp; **2017 年-09-11**
- *サブジェクト領域:* &nbsp; **Microsoft SQL Server on Linux**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

次のリンクは、最近追加された新しいアーティクルにジャンプします。


1. [データベース メールと Linux 上の SQL エージェントによる電子メールのアラート](sql-server-linux-db-mail-sql-agent.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この圧縮リストは、抜粋セクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [SQL Server on Linux の HA 可用性グループを操作します。](#TitleNum_1)
2. [Docker でコンテナー イメージの SQL Server 2017 を構成します。](#TitleNum_2)
3. [Mssql conf ツールを使用して Linux 上の SQL Server を構成します。](#TitleNum_3)
4. [Linux での SQL Server カスタマー フィードバック](#TitleNum_4)
5. [Windows からのバックアップと復元を使用して Linux に SQL Server データベースを移行します。](#TitleNum_5)
6. [Linux 上の SQL Server 2017 のリリース ノート](#TitleNum_6)
7. [Linux 上の SQL Server のインストールのガイダンス](#TitleNum_7)
8. [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](#TitleNum_8)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-operate-ha-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-failover-hamd"></a>1.&nbsp;[動作 HA 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-failover-ha.md)

*最終更新日: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 167.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1bef3ece125721b041aa2b9d836329736377df8d 669d2b9a614d680b98280d5b522ba82cf466536c  (PR=2948  ,  Filename=sql-server-linux-availability-group-failover-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



**可用性グループをアップグレードします。**


可用性グループをアップグレードする前に [アップグレードする可用性グループ レプリカ インスタンス--.. のベスト プラクティスを確認します。/database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)。

次のセクションでは、可用性グループを含む Linux 上の SQL Server インスタンスでローリング アップグレードを実行する方法を説明します。

**Linux 上のアップグレード手順**


可用性グループのレプリカが Linux での SQL Server のインスタンス上にある場合は、可用性グループのクラスターの種類は`EXTERNAL`または`NONE`です。 さらには、Windows Server フェールオーバー クラスター (WSFC) クラスター マネージャーで管理されている可用性グループ`EXTERNAL`です。 Corosync とペースでは、外部のクラスター マネージャーの例を示します。 クラスター マネージャーがありませんがある可用性グループがクラスターの種類`NONE`アップグレード手順は、こちらは、クラスターの種類の可用性グループの特定`EXTERNAL`または`NONE`です。

1. 開始する前に、各データベースをバックアップします。
2. セカンダリ レプリカをホストする SQL Server のインスタンスをアップグレードします。

    a. 非同期のセカンダリ レプリカを最初にアップグレードします。

    b. 同期セカンダリ レプリカをアップグレードします。

   >[!NOTE]
   >のみの場合、可用性グループ非同期レプリカ - をデータの損失を回避するのには 1 つのレプリカを同期に変更しが同期されるまでを待ちます。 このレプリカをアップグレードします。

   b.1 です。 アップグレードの対象となるセカンダリ レプリカをホストしているノード上のリソースを停止します。

   アップグレード コマンドを実行する前に、クラスターを監視し、は、不必要に失敗するように、リソースを停止します。 次の例では、停止するためのリソースに原因となるノードの場所の制約を追加します。 更新`ag_cluster-master`リソース名を持つと`nodeName1`アップグレードの対象となるレプリカをホストしているノードにします。

```
   pcs constraint location ag_cluster-master avoids nodeName1
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>2.&nbsp;[Docker でコンテナーのイメージを構成する SQL Server 2017 年 1](sql-server-linux-configure-docker.md)

*最終更新日: 2017 年-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 257.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0239ed55a23721eedcc0407a0886d08da47c975b 108fe230151cff7dc91fcdc22218f232394746ec  (PR=3050  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=60272ce672c0a32738b0084ea86f8907ec7fc0a5) -->



1. Docker を識別**タグ**を使用するリリースします。 使用できるタグを表示するを参照してください。 [mssql サーバー linux Docker ハブ ページ](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/)です。

1. タグを持つ SQL Server のコンテナー イメージをプルします。 たとえば、RC1 のイメージをプルする次のように置換します。`<image_tag>`で次のコマンドで`rc1`です。

```
   docker pull microsoft/mssql-server-linux:<image_tag>
```

1. をそのイメージを新しいコンテナーを実行するには、でタグの名前を指定、`docker run`コマンド。 次のコマンドで置き換える`<image_tag>`バージョンを実行するとします。

```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -p 1401:1433 -d microsoft/mssql-server-linux:<image_tag>
```

次の手順は、既存のコンテナーをダウン グレードにも使用できます。 たとえばにロールバックします。 またはトラブルシューティングやテストの実行中のコンテナーをダウン グレードする可能性があります。 実行中のコンテナーをダウン グレードには、データ フォルダーの永続化手法を使用する必要があります。 記載されている同じ手順に従って、[アップグレード セクション--#upgrade) が、新しいコンテナーを実行すると、古いバージョンのタグ名を指定します。

> [!IMPORTANT]



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>3.&nbsp;[Mssql conf ツールを使用して Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)

*最終更新日: 2017 年-09-05* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= lbosq.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6117f03e9617b70077488d86f94b32537c4cb9e8 4247a749c056037dd71a27121525be04be6a4f21  (PR=3042  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=46b16dcf147dbd863eec0330e87511b4ced6c4ce) -->



**<a id="localaudit"></a>監査のローカル ディレクトリのセット**


**Telemetry.userrequestedlocalauditdirectory**設定は、ローカルの監査を有効にし、ローカルの監査ログで、ディレクトリを設定できますが作成されます。

1. 新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例は、新しい作成**tmp/監査**ディレクトリ。

```
   sudo mkdir /tmp/audit
```

1. 所有者とするディレクトリのグループを変更、 **mssql**ユーザー。

```
   sudo chown mssql /tmp/audit
   sudo chgrp mssql /tmp/audit
```

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**telemetry.userrequestedlocalauditdirectory**:

```
   sudo /opt/mssql/bin/mssql-conf set telemetry.userrequestedlocalauditdirectory /tmp/audit
```

1. SQL Server サービスを再起動します。

```
   sudo systemctl restart mssql-server
```

詳細については、[Linux--sql-server-linux-customer-feedback.md での SQL Server カスタマー フィードバック) を参照してください。

**<a id="lcid"></a>SQL Server のロケールを変更します。**


**Language.lcid**設定の変更をすべてサポートされている言語識別子 (LCID) に SQL Server のロケールです。

1. 次の例は、フランス語にロケールを変更 (1036)。

```
   sudo /opt/mssql/bin/mssql-conf set language.lcid 1036
```

1. 変更を適用する SQL Server サービスを再起動します。

```
   sudo systemctl restart mssql-server
```

**<a id="memorylimit"></a>メモリ制限を設定します。**


**Memory.memorylimitmb** SQL Server にコントロールの量 (MB) で使用できる物理メモリを設定します。 既定では物理メモリの 80% です。

1. ルートととして mssql conf スクリプトを実行、**設定**コマンドを**memory.memorylimitmb**です。 次の例では、使用可能なメモリを 3.25 GB (3328 MB) を SQL Server に変更します。

```
   sudo /opt/mssql/bin/mssql-conf set memory.memorylimitmb 3328
```

1. 変更を適用する SQL Server サービスを再起動します。



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-customer-feedback-for-sql-server-on-linuxsql-server-linux-customer-feedbackmd"></a>4.&nbsp;[For Linux に SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)

*最終更新日: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3) | [次](#TitleNum_5))

<!-- Source markdown line 104.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9d8122e864804004d91f6b7c5c3d24c4a4114d34 7316ef831c390a854c324f23a02c3fb6005e2fea  (PR=2948  ,  Filename=sql-server-linux-customer-feedback.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->




**Docker で**

Docker でローカルの監査を有効にする必要があります Docker [、data--sql-server-linux-configure-docker.md を保持) します。

1. 新しいローカルの監査ログのターゲット ディレクトリをコンテナーになります。 コンピューターにホスト ディレクトリ内には、新しいローカルの監査ログのターゲット ディレクトリを作成します。 次の例は、新しい作成**監査/**ディレクトリ。

```
   sudo mkdir <host directory>/audit
```


1. 追加、`mssql.conf`の行を含むファイル`[telemetry]`と`userrequestedlocalauditdirectory = <host directory>/audit`ホスト ディレクトリ。

```
   echo '[telemetry]' >> <host directory>/mssql.conf
```

```
   echo 'userrequestedlocalauditdirectory = <host directory>/audit' >> <host directory>/mssql.conf
```
2. コンテナー イメージを実行します。
```
   docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

```
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" --cap-add SYS_PTRACE -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux
```

**次の手順**





&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restoresql-server-linux-migrate-restore-databasemd"></a>5.&nbsp;[Windows からのバックアップと復元を使用して Linux に SQL Server データベースを移行します。](sql-server-linux-migrate-restore-database.md)

*最終更新日: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_4) | [次](#TitleNum_6))

<!-- Source markdown line 30.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e78f5516a46eab834f644979d3e1c0ca415fabcd 6b03a01385078290b9f451ac013b628f53e0e8b4  (PR=2948  ,  Filename=sql-server-linux-migrate-restore-database.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



* 次の Windows コンピューター:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions)をインストールします。
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)をインストールします。
  * ターゲット データベースを移行します。

* インストールされている次の Linux マシン:
  * SQL Server 2017 RC2。 インストールのクイック スタートを参照してください [RHEL--quickstart-install-connect-red-hat.md)、[SLES--クイック スタートのインストール-接続-suse.md) または [Ubuntu--クイック スタートのインストール-接続-ubuntu.md)。
  * SQL Server 2017 RC2 [コマンド ライン tools--sql-server-linux-setup-tools.md)。

**Windows でバックアップを作成します。**


Windows 上のデータベースのバックアップ ファイルを作成するいくつかの方法はあります。 次の手順では、SQL Server Management Studio (SSMS) を使用します。

1. 開始**SQL Server Management Studio** Windows コンピューターにします。

1. 接続ダイアログ ボックスで、次のように入力します。 **localhost**です。

1. オブジェクト エクスプ ローラーで、**データベース**です。



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>6.&nbsp;[Linux 上の SQL Server 2017 のリリース ノート](sql-server-linux-release-notes.md)

*最終更新日: 2017-08-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_5) | [次](#TitleNum_7))

<!-- Source markdown line 31.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4c8b9876f4792782314ba2f9b246405fb8036f84 acb97cf0a2e0bdd039575eaab9c41003316cbb02  (PR=2939  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=91098c850b0f6affb8e4831325d0f18fd163d71a) -->



**<a id="RC2"></a>RC2 (2017 年 8 月)**


このリリースの SQL Server エンジンのバージョンは、14.0.900.75 です。

**サポートされているプラットフォーム**


| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール guide--quickstart-install-connect-red-hat.md) |
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [クイック スタートのインストール-接続-suse.md--インストール ガイド) |
| Ubuntu 16.04LTS | EXT4 | [クイック スタートのインストール-接続-ubuntu.md--インストール ガイド) |
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [クイック スタートのインストール-接続-docker.md--インストール ガイド) |

> [!NOTE]
> Linux 上の SQL Server を実行するには、少なくとも 3.25 GB のメモリを必要とします。
> SQL Server エンジンがされてこの時点で 1.5 TB のメモリをテストします。

**パッケージの詳細**


パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありませんに注意してください。

- [SQL Server パッケージ--sql server-linux setup.md インストール)
- [フルテキスト検索 package--sql-server-linux-setup-full-text-search.md をインストール)
- [Package--sql-server-linux-setup-sql-agent.md の SQL Server エージェントのインストール)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.900.75-1 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) |



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7.&nbsp;[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)

*最終更新日: 2017-08-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_6) | [次](#TitleNum_8))

<!-- Source markdown line 70.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00394e1733568a55243788d828968ff9b58a3c99 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880  (PR=2971  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=303d3b74da3fe370d19b7602c0e11e67b63191e7) -->



**<a id="rollback"></a>SQL Server をロールバック**


ロールバックまたは SQL Server の以前のリリースにダウン グレードは、次の手順に従います。

1. ダウン グレードする SQL Server パッケージのバージョン番号を識別します。 パッケージの番号の一覧は、[リリース notes--sql-server-linux-release-notes.md) を参照してください。

1. SQL Server の以前のバージョンにダウン グレードします。 次のコマンドで置き換える`<version_number>`いずれかの手順で特定した SQL Server のバージョン番号を持つ。

   | プラットフォーム | パッケージの更新コマンド |
   |-----|-----|
   | RHEL | `sudo yum downgrade mssql-server-<version_number>.x86_64` |
   | SLES | `sudo zypper install --oldpackage mssql-server=<version_number>` |
   | Ubuntu | `sudo apt-get install mssql-server=<version_number>`<br/>`sudo systemctl start mssql-server` |

> [!NOTE]
> SQL Server 2017 など、同じメジャー バージョンのリリースにダウン グレードすることのみサポートされます。

> [!IMPORTANT]
> ダウン グレードは、この時点で RC2 と RC1 の間でのみサポートされます。




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-install-sql-server-integration-services-ssis-on-linuxsql-server-linux-setup-ssismd"></a>8.&nbsp;[Linux 上の SQL Server Integration Services (SSIS) のインストール](sql-server-linux-setup-ssis.md)

*最終更新日: 2017-08-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_7))

<!-- Source markdown line 66.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a3fecd2553d1b25406445b8a26b22c9015dd98fe f836d560513fef1217e7dbce0ab85f78eec6f937  (PR=2948  ,  Filename=sql-server-linux-setup-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=7b8c23474aee48e6d34ba268bc8942bc1c0263d3) -->



既に存在する場合`mssql-server-is`インストールされている、次のように次のコマンドで最新バージョンに更新できます。

```
sudo apt-get install mssql-server-is
```


削除する`mssql-server-is`、次のコマンドを実行することができます。
```
sudo apt-get remove msssql-server-is
```



**<a name="RHEL"></a>RHEL に SSIS をインストールします。**

インストールする、 `mssql-server-is` RHEL にパッケージ化、これらの手順に従います。


1.  スーパー ユーザーのモードを入力します。

```
    sudo su
```


2.  Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードします。

```
    curl https://packages.microsoft.com/config/rhel/7/mssql-server.repo > /etc/yum.repos.d/mssql-server.repo
```


3.  スーパー ユーザーのモードを終了します。

```
    exit
```


4.  SQL Server Integration Services をインストールする次のコマンドを実行します。

```
    sudo yum install -y mssql-server-is
```


5.  インストールを実行してください。`ssis-conf`です。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションには、パブリック GitHub.com リポジトリ内の他のサブジェクト領域で、最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示されます: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/)です。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (3 + 12): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (5 + 0): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (5 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (19 + 82): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (1 + 8): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (12 + 1):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (0 + 1): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (7 + 1): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新しい + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (4 + 1): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)
- [新しい + 更新 (0 + 1): **Tools for SQL** docs](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新しい + 更新 (0 0 以降): **SQL のように、マスター データ サービス (MDS)** docs](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



