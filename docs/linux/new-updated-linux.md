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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 13c237af359c543f6a99a0fce101af81b5eb2bcf
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-05-23** &nbsp;対&nbsp; **2017-07-17**
- *サブジェクト領域:* &nbsp; **Microsoft SQL Server on Linux**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [Docker を使用した SQL Server 2017 コンテナー イメージを実行します。](quickstart-install-connect-docker.md)
2. [SQL Server をインストールし、Red hat でデータベースを作成](quickstart-install-connect-red-hat.md)
3. [SQL Server をインストールし、SUSE Linux Enterprise Server にデータベースを作成](quickstart-install-connect-suse.md)
4. [SQL Server をインストールし、Ubuntu でデータベースを作成](quickstart-install-connect-ubuntu.md)
5. [Red Hat Enterprise Linux 用のサンプル: SQL Server を無人インストール スクリプト](sample-unattended-install-redhat.md)
6. [SUSE Linux Enterprise Server のサンプル: SQL Server を無人インストール スクリプト](sample-unattended-install-suse.md)
7. [Ubuntu 用のサンプル: SQL Server の無人インストール スクリプト](sample-unattended-install-ubuntu.md)
8. [SQL Server on Linux での active Directory 認証](sql-server-linux-active-directory-authentication.md)
9. [可用性グループの構成の高可用性とデータの保護](sql-server-linux-availability-group-ha.md)
10. [Docker でコンテナー イメージの SQL Server 2017 を構成します。](sql-server-linux-configure-docker.md)
11. [Linux での SQL Server カスタマー フィードバック](sql-server-linux-customer-feedback.md)
12. [Linux 上の SQL Server への接続を暗号化](sql-server-linux-encrypted-connections.md)
13. [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この圧縮リストは、抜粋セクションに記載されているすべての更新されたアーティクルへのリンクを提供します。



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-sles-cluster-for-sql-server-availability-groupsql-server-linux-availability-group-cluster-slesmd"></a>1.&nbsp;[SLES クラスター SQL Server 可用性グループの構成](sql-server-linux-availability-group-cluster-sles.md)

*Updated: 2017-06-22* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 189.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f8d28af253be1dc67615f1ea04135b2f6dff3b71 8be07deddcf0c348d75bf5b4f44615c2383e0722  (PR=2150  ,  Filename=sql-server-linux-availability-group-cluster-sles.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=6dccaff93a6c8b2374a1fad069b2f597898802fc) -->



**開始-障害が-致命的でクラスターのプロパティが false に設定します。**


`Start-failure-is-fatal`ノードにリソースを起動しますの失敗によってそのノードに対して試行された開始でがさらにかどうかを示します。 設定すると`false`クラスターが、リソースの現在の失敗数と移行のしきい値に基づいて、もう一度同じノードで起動するかどうかを決定します。 そのため、フェールオーバーが発生した後にペース再試行、可用性グループ リソースで開始以前のプライマリ SQL インスタンスが使用可能にします。 ペースが対処するセカンダリ レプリカを降格して、可用性グループを自動的に再参加がします。 また場合、`start-failure-is-fatal`に設定されている`false`クラスターは移行しきい値で構成されている移行しきい値が適宜更新の既定値のことを確認する必要があるので、構成された failcount 制限にフォールバックします。

False 実行するようにプロパティの値を更新します。
```
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
プロパティ値を持つ場合、既定の`true`リソースが失敗した、ユーザーの介入を開始する最初の試行後、リソースの失敗した回数をクリーンアップするには、自動フェールオーバーが必要なとを使用して構成をリセットする場合は、:`sudo crm resource cleanup <resourceName>`コマンド。

ペース クラスターのプロパティの詳細についてを参照してください[クラスター リソースの構成](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html)です。

**フェンス操作 (STONITH) を構成します。**

ペース クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスが必要です。 ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、既知の状態をクラスターに戻すにフェンス操作が使用されます。
主ににより、リソース レベルのフェンス操作はリソースを構成することにより、障害が発生した場合、データの破損がないことです。 リソース レベルのフェンス操作を使用するインスタンスのように古くなった場合に、ノード上のディスクをマークする DRBD (レプリケート ブロック デバイスの分散) との通信リンクがダウンしました。




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>2.&nbsp;[Linux 上の SQL Server 2017 のリリース ノート](sql-server-linux-release-notes.md)

*Updated: 2017-06-20* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 156.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 684da20f7834000886d7a93f83563c55dc3cf9a6 8597bcde7e5754bb7f38de1ec980027245dac6e5  (PR=2115  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=424a23fd98876db808b91f017e7acbcb5b4daa45) -->



**SQL Server Integration Services (SSIS)**

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





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>類似した記事

このセクションには、同じ GitHub.com リポジトリ内の他のサブジェクト領域で、最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示されます: [MicrosoftDocs/**sql docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/)です。

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新規または最近更新されたアーティクルを持つサブジェクト領域

- [新しい + 更新 (4 + 4): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (2 + 0): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (1 + 2): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (6 + 0): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (13 + 2): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (1 + 0): **SQL のように、マスター データ サービス (MDS)** docs](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (1 + 0): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (8 + 4):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (2 + 2): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (1 + 0): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)
- [新しい + 更新 (1 + 0): **Tools for SQL** docs](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>サブジェクト領域に新規または最近更新されたアーティクルを持たない

- [新しい + 更新 (0 0 以降): **SQL のように、ActiveX データ オブジェクト (ADO)** docs](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新しい + 更新 (0 0 以降): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL 用の PowerShell** docs](../powershell/new-updated-powershell.md)
- [新しい + 更新 (0 0 以降): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../sample/new-updated-sample.md)
- [新しい + 更新 (0 0 以降): **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)


&nbsp;


