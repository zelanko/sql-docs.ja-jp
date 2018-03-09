---
title: "SQL Server のドキュメントへの接続の更新 |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、Microsoft SQL Server への接続の更新されたコンテンツのスニペットを表示します。"
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: connect
ms.date: 02/03/2018
ms.openlocfilehash: cc4eb05dc4dcd74623c8ce7dfa7b7842449d79b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>新規または最近更新された: SQL Server に接続



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-12-03** &nbsp;対&nbsp; **2018-02-03**
- *サブジェクト領域:* &nbsp; **SQL Server への接続**です。




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

1. [SQL Server 用 ODBC ドライバーで Always Encrypted を使用します。](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-using-always-encrypted-with-the-odbc-driver-for-sql-serverodbcusing-always-encrypted-with-the-odbc-drivermd"></a>1.&nbsp;[For SQL Server ODBC ドライバーで Always Encrypted を使用します。](odbc/using-always-encrypted-with-the-odbc-driver.md)

*最終更新日: 2018-01-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 524.  ms.author= "v-chojas".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a52abae2a8f27c3b5bc411ef758610116a608f9f 352368eb269b98ab5ca3a9791fae2e70bf26277a  (PR=4686  ,  Filename=using-always-encrypted-with-the-odbc-driver.md  ,  Dirpath=docs\connect\odbc\  ,  MergeCommitSha40=82c9868b5bf95e5b0c68137ba434ddd37fc61072) -->



**SQLGetData を使用してパーツ内のデータを取得します。**

SQL Server 用 ODBC ドライバーの 17 暗号化前に文字とバイナリ列は、SQLGetData を使用してパーツで取得できません。 列全体のデータを格納するための十分な長さのバッファーが、SQLGetData を 1 つだけの呼び出しを作成できます。

**SQLPutData を使用してパーツでデータを送信します。**

SQLPutData を使用してパーツでは、データを挿入または比較を送信できません。 全体のデータを格納するバッファーと、SQLPutData のみ 1 回の呼び出しを作成できます。 長い形式のデータを暗号化された列に挿入するためには、入力データ ファイルを使用して、次のセクションで説明されている、一括コピー API を使用します。

**暗号化された money および smallmoney**

暗号化**money**または**smallmoney**列は、パラメーターの対象となることはできません、ODBC データ型のオペランド型の競合エラーでその結果、それらの型に対応する関連があるためです。

**暗号化された列の一括コピー**


使用、 [SQL 一括コピー関数](odbc/../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)と**bcp** for SQL Server ODBC ドライバーの 17 以降、ユーティリティが Always Encrypted でサポートされています。 挿入することができます (では暗号化された挿入およびで復号化された取得) のプレーン テキストと (そのまま転送) の暗号化テキストの両方と、一括コピー (bcp_ *) Api を使用して取得し、 **bcp**ユーティリティです。

- Varbinary (max) 形式 (たとえば、別のデータベースに読み込む一括) で暗号化テキストを取得せずに接続する、`ColumnEncryption`オプション (またはに設定する`Disabled`) BCP OUT 操作を実行するとします。

- 挿入し、プレーン テキストを取得および、ドライバーが暗号化および復号化、必要な設定としてを透過的に実行できるように`ColumnEncryption`に`Enabled`だけで十分です。 BCP API の機能は、それ以外の場合変更されません。

- Varbinary (max) 形式 (例: 取得された上) で暗号化テキストを挿入、設定、`BCPMODIFYENCRYPTED`オプションを TRUE に設定し、BCP IN 操作を実行します。 結果として得られるデータを復号可能なためには、転送先の列の CEK が元となる、暗号化テキストの取得元と同じことを確認します。







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


