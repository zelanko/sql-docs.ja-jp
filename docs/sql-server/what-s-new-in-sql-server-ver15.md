---
title: SQL Server 2019 の新機能 | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 015a6d65f1d225ab5a8752352d41fd2201f871b5
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461117"
---
# <a name="whats-new-in-sql-server-2019"></a>SQL Server 2019 の新機能

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

以前のリリースを基にして構築された [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]では、開発言語、データ型、オンプレミスまたはクラウド、オペレーティング システムを選択できるプラットフォームとしての SQL Server がいっそう成長しています。 この記事では、SQL Server 2019 の新機能をまとめます。 詳細および既知の問題については、「[SQL Server 2019 Release Notes](sql-server-ver15-release-notes.md)」(SQL Server 2019 リリース ノート) をご覧ください。

**SQL Server 2019 をお試しください。**
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [SQL Server 2019 をダウンロードして Windows にインストールする](http://go.microsoft.com/fwlink/?LinkID=862101)
- [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md)、[SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)、および [Ubuntu](../linux/quickstart-install-connect-ubuntu.md) の Linux にインストールする。
- [Docker で SQL Server 2019 を実行する](../linux/quickstart-install-connect-docker.md)。

## <a name="ctp-20"></a>CTP 2.0 

Community Technology Preview (CTP) 2.0 は、[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]の最初のパブリック リリースです。 [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.0 に関しては、以下の機能が追加または強化されています。

- [ビッグ データ クラスター](#bigdatacluster)
  - SQL および Spark Linux コンテナーを使用するビッグ データ クラスターを Kubernetes にデプロイする
  - HDFS からビッグ データにアクセスする
  - Spark で高度な分析と機械学習を実行する
  - SQL データ プールへのデータに Spark ストリーミングを使用する
  - Azure Data Studio を使用して、ノートブック エクスペリエンスを提供するクエリ ブックを実行する

- [データベース エンジン](#databaseengine)
  - UTF-8 のサポート
  - 再開可能なオンライン インデックス作成により、インデックス作成を中断後に再開できる
  - クラスター化列ストアのオンライン インデックスのビルドとリビルド
  - セキュア エンクレーブを使用する Always Encrypted
  - インテリジェントなクエリ処理
  - Java 言語のプログラミング機能の拡張
  - SQL グラフ機能
  - オンラインおよび再開可能な DDL 操作に対するデータベース スコープの構成設定
  - Always On 可用性グループ - セカンダリ レプリカの接続のリダイレクト
  - データの検出と分類 - SQL Server へのネイティブな組み込み
  - 永続メモリ デバイスの拡張サポート
  - `DBCC CLONEDATABASE` での列ストア統計のサポート
  - `sp_estimate_data_compression_savings` に追加された新しいオプション
  - SQL Server Machine Learning Services フェールオーバー クラスター
  - 既定で有効になる軽量クエリ プロファイリング インフラストラクチャ
  - 新しい Polybase コネクタ
  - ページ情報を返す新しい `sys.dm_db_page_info` システム関数

- [SQL Server on Linux](#sqllinux)
  - レプリケーションのサポート
  - Microsoft 分散トランザクション コーディネーター (MSDTC) のサポート
  - Kubernetes を使用する Docker コンテナー上の Always On 可用性グループ
  - サード パーティの AD プロバイダーに対する OpenLDAP のサポート
  - Linux 上の Machine Learning
  - 新しいコンテナー レジストリ
  - 新しい RHEL ベースのコンテナー イメージ
  - メモリ不足の通知

- [マスター データ サービス](#mds)
  - Silverlight コントロールの置き換え

- [Security](#security)
  - SQL Server 構成マネージャーでの証明書管理

- [ツール](#tools)
  - SQL Server Management Studio (SSMS) 18.0 (プレビュー)
  - Azure Data Studio

これらの機能の詳細については、以下をお読みください。

## <a id="bigdatacluster"></a>ビッグ データ クラスター

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)により、次のような新しいシナリオが可能になります。

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および Spark Linux コンテナーを使用するビッグ データ クラスターを Kubernetes にデプロイする
- HDFS からビッグ データにアクセスする
- Spark で高度な分析と機械学習を実行する
- SQL データ プールへのデータに Spark ストリーミングを使用する
- [**Azure Data Studio**](../sql-operations-studio/what-is.md) でノートブック エクスペリエンスを提供するクエリ ブックを実行する。
  
[!INCLUDE [Big Data Clusters preview](../includes/big-data-cluster-preview-note.md)]

## <a id="databaseengine"></a>データベース エンジン

CTP 2.0 では、[!INCLUDE[ssdeNoVersion](../includes/ssdenoversion_md.md)] の次の新機能が導入または強化されています。

### <a name="database-compatibility-level"></a>データベース互換性レベル

データベースの **COMPATIBILITY_LEVEL 150** が追加されています。 特定のユーザー データベースに対して有効にするには、次のコマンドを実行します。

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support"></a>UTF-8 のサポート

インポートまたはエクスポートのエンコードとして、あるいはテキスト データのデータベース レベルまたは列レベルの照合順序としての、広く使用されている UTF-8 文字エンコードの完全なサポート。 UTF-8 は、`CHAR` および `VARCHAR` データ型で許可されており、`UTF8` サフィックスを持つオブジェクトの照合順序を作成したり、照合順序をそれに変更したりすると有効になります。 

たとえば、`LATIN1_GENERAL_100_CI_AS_SC` を `LATIN1_GENERAL_100_CI_AS_SC_UTF8` に変更するような場合です。 UTF-8 は、SQL Server 2012 で導入された補助文字をサポートする Windows 照合順序にのみ使用できます。 `NCHAR` および `NVARCHAR` では UTF-16 エンコードのみが許可され、変更されていません。

使用されている文字セットによっては、この機能によりストレージを大幅に節約できます。 たとえば、ASCII 文字列の既存の列データ型を、UTF-8 対応の照合順序を使用して `NCHAR(10)` から `CHAR(10)` に変更すると、必要なストレージが約 50% 削減されます。 このように減るのは、`NCHAR(10)` を保存するには 22 バイト必要であるのに対し、`CHAR(10)` では同じ Unicode 文字列に 12 バイトしか必要ないためです。

### <a name="resumable-online-index-create"></a>再開可能なオンライン インデックスの作成

- **再開可能なオンライン インデックスの作成**により、インデックス作成操作が一時停止しても、最初からやり直すのではなく、操作が一時停止または失敗した場所から後で再開できます。

  再開可能なオンライン インデックス作成では次のシナリオがサポートされています。
  - インデックスの作成が失敗した後で、インデックス作成操作を再開します (データベースのフェールオーバー後や、ディスク領域が不足した後など)。
  - 実行中のインデックス作成操作を一時停止し、後で再開することで、必要なシステム リソースを一時的に解放できます。
  - 多くのログ領域と、他のメンテナンス アクティビティをブロックしてログが切り捨てられる実行時間の長いトランザクションを使用することなく、大きなインデックスを作成します。

  この機能がないと、インデックス作成が失敗した場合、オンライン インデックス作成操作を最初からもう一度実行する必要があります。

このリリースでは、この機能を追加する再開可能機能を[再開可能なオンライン インデックス再構築](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/)に拡張します。

さらに、[オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)を使用して、特定のデータベースに対する既定値としてこの機能を設定できます。

詳しくは、[再開可能なオンライン インデックス作成](../t-sql/statements/create-index-transact-sql.md#resumable-indexes)に関する記事をご覧ください。

### <a name="build-and-rebuild-clustered-columnstore-indexes-online"></a>クラスター化列ストア インデックスのオンラインのビルドとリビルド

行ストア テーブルを列ストア形式に変換します。 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、クラスター化列ストア インデックス (CCI) の作成はオフラインのプロセスで、CCI の作成中はすべての変更を停止する必要がありました。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] および [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] では、CCI をオンラインで作成または再作成できます。 ワークロードはブロックされず、基になるデータに対するすべての変更はターゲットの列ストア テーブルに透過的に追加されます。 使用できる新しい [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの例を次に示します。

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

### <a name="always-encrypted-with-secure-enclaves"></a>セキュア エンクレーブを使用する Always Encrypted

インプレースの暗号化と高度な計算で Always Encrypted を拡張します。 拡張は、サーバー側のセキュリティ エンクレーブ内でプレーンテキスト データに対する計算を有効にすることによって行われます。

暗号化操作には、列の暗号化と、列暗号化キーのローテーションが含まれます。 これらの操作は [!INCLUDE[tsql](../includes/tsql-md.md)] を使用して発行でき、データベースから外にデータを移動する必要ありません。 セキュア エンクレーブでは、次の要件が両方ともある広範なシナリオのセットに Always Encrypted が提供されます。  

- データベース管理者、システム管理者、クラウド オペレーター、マルウェアなど、高い特権を持ちながら承認されていないユーザーから機密データが保護する必要がある。
- 保護されたデータに対する高度な計算がデータベース システム内でサポートされている必要がある。

詳しくは、「[Always Encrypted with secure enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md)」(セキュア エンクレーブを使用する Always Encrypted) をご覧ください。

> [!NOTE]
> セキュア エンクレーブを使用する Always Encrypted は、Windows OS でのみ使用できます。

### <a name="intelligent-query-processing"></a>インテリジェントなクエリ処理

- **行モード メモリ許可フィードバック**は、バッチ モードと行モード両方の演算子のメモリ許可サイズを調整することにより、[!INCLUDE[ssSQL17](../includes/sssql17-md.md)] で導入されたメモリ許可フィードバックの機能を拡張します。  メモリ許可条件が過剰な場合、許可されるメモリが実際に使われるメモリ サイズの 2 倍より多いと、メモリ許可フィードバックはメモリ許可を再計算します。 その後は、連続実行で要求されるメモリが少なくなります。 メモリ許可が過少な場合、ディスクへの書き込みが発生すると、メモリ許可フィードバックはメモリ許可の再計算をトリガーします。 その後は、連続実行で要求されるメモリが多くなります。 この機能は、データベース互換性レベル 150 では既定で有効です。

- **概算 COUNT DISTINCT** は、グループ内の一意の非 null 値の概数を返します。 この関数は、ビッグ データのシナリオで使用するために設計されています。 この関数は、次の条件がすべて満たされるクエリ向けに最適化されています。
   - 数百万行以上のデータ セットにアクセスする。
   - 多数の個別値を持つ 1 つまたは複数の列を集計する。
   - 絶対的な精度より応答性が重視される。
      - 通常、`APPROX_COUNT_DISTINCT` は正確な答の 2% 以内の結果を返します。
      - 正確な答に必要な時間より短い時間で、おおよその答を返します。

- **行ストアのバッチ モード**では、バッチ モードでクエリを処理するのに列ストア インデックスが不要になりました。 バッチ モードのクエリ演算子は、一度に 1 行だけでなく、行のセットを処理できます。 この機能は、データベース互換性レベル 150 では既定で有効です。 次のすべてが当てはまる場合、行ストア テーブルにアクセスするクエリはバッチ モードによって速度が向上します。
   - クエリで、結合や集計演算子などの分析演算子が使用されている。
   - クエリに 100,000 行以上が関係する。
   - クエリが、入力/出力データ バインドではなく CPU バインドである。
   - 列ストア インデックスを作成して使用すると、次のいずれかの欠点がある。
      - クエリに加わるオーバーヘッドが大きすぎる。
      - 列ストア インデックスでまだサポートされていない機能に依存するアプリケーションのため不可能である。

- **テーブル変数の遅延コンパイル**を使用すると、テーブル変数を参照するクエリのプランの品質および全体的なパフォーマンスが向上します。 最適化と最初のコンパイルの実行中に、この機能は実際テーブル変数の行数に基づくカーディナリティの推定を反映します。  この正確な行数の情報は、ダウンストリーム プラン操作を最適化するために使用されます。 この機能は、データベース互換性レベル 150 では既定で有効です。

インテリジェントなクエリ処理機能を使用するには、データベースを `COMPATIBILITY_LEVEL = 150` に設定します。

### <a id="programmability"></a> Java 言語のプログラミング機能の拡張

- **Java 言語拡張機能 (プレビュー)**: Java 言語の拡張機能を使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で Java コードを実行します。 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、機能 "Machine Learning Services (データベース内)" を SQL Server インスタンスに追加すると、この拡張機能がインストールされます。

### <a id="sqlgraph"></a> SQL グラフ機能

- **`MERGE` DML での一致サポート**を使用すると、個別の `INSERT`、`UPDATE`、または `DELETE` ステートメントではなく、単一のステートメントでグラフのリレーションシップを指定できます。 `MERGE` ステートメントの `MATCH` 述語を使用して、新しいデータがあるノードまたはエッジ テーブルから現在のグラフ データをマージします。 この機能により、エッジ テーブルでの `UPSERT` シナリオが可能になります。 ユーザーは 1 つのマージ ステートメントを使用して、2 つのノードの間で、新しいエッジを挿入したり、既存のエッジを更新したりできます。

- **エッジ制約**が SQL グラフのエッジ テーブルに導入されます。 エッジ テーブルは、任意のノードをデータベース内の他の任意のノードに接続できます。 エッジ制約の導入により、この動作にいくつかの制限を適用できるようになります。 新しい `CONNECTION` 制約を使用して、特定のエッジ テーブルが接続できるノードの種類をスキーマで指定できます。

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations"></a>オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定 

- **オンラインおよび再開可能な DDL 操作に対するデータベース スコープの既定の設定**では、データベース レベルで `ONLINE` と `RESUMABLE` のインデックス操作に対して既定の動作を設定できます。インデックスの作成や再構築などの個々のインデックス DDL ステートメントごとにこれらのオプションを定義する必要はありません。

- これらの既定値は、データベース スコープの構成オプション `ELEVATE_ONLINE` と `ELEVATE_RESUMABLE` を使用して設定します。 いずれのオプションでも、エンジンはサポートされる操作をオンラインまたは再開可能のインデックス実行に自動昇格します。 これらのオプションを使用して、次の動作を有効にできます。

  - `FAIL_UNSUPPORTED` オプションでは、すべてのインデックス操作がオンラインまたは再開可能を許可され、オンラインまたは再開可能をサポートされていないインデックス操作は失敗します。
  - `WHEN_SUPPPORTED` オプションでは、サポートされている操作はオンラインまたは再開可能を許可され、サポートされていない操作はオフラインまたは再開不可能で実行されます。
  - `OFF` オプションでは、DDL ステートメントで明示的に指定されていない限り、すべてのインデックス操作をオフラインと再開不可能で実行する現在の動作が許可されます。

既定の設定を上書きするには、ONLINE または RESUMABLE オプションをインデックスの作成および再構築コマンドで指定します。  

この機能がないと、インデックスの作成や再構築などのインデックス DDL ステートメントで、オンラインおよび再開可能のオプションを直接指定する必要があります。

詳細情報: インデックスの再開可能な操作について詳しくは、「[再開可能なインデックス操作](http://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/)」をご覧ください。

### <a id="ha"></a>Always On 可用性グループ - 同期レプリカの増加 

- **最大 5 つの同期レプリカ**: [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] では 3 つであった同期レプリカの最大数が、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では 5 つに増加します。 この 5 つのレプリカのグループを、グループ内で自動フェールオーバーするように構成できます。 1 つのプライマリ レプリカと、4 つの同期セカンダリ レプリカがあります。

- **セカンダリ レプリカからプライマリ レプリカへの接続のリダイレクト**: 接続文字列に指定されたターゲット サーバーに関係なく、クライアント アプリケーションの接続をプライマリ レプリカに向けることができます。 この機能により、リスナーなしで接続をリダイレクトできます。 次のような場合に、セカンダリ レプリカからプライマリ レプリカへの接続のリダイレクトを使用します。

  - クラスター テクノロジでリスナー機能が提供されていない。
  - リダイレクトが複雑になるマルチ サブネット構成。
  - クラスターの種類が `NONE` である読み取りスケールアウトまたはディザスター リカバリーのシナリオ。

詳しくは、「[セカンダリからプライマリ レプリカへの読み取り/書き込み接続のリダイレクト (Always On 可用性グループ)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md)」をご覧ください。

### <a name="data-discovery-and-classification"></a>データの検出と分類

データの検出と分類では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にネイティブに組み込まれた高度な機能が提供されます。 最も機密性の高いデータの分類とラベル付けには、次のような利点があります。
- データのプライバシーに関する基準と規制のコンプライアンス要件を満たすのに役立ちます。
- 監視 (監査) や、機密データへの異常アクセスに対するアラートなど、セキュリティ シナリオをサポートします。
- 企業内で機密データが存在する場所を識別しやすくなるので、管理者はデータベースをセキュリティで保護する適切な手順を実行できます。

詳しくは、「[SQL データの検出と分類](../relational-databases/security/sql-data-discovery-and-classification.md)」をご覧ください。

[監査](../relational-databases/security/auditing/sql-server-audit-database-engine.md)も、新しいフィールド `data_sensitivity_information` が監査ログに追加されて強化されました。このフィールドには、クエリによって返された実際のデータの機密度の分類 (ラベル) が記録されます。 詳細と例については、「[ADD SENSITIVITY CLASSIFICATION](../t-sql/statements/add-sensitivity-classification-transact-sql.md)」をご覧ください。

>[!NOTE]
>監査を有効にする方法についての変更はありません。 監査レコードには、新しいフィールド `data_sensitivity_information` が追加されています。このフィールドには、クエリによって返された実際のデータの機密度の分類 (ラベル) が記録されます。 「[機密データへのアクセスの監査](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3)」をご覧ください。

### <a name="expanded-support-for-persistent-memory-devices"></a>永続メモリ デバイスの拡張サポート

永続メモリ デバイスに配置されるすべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ファイルが、"*エンライト化*" モードで動作できるようになりました。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、効率的な memcpy 操作を使用してオペレーティング システムのストレージ スタックをバイパスし、デバイスに直接アクセスします。 このモードでは、このようなデバイスに対して低遅延の入力/出力が許可されるので、パフォーマンスが向上します。
    - たとえば、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には次のようなファイルが含まれます。
        - データベース ファイル
        - トランザクション ログ ファイル
        - インメモリ OLTP チェックポイント ファイル
    - 永続メモリは、ストレージ クラス メモリとも呼ばれます。
    - 永続メモリは、Microsoft 以外の Web サイトでは非公式に *pmem* と呼ばれることがあります。

> [!NOTE]
> このプレビュー リリースでは、永続メモリ デバイス上のファイルのエンライトメントは Linux でのみ利用できます。 Windows 上の SQL Server では、SQL Server 2016 以降で永続メモリ デバイスがサポートされています。

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase"></a>DBCC CLONEDATABASE での列ストア統計のサポート

`DBCC CLONEDATABASE` では、データをコピーすることなく、クエリのパフォーマンスに関する問題のトラブルシューティングに必要なすべての要素を含むスキーマのみのデータベースのコピーが作成されます。  以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のコマンドでは、列ストア インデックスのクエリのトラブルシューティングを正確に行うために必要な統計情報がコピーされず、手作業でこの情報をキャプチャする必要がありました。 現在の [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] の DBCC CLONEDATABASE では、列ストア インデックスの統計 BLOB が自動的にキャプチャされるので、手作業は必要ありません。

### <a name="new-options-added-to-spestimatedatacompressionsavings"></a>sp_estimate_data_compression_savings に追加された新しいオプション

`sp_estimate_data_compression_savings` は、要求されたオブジェクトの現在のサイズ、および要求された圧縮状態での推定オブジェクト サイズを返します。  現在、このプロシージャでは、`NONE`、`ROW`、`PAGE` の 3 つのオプションがサポートされています。 SQL Server 2019 では、2 つの新しいオプション `COLUMNSTORE` と `COLUMNSTORE_ARCHIVE` が導入されます。 これらの新しいオプションを使用すると、標準またはアーカイブいずれかの列ストア圧縮を使用してテーブルに列ストア インデックスを作成した場合に節約される領域を見積もることができます。

### <a id="ml"></a> SQL Server Machine Learning Services フェールオーバー クラスターとパーティション ベースのモデリング

- **パーティション ベースのモデリング**: `sp_execute_external_script` 追加される新しいパラメーターを使用すると、データのパーティションごとに外部スクリプトが処理されます。 この機能は、1 つの大きいモデルではなく、多数の小さいモデル (データのパーティションごとに 1 つのモデル) のトレーニングをサポートします。

- **Windows Server フェールオーバー クラスター**: Windows Server フェールオーバー クラスター上の Machine Learning Services に対して高可用性を構成します。

詳しくは、「[What's new in SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)」(SQL Server Machine Learning Services の新機能) をご覧ください。

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default"></a>既定で有効になる軽量クエリ プロファイリング インフラストラクチャ

軽量クエリ プロファイリング インフラストラクチャ (LWP) では、標準プロファイリング テクノロジより効率的にクエリのパフォーマンス データが提供されます。 軽量プロファイリングが既定で有効になるようになりました。 この機能は、[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 で導入されました。 軽量プロファイリングでは推定 2% の CPU オーバーヘッドでクエリ実行統計コレクション メカニズムが提供されるのに対し、標準クエリ プロファイリング メカニズムでは最大 75% の CPU オーバーヘッドが発生します。 以前のバージョンでは、既定ではオフでした。 データベース管理者は、[トレース フラグ 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) でこの機能を有効にできます。 

軽量プロファイリングについて詳しくは、「[Developers Choice: Query progress - anytime, anywhere](http://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/)」(開発者の選択: クエリの進行状況 - いつでも、どこでも) をご覧ください。

### <a id="polybase"></a>新しい Polybase コネクタ

- **[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Oracle、Teradata、MongoDB 用の新しいコネクタ**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、Oracle、Teradata、および MongoDB 用に外部データへの新しいコネクタが導入されています。

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information"></a>ページ情報を返す新しい sys.dm_db_page_info システム関数

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` では、データベースでのページに関する情報が返されます。 この関数では、`object_id`、`index_id`、`partition_id` など、ページからのヘッダー情報を含む行が返されます。 この関数を使用すると、ほとんどの場合に `DBCC PAGE` を使用する必要がなくなります。  

ページ関連の待機のトラブルシューティングを容易にするため、page_resource という名前の新しい列も `sys.dm_exec_requests` と `sys.sysprocesses` に追加されました。 この新しい列を使用すると、別の新しいシステム関数 `sys.fn_PageResCracker` を介して、これらのビューに `sys.dm_db_page_info` を結合できます。 例として、次のスクリプトをご覧ください。

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server on Linux

- **レプリケーションのサポート**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、Linux での SQL Server レプリケーションがサポートされています。 SQL エージェントを備えた Linux 仮想マシンは、パブリッシャー、ディストリビューター、またはサブスクライバーになることができます。 

  次の種類のパブリケーションを作成します。
  - トランザクション
  - スナップショット
  - Merge

  レプリケーション [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を構成するか、または[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)を使用します。

- **Microsoft 分散トランザクション コーディネーター (MSDTC) のサポート**: SQL Server 2019 on Linux では、Microsoft 分散トランザクション コーディネーター (MSDTC) がサポートされています。 詳しくは、「[How to configure MSDTC on Linux](../linux/sql-server-linux-configure-msdtc.md)」(Linux で MSDTC を構成する方法) をご覧ください。

- **Kubernetes を使用する Docker コンテナーでの Always On 可用性グループ**: Kubernetes は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで実行されているコンテナーを調整して、SQL Server Always On 可用性グループで高可用性のデータベース セットを提供できます。 Kubernetes オペレーターは、**mssql-server コンテナー**と正常性モニターを備えたコンテナーを含む StatefulSet をデプロイします。

- **サード パーティの AD プロバイダーに対する OpenLDAP のサポート**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] on Linux は OpenLDAP をサポートしているので、サード パーティのプロバイダーが Active Directory に参加できます。

- **Linux での Machine Learning**: SQL Server 2019 Machine Learning Services (データベース内) が Linux でサポートされるようになりました。 サポートには、`sp_execute_external_script` ストアド プロシージャが含まれます。 Linux に Machine Learning Services をインストールする方法については、「[Install SQL Server 2019 Machine Learning Services R and Python support on Linux](../linux/sql-server-linux-setup-machine-learning.md)」(R と Python をサポートする SQL Server 2019 Machine Learning Services を Linux にインストールする) をご覧ください。

- **新しい コンテナー レジストリ**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] および [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] のすべてのコンテナー イメージが、Microsoft Container Registry に格納されるようになります。 Microsoft Container Registry は、Microsoft 製品のコンテナーを配布するための公式のコンテナー レジストリです。 さらに、認定された RHEL ベースのイメージが発行されるようになります。

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - 認定済みの RHEL ベースのコンテナー イメージ: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a> マスター データ サービス (MDS)

- **Silverlight コントロールの HTML への置き換え**: マスター データ サービス (MDS) ポータルは、Silverlight に依存しなくなりました。 以前の Silverlight コンポーネントはすべて、HTML コントロールに置き換えられました。

## <a id="security"></a>Security

- **SQL Server 構成マネージャーでの証明書管理**: SSL/TLS 証明書は、SQL Server インスタンスへのアクセスをセキュリティで保護するために広く使われています。 証明書の管理が SQL Server 構成マネージャーに統合され、次のような一般的なタスクが簡単になりました。

  - [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスにインストールされている証明書の表示と検証。 
  - 有効期限が近い証明書の表示。
  - Always On 可用性グループに参加しているコンピューターへの証明書の展開 (プライマリ レプリカを保持するノードから)。
  - フェールオーバー クラスター インスタンスに参加しているコンピューターへの証明書の展開 (アクティブなノードから)。

  > [!NOTE]
  > ユーザーには、すべてのクラスター ノードでの管理者権限が必要です。

## <a id="tools"></a>ツール

- [**Azure Data Studio**](../azure-data-studio/what-is.md): 以前は SQL Operations Studio というプレビュー名でリリースされていた Azure Data Studio は、軽量、最新、オープン ソース、クロスプラットフォームのデスクトップ ツールであり、データの開発と管理におけるほとんどの一般的なタスクに対応します。 Azure Data Studio を使用すると、オンプレミスおよびクラウドの Windows、macOS、Linux 上の SQL Server に接続できます。 Azure Data Studio では次のことができます。

  - 非常に高速の Intellisense、コード スニペット、ソース管理が統合された最新の開発環境で、クエリを編集して実行できます。  
  - 組み込まれている結果セット グラフ化機能を使用して、すばやくデータを視覚化できます。  
  - カスタマイズ可能なウィジェットを使用して、サーバーおよびデータベース用のカスタム ダッシュボードを作成できます。  
  - 組み込みのターミナルを使用して、広範な環境を簡単に管理できます。  
  - Jupyter を基に構築された統合ノートブック エクスペリエンスでデータを分析できます。  
  - カスタム テーマと拡張機能を使用して自分のエクスペリエンスを拡張できます。  
  - 組み込まれているサブスクリプションとリソースのブラウザーを使用して、Azure リソースを調べることができます。
  - SQL Server ビッグ データ クラスターを使用するシナリオをサポートできます。


- [**SQL Server Management Studio (SSMS) 18.0 (プレビュー)**](../ssms/sql-server-management-studio-ssms.md)

  - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] をサポートします。
  - セキュリティで保護されたエンクレーブが設定された Always Encrypted をサポートします。
  - ダウンロード サイズが小さくなりました。
  - Visual Studio 2017 Isolated Shell に基づくようになりました。
  - 完全な一覧については、[SSMS の変更ログ](../ssms/sql-server-management-studio-changelog-ssms.md)に関する記事をご覧ください。

## <a name="other-services"></a>その他のサービス

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 では、次のサービスに関する新機能は導入されていません。

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>次の手順

- [SQL Server 2019 リリース ノート](sql-server-ver15-release-notes.md)

- [Microsoft SQL Server 2019: テクニカル ホワイト ペーパー](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />2018 年 9 月に公開されました。 Windows、Linux、Docker コンテナー向けの Microsoft SQL Server 2019 CTP 2.0 に適用されます。


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
