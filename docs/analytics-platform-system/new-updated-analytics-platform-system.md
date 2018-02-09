---
title: "更新済み - SQL Server ドキュメントの Analytics Platform System |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、Microsoft SQL Server の Analytics Platform System の更新されたコンテンツのスニペットを表示します。"
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: aps-pdw
ms.date: 02/03/2018
ms.openlocfilehash: 2ae6339897b52cd16ad3417cc218afe1df95ba2a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-analytics-platform-system-for-sql-server"></a>新規または最近更新された: SQL Server 用の分析プラットフォーム システム



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-12-03** &nbsp;対&nbsp; **2018-02-03**
- *サブジェクト領域:* &nbsp; **for SQL Server 分析プラットフォーム システム**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


***今回は新しい記事はありません。***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [外部データへの接続を PolyBase を構成します。](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-polybase-connectivity-to-external-dataconfigure-polybase-connectivity-to-external-datamd"></a>1.&nbsp;[外部データへの接続を PolyBase を構成します。](configure-polybase-connectivity-to-external-data.md)

*最終更新日: 2018-01-29* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 132.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 947f789480da66b9f636f39b30caec6be60d8c4d d4d4d45fbbb8e10ed6f26fe12f9a25d2e8e4f068  (PR=4741  ,  Filename=configure-polybase-connectivity-to-external-data.md  ,  Dirpath=docs\analytics-platform-system\  ,  MergeCommitSha40=0a44ce9993ebf61f86e409255a1d58d47993951a) -->



**Kerberos の構成**

Kerberos のセキュリティで保護されたクラスターに PolyBase が認証されると、ときに、hadoop.rpc.protection 設定する必要がありますに設定することの認証に注意してください。 これにより、データ通信が暗号化されていない Hadoop ノード間で残ります。

 [Using MIT KDC] Kerberos でセキュリティ保護された Hadoop クラスターに接続します。


1.  [管理] ノードでのインストール パスで Hadoop 構成ディレクトリを検索します。

    ```
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```

2.  次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。

3.  コントロールのノード上の対応するファイル内の値プロパティに、構成値をコピーします。

    |**#**|**構成ファイル**|**構成キー**|**操作**|
    |------------|----------------|---------------------|----------|
    |1|core-site.xml|polybase.kerberos.kdchost|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|
    |2|core-site.xml|polybase.kerberos.realm|Kerberos 領域を指定します。 例: YOUR-REALM.COM|
    |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|
    |6|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: 10.193.26.174:10020|
    |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|







## <a name="similar-articles-about-new-or-updated-articles"></a>新規または更新のアーティクルに関する類似の記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>サブジェクト領域を*しないで*が新規または最近更新のアーティクル


- [新しい + 更新 (1 + 3):&nbsp; **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (0 + 1):&nbsp; **sql 分析プラットフォーム システム**docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (0 + 1):&nbsp; **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (0 + 1):&nbsp; **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (12 + 1): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (6 + 2):&nbsp; **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (15 + 0): **SQL 用の PowerShell** docs](../powershell/new-updated-powershell.md)
- [新しい + 更新 (2 + 9):&nbsp; **リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (1 + 0):&nbsp; **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (1 + 1):&nbsp; **SQL 操作 Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新しい + 更新 (1 + 1):&nbsp; **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (0 + 1):&nbsp; **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (1 + 2):&nbsp; **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 2):&nbsp; **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>実行の領域をサブジェクト*いない*がいずれかの new または最近更新のアーティクル


- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新しい + 更新 (0 0 以降): **SQL のように、ActiveX データ オブジェクト (ADO)** docs](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../sample/new-updated-sample.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)


