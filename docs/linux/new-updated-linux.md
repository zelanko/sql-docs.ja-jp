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
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 030f30580b0ddb02da2a67990d0c58acf15236c9
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 28 日**&nbsp;から &nbsp; **2017 年 12 月 2 日**
- *サブジェクト領域:* &nbsp; **Microsoft SQL Server on Linux**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server 2017 をクラウドで実行します。](quickstart-install-connect-clouds.md)
2. [リポジトリをプレビュー リポジトリから GA リポジトリに変更します。](sql-server-linux-change-repo.md)
3. [パフォーマンスのベスト プラクティスと Linux 上の SQL Server 2017 の構成ガイドライン](sql-server-linux-performance-best-practices.md)
4. [フェールオーバー クラスター インスタンスの SQL Server on Linux](sql-server-linux-shared-disk-cluster-concepts.md)
5. [フェールオーバー クラスター インスタンス - iSCSI: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
6. [フェールオーバー クラスター インスタンス: NFS - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-nfs.md)
7. [フェールオーバー クラスター インスタンス: SMB - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-smb.md)
8. [フェールオーバー クラスター インスタンス: Linux 上の SQL Server の動作します。](sql-server-linux-shared-disk-cluster-operate.md)
9. [制限事項と Linux の SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
10. [Linux Docker コンテナーでの SQL Server データベースを復元します。](tutorial-restore-backup-in-sql-server-container.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [Docker を使用した SQL Server 2017 コンテナー イメージを実行します。](#TitleNum_1)
2. [Linux 上の SQL Server の Always On 可用性グループを構成します。](#TitleNum_2)
3. [可用性グループの構成の高可用性とデータの保護](#TitleNum_3)
4. [Docker でコンテナー イメージの SQL Server 2017 を構成します。](#TitleNum_4)
5. [Linux 上の SQL Server への接続を暗号化](#TitleNum_5)
6. [作成し、Linux 上の SQL Server エージェント ジョブの実行](#TitleNum_6)
7. [Linux 上の SQL Server のインストールのガイダンス](#TitleNum_7)
8. [SQL Server Linux (RHEL) でのフェールオーバー クラスター インスタンスを構成します。](#TitleNum_8)
9. [SQL Server on Linux をトラブルシューティングします。](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-run-the-sql-server-2017-container-image-with-dockerquickstart-install-connect-dockermd"></a>1.&nbsp;[Docker を使用した SQL Server 2017 コンテナー イメージを実行](quickstart-install-connect-docker.md)

*更新日: 2017 年 11 月 30 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 261.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2aaf953c2f1fb675b1304186108fbef1eebf6f8f f7cd42bb320a8892a5ec63ce999186438097636a  (PR=4150  ,  Filename=quickstart-install-connect-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**コンテナーを削除します。**


このチュートリアルで使用される SQL Server のコンテナーを削除する場合は、次のコマンドを実行します。

```
sudo docker stop sql1
sudo docker rm sql1
```

```
docker stop sql1
docker rm sql1
```

> [!WARNING]
> コンテナーの完全に削除を停止して、コンテナー内の任意の SQL Server データを削除します。 データを保持する必要がある場合 [、container--tutorial-restore-backup-in-sql-server-container.md 外のバックアップ ファイルのコピーを作成および) か使用して、[コンテナーのデータ永続化 technique--sql-server-linux-configure-docker.md#persist)。




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-always-on-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-configure-hamd"></a>2.&nbsp;[構成 Always On 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 129.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c7e6bc862e5b062a855918efbeee5fe748b7236 6900c9a30ce04ce54e7aaa270ef7d276c18f9afd  (PR=4150  ,  Filename=sql-server-linux-availability-group-configure-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



- 2 つの同期レプリカと構成のレプリカの可用性グループを作成します。

   >[!IMPORTANT]
   >このアーキテクチャにより、3 番目のレプリカをホストする SQL Server の任意のエディションです。 たとえば、SQL Server Enterprise Edition で 3 番目のレプリカをホストすることができます。 Enterprise Edition でのみ有効なエンドポイント タイプは`WITNESS`します。

```sql
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
       N'**<node1>**' WITH (
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node2>**' WITH (
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node3>**' WITH (
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**',
          AVAILABILITY_MODE = CONFIGURATION_ONLY
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-high-availability-and-data-protection-for-availability-group-configurationssql-server-linux-availability-group-hamd"></a>3.&nbsp;[可用性グループの構成の高可用性とデータの保護](sql-server-linux-availability-group-ha.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 106.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e6bee794ce19f1ed62298b4a0cce7207550f1595 b64726cd6e91721850721786d26c170d59fc320a  (PR=4150  ,  Filename=sql-server-linux-availability-group-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



既定値`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`は 0 です。 次の表では、可用性の動作について説明します。

| |高可用性 (& a) </br> データの保護 | データの保護
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|@shouldalert
|プライマリ停止 | 自動フェールオーバー。 新しいプライマリが R が付けられます。 | 自動フェールオーバー。 新しいプライマリでは、ユーザー トランザクションで使用できません。
|セカンダリ レプリカの停止 | プライマリ ファイル グループは読み取り/書き込みを実行して公開されているデータの損失を (プライマリが失敗し、回復することはできません) です。 プライマリにも失敗した場合はない自動フェールオーバー。 | プライマリでは、ユーザー トランザクションで使用できません。 プライマリにも失敗した場合にフェールオーバーするレプリカがありません。
|構成のみのレプリカの停止 | プライマリが R 付けられます。 プライマリにも失敗した場合はない自動フェールオーバー。 | プライマリが R 付けられます。 プライマリにも失敗した場合はない自動フェールオーバー。
|同期セカンダリ + の構成のみのレプリカの停止| プライマリでは、ユーザー トランザクションで使用できません。 自動フェールオーバーはありません。 | プライマリでは、ユーザー トランザクションで使用できません。 レプリカにフェールオーバーする場合はプライマリでも失敗しません。
<sup>*</sup>既定値

>[!NOTE]
>構成のみのレプリカをホストする SQL Server のインスタンスは、他のデータベースをホストすることもできます。 1 つ以上の可用性グループの構成のみデータベースとして参加できます。

**必要条件**


* 構成の唯一のレプリカを可用性グループ内のすべてのレプリカは、SQL Server 2017 CU 1 またはそれ以降である必要があります。
* SQL Server の任意のエディションでは、SQL Server Express を含む、構成のみレプリカをホストできます。
* 可用性グループには、プライマリ レプリカに加えて - には、少なくとも 1 つのセカンダリ レプリカが必要があります。
* 構成の唯一のレプリカは、SQL Server のインスタンスごとのレプリカの最大数になるまではカウントされません。 SQL Server の standard エディションで許容される最大 3 つのレプリカが、SQL Server Enterprise Edition には最大 9 ができます。



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>4.&nbsp;[Docker でコンテナーのイメージを構成する SQL Server 2017 年 1](sql-server-linux-configure-docker.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3) | [次](#TitleNum_5))

<!-- Source markdown line 34.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c759fb88ae8d654414202f28c5fc58dfd02581bf fd270118f2f4608fceaf563fc143951b41097bdb  (PR=4150  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



この構成のトピックでは、以下のセクションに追加の使用シナリオを示します。

**<a id="production"></a>実稼働環境にコンテナー イメージを実行します。**


前のセクションで、クイック スタートでは、Docker Hub から SQL Server の無償の Developer エディションを実行します。 情報の大部分は、Enterprise、Standard、または Web edition などのコンテナー イメージの運用を実行する場合にも適用されます。 ただし、ここで説明されている、いくつかの違いがあります。

- のみ、有効なライセンスがある場合、SQL Server を実稼働環境で使用できます。 無料の SQL Server Express の運用環境ライセンスを取得する[ここ](https://go.microsoft.com/fwlink/?linkid=857693)です。 を通じて使用可能な SQL Server Standard および Enterprise Edition のライセンス[Microsoft ボリューム ライセンス](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx)です。

- 実稼働 SQL Server のコンテナー イメージをプルする必要があります[Docker ストア](https://store.docker.com)です。 1 つをいない場合は、Docker ストアでアカウントを作成します。

- 実稼働エディションもを実行する、Docker のストアに開発者のコンテナーのイメージを構成できます。 実稼働のエディションを実行するのにには、次の手順を使用します。

   1. 最初に、ログイン、docker id に、コマンドラインからします。

```
      docker login
```

   1. 次に、無料の開発者用 Docker ストアにコンテナーのイメージを取得する必要があります。 移動して[https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux)をクリックして**チェック アウトを続行**、し、指示に従います。

   1. 要件を確認し、[クイック スタート - クイック スタートのインストール-接続-docker.md) プロシージャを実行します。 2 つの違いがあります。 イメージをプルする必要があります**ストアまたは microsoft/mssql-サーバー-linux:\<タグ名\>** Docker ストアからです。 実稼働のエディションを指定する必要がありますと、 **MSSQL_PID**環境変数。 次の例では、Enterprise Edition 用の最新の SQL Server 2017 コンテナー イメージを実行する方法を示します。



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-encrypting-connections-to-sql-server-on-linuxsql-server-linux-encrypted-connectionsmd"></a>5.&nbsp;[Linux に SQL Server への接続を暗号化](sql-server-linux-encrypted-connections.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_4) | [次](#TitleNum_6))

<!-- Source markdown line 45.  ms.author= meetb;rickbyh.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e3187866df060903e30000d60d673edad46d210 bcb1f2771e6c29b535a30b9f23ac296954509187  (PR=4150  ,  Filename=sql-server-linux-encrypted-connections.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



        sudo chown mssql:mssql mssql.pem mssql.key
        sudo chmod 600 mssql.pem mssql.key
        sudo mv mssql.pem /etc/ssl/certs/
        sudo mv mssql.key /etc/ssl/private/

- **SQL Server を構成します。**

        systemctl stop mssql-server
        cat /var/opt/mssql/mssql.conf
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0

- **(Windows、Linux または macOS)、クライアント コンピューターの証明書を登録します。**

    -   CA の署名証明書を使用している場合、ユーザー証明書の代わりに証明機関 (CA) 証明書をクライアント コンピューターにコピーする必要があります。
    -   .Pem ファイルを配布するそれぞれの次のフォルダーにコピーした自己署名証明書を使用している場合、およびコマンドを実行できるようにします

        - **Windows**: ルート証明機関証明書]-> [信頼された証明書を現在のユーザーとして .pem ファイル]-> [インポート
        - **macOS**:

-   **接続文字列の例**

    - **..!テキストの NotShown--ssmanstudiofull md--./includes/ssmanstudiofull-md.md)]** ! [SSMS 接続 dialog--media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png「SSMS 接続ダイアログ」)



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-create-and-run-sql-server-agent-jobs-on-linuxsql-server-linux-run-sql-server-agent-jobmd"></a>6.&nbsp;[作成し、Linux 上の SQL Server エージェント ジョブを実行](sql-server-linux-run-sql-server-agent-job.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_5) | [次](#TitleNum_7))

<!-- Source markdown line 35.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1598129bb5f98434435d8ad02336a9adf76c7870 6fe3fe7df3a60dbac31f1df59aac9860d293421a  (PR=4150  ,  Filename=sql-server-linux-run-sql-server-agent-job.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



このチュートリアルを完了するには、次の前提条件が必要です。

* 次の前提条件での Linux マシン:
  * SQL Server 2017 ([RHEL--quickstart-install-connect-red-hat.md)、[SLES--クイック スタートのインストール-接続-suse.md) または [Ubuntu--クイック スタートのインストール-接続-ubuntu.md)) コマンド ライン ツールを使用します。

次の前提条件はオプションです。

* SSMS を持つ Windows マシン。
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) SSMS 手順については省略可能です。

**SQL Server エージェントのインストール**


Linux に SQL Server エージェントを使用するには、まず、 **mssql server エージェント**がインストールされている SQL Server 2017 マシン上のパッケージです。

1. インストール**mssql server エージェント**には、Linux OS の適切なコマンドを使用します。

   | プラットフォーム | インストール コマンド |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. 次のコマンドで SQL Server を再起動します。

```
   sudo systemctl restart mssql-server
```

**サンプル データベースを作成します。**


という名前のサンプル データベースを作成する、次の手順を使用して**SampleDB**です。 このデータベースは、毎日のバックアップ ジョブに使用されます。

1. Linux コンピューターでは、bash ターミナル セッションを開きます。



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7.&nbsp;[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)

*最終更新日: 2017 年-12-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_6) | [次](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880 eedddcfb64c6432215f56b74dc91700d9804fce8  (PR=4160  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=085dd05d56afecbb454206ed8402cfbaa597cfbe) -->



**<a id="repositories"></a>ソース リポジトリを構成します。**


インストールまたは SQL Server をアップグレードするときに、構成されている Microsoft リポジトリから SQL Server の最新バージョンを取得します。

**リポジトリのオプション**


各配布用のリポジトリの 2 つの主な種類があります。

- **累積的な更新プログラム (CU)**:、累積的な更新プログラム (CU) リポジトリには、そのリリース以降、基本の SQL Server リリースおよびバグの修正や改善用のパッケージが含まれます。 累積的更新プログラムは、SQL Server 2017 などのリリース バージョンに固有です。 正規わかりませんがリリースされます。

- **GDR**: の GDR リポジトリには、そのリリース以降、基本の SQL Server リリースのみ重要な修正プログラムとセキュリティ更新プログラム用のパッケージが含まれています。 これらの更新プログラムは、次の CU リリースにも追加されます。

各 CU および GDR のリリースには、完全な SQL Server パッケージとそのリポジトリの以前のすべての更新が含まれています。 CU リリースに GDR のリリースから更新は、SQL Server 用に構成されているリポジトリを変更することによってサポートされています。 こともできます [ダウン グレード--#rollback) に、メジャー バージョン内で任意のリリース (ex: 2017)。 更新 CU から GDR リリースにリリースはサポートされていません。

**構成されているリポジトリを確認します。**


どのようなリポジトリが構成されていることを確認する場合は、次のプラットフォームに依存する手法を使用します。

| プラットフォーム | 手順 |
|-----|-----|
| RHEL | 1.内のファイルを表示、 **/etc/yum.repos.d**ディレクトリ。`sudo ls /etc/yum.repos.d`<br/>2.など、SQL Server ディレクトリを構成するファイルを探します**mssql server.repo**です。<br/>3.ファイルの内容を出力します。`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4.**名前**プロパティが構成されているリポジトリ。|
| SLES | 1.コマンド `sudo zypper info mssql-server` を実行します。<br/>2.**リポジトリ**プロパティが構成されているリポジトリ。 |
| Ubuntu | 1.コマンド `sudo cat /etc/apt/sources.list` を実行します。<br/>2.Mssql サーバーのパッケージ URL を確認します。 |



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-configure-failover-cluster-instance---sql-server-on-linux-rhelsql-server-linux-shared-disk-cluster-configuremd"></a>8.&nbsp;[構成のフェールオーバー クラスター インスタンス: SQL Server Linux (RHEL) に](sql-server-linux-shared-disk-cluster-configure.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_7) | [次](#TitleNum_9))

<!-- Source markdown line 25.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 308fa1809c80a009f7f15b5ca6917f6b76588c3e 71f18baa320041ff10c94e8c7668e40dff45cac3  (PR=4150  ,  Filename=sql-server-linux-shared-disk-cluster-configure.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



> [!div class="checklist"]
> * 設定し、Linux を構成します。
> * SQL サーバー インストールし、構成
> * Hosts ファイルを構成します。
> * 共有記憶域を構成して、データベース ファイルの移動
> * インストールし、ペースを各クラスター ノードの構成
> * フェールオーバー クラスター インスタンスを構成します。

この記事では、SQL Server の 2 つのノードの共有ディスク フェールオーバー クラスター インスタンス (FCI) を作成する方法について説明します。 アーティクルには Red Hat Enterprise Linux (RHEL) の手順とスクリプトの例が含まれています。 Ubuntu 中の配布 RHEL のようなスクリプトの例は、通常されます Ubuntu でも機能します。

概念については、[SQL Server フェールオーバー クラスター インスタンス (FCI) Linux--sql-server-linux-shared-disk-cluster-concepts.md) を参照してください。 します。

**前提条件**


次のエンド ツー エンド シナリオを完了するには、2 台のコンピューターを 2 つのノードのクラスターと記憶域を別のサーバーを展開する必要があります。 以下の手順には、これらのサーバーを構成する方法を説明します。

**設定し、Linux を構成します。**


最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 クラスター内の各ノードでは、linux ディストリビューションを構成します。 両方のノードで同じディストリビューションとバージョンを使用します。 1 つまたは他の次のディストリビューションを使用します。

* HA のアドオンの有効なサブスクリプションで RHEL

**SQL サーバー インストールし、構成**


1. インストールし、両方のノードに SQL Server をセットアップします。  詳細な手順については、[インストール Linux に SQL Server--sql server-linux setup.md) を参照してください。
1. プライマリ サーバーと、他の構成のために、セカンダリとして 1 つのノードを指定します。 これらの用語を使用して、次のこのガイドです。
1. セカンダリ ノードで停止し、SQL Server を無効にします。
    次の例では、停止して、SQL Server を無効にします。
```
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
```

    > [!NOTE]
    > At set up time, a Server Master Key is generated for the SQL Server instance and placed at `var/opt/mssql/secrets/machine-key`. On Linux, SQL Server always runs as a local account called mssql. Because it's a local account, its identity isn't shared across nodes. Therefore, you need to copy the encryption key from primary node to each secondary node so each local mssql account can access it to decrypt the Server Master Key.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-troubleshoot-sql-server-on-linuxsql-server-linux-troubleshooting-guidemd"></a>9.&nbsp;[Linux に SQL Server のトラブルシューティング](sql-server-linux-troubleshooting-guide.md)

*更新日: 2017 年 11 月 30 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f8557a34b38e028ff6e5ac370b6d2d6bf315091 196e56187b57bdd79cc5cdc5e6fce3d41e82af0c  (PR=4150  ,  Filename=sql-server-linux-troubleshooting-guide.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**最小構成で、またはシングル ユーザー モードで SQL Server を起動します。**


**最小構成モードで SQL Server を起動します。**

設定値によりサーバーが起動できないとき (たとえば使用できるメモリが不足している場合) などに便利です。

```
   sudo -u mssql /opt/mssql/bin/sqlservr -f
```

**シングル ユーザー モードで SQL Server を起動します。**

特定の状況では、スタートアップ オプションと m を使用して、シングル ユーザー モードで SQL Server のインスタンスを起動する必要があります。 たとえば、サーバーの構成オプションを変更したり、破損した master データベースや他のシステム データベースを復旧したりすることがあります。 たとえば、サーバー構成オプションを変更または破損した master データベースまたはその他のシステム データベースを復元する可能性があります。

シングル ユーザー モードで SQL Server を起動します。
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m
```

SQLCMD でのシングル ユーザー モードで SQL Server を起動します。
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
```

> [!WARNING]
>  スタートアップに関する将来の問題を防ぐため、Linux 上の SQL Server は "mssql" ユーザーで起動してください。 たとえば、"sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]" などとします。

別のユーザーと、SQL Server を開始している誤って場合、systemd で SQL Server を開始する前に 'mssql' ユーザーに SQL Server データベース ファイルの所有権を変更する必要があります。 たとえば、'mssql' ユーザーに/var/opt/mssql 下にあるすべてのデータベース ファイルの所有権を変更するに次のコマンドを実行します。

```
   chown -R mssql:mssql /var/opt/mssql/
```







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 14): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (87 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (5 + 4): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (2 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (10 + 9): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (2 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (4 + 2): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (21 + 0): **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (5 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


