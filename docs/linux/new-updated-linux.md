---
title: 更新済み - SQL Server on Linux docs |Microsoft ドキュメント
description: 最近変更したドキュメントについては、Microsoft SQL Server on Linux の更新されたコンテンツのスニペットを表示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: sql-linux,UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: ''
ms.date: 02/03/2018
ms.openlocfilehash: 3395059669c3bcf406e8542c97bd87b80479fccd
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2018
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>新規または最近の更新: SQL Server on Linux のドキュメント



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *"更新日の範囲:"* &nbsp; **2017 年 12 月 3 日**&nbsp;から&nbsp;**2018 年 2 月 3 日**
- *サブジェクト領域:* &nbsp; **Microsoft SQL Server on Linux**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [複数のサブネット Always On 可用性グループおよびフェールオーバー クラスター インスタンスを構成します。](sql-server-linux-configure-multiple-subnet.md)
2. [作成し、Linux 上の SQL Server の可用性グループを構成します。](sql-server-linux-create-availability-group.md)
3. [SQL Server on Linux のペース クラスターを展開します。](sql-server-linux-deploy-pacemaker-cluster.md)
4. [SQL Server on Linux Frequently Asked Questions (FAQ)](sql-server-linux-faq.md)
5. [Linux 展開用の SQL Server 可用性の基礎](sql-server-linux-ha-basics.md)
6. [Kubernetes で高可用性のため、SQL Server のコンテナーを構成します。](tutorial-sql-server-containers-kubernetes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [Always On Linux 上の可用性グループ](#TitleNum_1)
2. [抽出、変換、および SSIS Linux でのデータを読み込む](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-always-on-availability-groups-on-linuxsql-server-linux-availability-group-overviewmd"></a>1.&nbsp;[Always On Linux 上の可用性グループ](sql-server-linux-availability-group-overview.md)

*最終更新日: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 85.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 85685bc8ad3528aa26ca3f2bba7b0112808ad6f9 51aff6e55104c8f775d2b4f4461e44f689a9ee6b  (PR=4768  ,  Filename=sql-server-linux-availability-group-overview.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



自動フェールオーバー、AG は、次の条件が満たされたときにできます。

-   プライマリ レプリカとセカンダリ レプリカは、同期のデータの移動に設定されます。
-   セカンダリには、同期されている (同期中にありません)、つまり、2 つは、同じデータ ポイントでの状態があります。
-   クラスターの種類は、外部に設定されます。 自動フェールオーバーのなしのクラスターのタイプはできません。
-   `sequence_number`になるセカンダリ レプリカのプライマリが最も高いシーケンス番号: つまり、セカンダリ レプリカの`sequence_number`元のプライマリ レプリカから 1 つに一致します。

これらの条件が満たされてし、失敗した場合、プライマリ レプリカをホストしているサーバー、AG は同期レプリカへの所有権を変更します。 同期レプリカの動作は、(存在できる 3 つの合計: 1 つのプライマリ レプリカと 2 つのセカンダリ レプリカ) でさらに制御できます`required_synchronized_secondaries_to_commit`です。 これにより、Windows と Linux の両方の Ag とでも動作しますが完全に異なる方法で構成されています。 Linux では、値は AG リソース自体に、クラスターによって自動的に構成します。

**構成専用のレプリカとクォーラム**


また新しい CU1 時点での SQL Server 2017 では構成専用のレプリカです。 ペースは異なるため、WSFC よりも、クォーラムと STONITH を必要とするときに特に 2 つのノードの構成のみは機能しません、AG になります。 FCI のペースで提供されるクォーラム メカニズムもかまいません、クラスターの層のすべての FCI フェールオーバー判別が行われるためです。 AG の判別 Linux では、すべてのメタデータが格納されている SQL Server で行われます。 これは、活躍するが、構成のみのレプリカです。

せず何でも、3 番目のノードと、少なくとも 1 つの同期レプリカが必要になります。 これは、可用性グループに参加している 2 つのレプリカにしか持てないために、SQL Server Standard を使用できません。 構成専用のレプリカは、AG の構成内の他のレプリカと同じで、master データベースは、AG の構成を格納します。 構成専用レプリカには、可用性グループに参加しているユーザー データベースがありません。 構成データは、プライマリから同期的に送信されます。 自動か手動かにかかわらず、この構成データは、フェールオーバー時に使用されます。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-extract-transform-and-load-data-on-linux-with-ssissql-server-linux-migrate-ssismd"></a>2.&nbsp;[抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

*最終更新日: 2018-01-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1))

<!-- Source markdown line 50.  ms.author= lle.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9bba002ae3955ebb8376c7c85b7ec1ac8c706073 1533a8e0bfe553e5404de79129119b3f93185ee9  (PR=4768  ,  Filename=sql-server-linux-migrate-ssis.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=d4d880dd9c247d1e7fb7a728d5231bc9ac61c989) -->



    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  指定して、`/de[crypt]`対話形式で、次の例で示すように、パスワードを入力するオプション。

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de

    Enter decryption password:
    ```

3.  指定して、`/de`次の例のように、コマンド ラインで、パスワードを提供するオプションです。 このメソッドは、コマンド履歴にコマンドを使用して復号化パスワードを格納するためには推奨されません。

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test

    Warning: Using /De[crypt] <password> may store decryption password in command history.

    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

**パッケージの設計**


**ODBC データ ソースに接続**です。 Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域


- [新規 + 更新 (1 + 3):&nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (12 + 1): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (6 + 2):&nbsp;**Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (15 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (2 + 9):&nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (1 + 0):&nbsp;**SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 1):&nbsp;**SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (1 + 1):&nbsp;**Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 2):&nbsp;**SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2):&nbsp;**Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域


- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新しい + 更新 (0 0 以降): **SQL のように、ActiveX データ オブジェクト (ADO)** docs](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../samples/new-updated-samples.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)


