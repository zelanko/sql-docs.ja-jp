---
title: リリース ノート
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) の最新の更新プログラムと既知の問題について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c0dd96d4a3227fda76921764429b4566e3e5dd28
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419300"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>SQL Server 上のビッグデータクラスターのリリースノート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server ビッグデータクラスターの最新リリースに関する更新プログラムと既知の問題の一覧を示します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp32"></a>CTP 3.2 (7 月)

以下のセクションでは、SQL Server 2019 CTP 3.2 のビッグデータクラスターの新機能と既知の問題について説明します。

|新機能または更新 | 詳細 |
|:---|:---|
|パブリックプレビュー |CTP 3.2 より前の SQL Server ビッグデータクラスターは、登録済みの早期採用者に提供されました。 このリリースでは、あらゆるユーザーがビッグデータクラスター SQL Server の機能を体験できます。 <br/><br/> 「 [SQL Server ビッグデータクラスターの概要」を](deploy-get-started.md)参照してください。|
|`azdata` |CTP 3.2 の`azdata`導入-Python で作成されたコマンドラインユーティリティを使用して、クラスター管理者が REST api を使用してビッグデータクラスターをブートストラップし、管理できるようにします。 `azdata`を`mssqlctl`置き換えます。 「 [Install `azdata` ](deploy-install-azdata.md)」を参照してください。 |
|PolyBase |外部テーブルの列名は、SQL Server、Oracle、Teradata、MongoDB、および ODBC の各データソースに対してクエリを実行するために使用されるようになりました。 |
|HDFS 階層更新 |リモートデータの最新のスナップショットに対して既存のマウントを更新できるように、HDFS 階層化の更新機能を導入しました。 「 [HDFS 階層](hdfs-tiering.md)化」を参照してください。 |
|ノートブックベースのトラブルシューティング |CTP 3.2 では、Jupyter notebook が導入されており、SQL Server ビッグデータクラスター内のコンポーネントの[デプロイ](deploy-notebooks.md)と[検出、診断、トラブルシューティング](manage-notebooks.md)を支援します。 |
| &nbsp; | &nbsp; |

## <a id="ctp31"></a>CTP 3.1 (6 月)

以下のセクションでは、SQL Server 2019 CTP 3.1 のビッグデータクラスターの新機能と既知の問題について説明します。

|新機能または更新 | 詳細 |
|:---|:---|
|パブリックプレビュー |CTP 3.2 より前の SQL Server ビッグデータクラスターは、登録済みの早期採用者に提供されました。 このリリースでは、あらゆるユーザーがビッグデータクラスター SQL Server の機能を体験できます。 <br/><br/> 「 [SQL Server ビッグデータクラスターの概要」を](deploy-get-started.md)参照してください。|
|ノートブックに基づくトラブルシューティング。|CTP 3.2 では、[デプロイ](deploy-notebooks.md)を支援する Jupyter notebook と、SQL Server ビッグデータクラスター内のコンポーネントの[検出、診断、およびトラブルシューティング](manage-notebooks.md)が導入されています。 |
|`azdata` |CTP 3.2 の`azdata`導入-Python で作成されたコマンドラインユーティリティを使用して、クラスター管理者が REST api を使用してビッグデータクラスターをブートストラップし、管理できるようにします。 `azdata`を`mssqlctl`置き換えます。 「 [Install `azdata` ](deploy-install-azdata.md)」を参照してください。 |
|HDFS 階層更新 |リモートデータの最新のスナップショットに対して既存のマウントを更新できるように、HDFS 階層化の更新機能を導入しました。 「 [HDFS 階層](hdfs-tiering.md)化」を参照してください。 |
| &nbsp; | &nbsp; |

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| `mssqlctl` コマンドの変更 | `mssqlctl cluster` コマンドの名前が、`mssqlctl bdc` に変更されました。 詳しくは、[`mssqlctl` のリファレンス](reference-azdata.md)に関する記事をご覧ください。 |
| 新しい`mssqlctl`ステータスコマンドとクラスター管理ポータルの削除。 | このリリースでは、クラスター管理ポータルは削除されています。 既存の監視コマンドを補完する`mssqlctl`新しいステータスコマンドがに追加されました。 |
| Spark コンピューティング プール | ストレージをスケールアップする必要なしに、追加ノードを作成して Spark のコンピューティング能力を増強します。 さらに、Spark に使われない記憶域プールのノードを開始することができます。 Spark と記憶域は切り離されています。 詳しくは、「[Configure storage without spark (Spark なしで記憶域を構成する)](deployment-custom-configuration.md#sparkstorage)」をご覧ください。 |
| MSSQL Spark コネクタ | データ プール外部テーブルの読み取り/書き込みのサポート。 以前のリリースでは、MASTER インスタンス テーブルの読み取り/書き込みだけがサポートされていました。 詳しくは、「[How to read and write to SQL Server from Spark using the MSSQL Spark Connector (MSSQL Spark コネクタを使用して Spark から SQL Server の読み取りと書き込みを行う方法)](spark-mssql-connector.md)」をご覧ください。 |
| MLeap を使用する機械学習 | [Spark で MLeap 機械学習モデルをトレーニングし、Java 言語拡張機能を使用して SQL Server でスコアリングします](spark-create-machine-learning-model.md)。 |

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > 最新のリリースをデプロイする前に、データをバックアップしてから、(以前のバージョンの**azdata**を使用して) 既存のビッグデータクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="external-tables"></a>外部テーブル

- ビッグデータクラスターのデプロイでは、 **SqlDataPool**および**sqlstoragepool**外部データソースは作成されなくなりました。 これらのデータソースを手動で作成して、データプールと記憶域プールに対するデータの仮想化をサポートすることができます。

   > [!NOTE]
   > これらの外部データソースを作成するための URI は、Ctp 間で異なります。 次の Transact-sql コマンドを参照して、それらを作成する方法を確認してください。 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用する外部テーブルを Oracle に対して作成する場合、Azure Data Studio 仮想化ウィザードでは、これらの列は外部テーブル定義では VARCHAR として解釈されます。 これにより、外部テーブル DDL でエラーが発生します。 NVARCHAR2 型を使用するように Oracle スキーマを変更するか、外部テーブルステートメントを手動で作成して、ウィザードを使用せずに NVARCHAR を指定してください。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すと、呼び出しは5分でタイムアウトします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

#### <a name="kibana-logs-dashboards"></a>Kibana logs ダッシュボード

- Aris CTP 3.0 と3.1 の間では、Kibana のバージョンが6.3.1 から7.0.1 にアップグレードされました。  これにより、Edge ブラウザーと Kibana との互換性がなくなりました。 Edge で Kibana ダッシュボードの現在のバージョンを読み込むと、空のページが表示されます。 Kibana.rs でサポートされているブラウザーについて[は、こちら]( https://www.elastic.co/support/matrix#matrix_browse)をご覧ください。 


## <a id="ctp30"></a>CTP 3.0 (5 月)

以下のセクションでは、SQL Server 2019 CTP 3.0 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| **mssqlctl** の更新 | 複数の **mssqlctl** [コマンドとパラメーターが更新されました](reference-azdata.md)。 これには、コントローラーのユーザー名とエンドポイントをターゲットにするようになった **mssqlctl login** コマンドの更新も含まれています。 |
| ストレージの機能強化 | ログとデータのさまざまなストレージ構成のサポート。 また、ビッグ データ クラスターへの永続ボリューム要求の数が削減されました。 |
| 複数のコンピューティング プール インスタンス | 複数のコンピューティング プール インスタンスのサポート。 |
| 新しいプールの動作と機能 | コンピューティング プールは、既定で **ROUND_ROBIN** 配布内​​のストレージ プールおよびデータ プールの操作にのみ使用されるようになりました。 データ プールで新しい **REPLICATED** 分布の種類が使用できるようになりました。これは、同じデータがすべてのデータ プール インスタンスに存在することを意味します。 |
| 外部テーブルの機能強化 | HADOOP データ ソースの種類の外部テーブルで、最大サイズ 1 MB の行の読み取りがサポートされるようになりました。 外部テーブル (ODBC、記憶域プール、データ プール) で、SQL Server テーブルと同じ幅の行がサポートされるようになりました。 |

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="hdfs"></a>HDFS

- HDFS に新しいフォルダーを作成しようとすると、Azure Data Studio からエラーが返されます。 この機能を有効にするには、Azure Data Studio の insider ビルドをインストールします。
  
   - [Windows ユーザーインストーラー- **insider build**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Windows システムインストーラー- **insider ビルド**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows ZIP**内部のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [macOS ZIP- **insider ビルド**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux TAR。GZ**内部のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="deployment"></a>展開

- GPU が有効なビッグデータクラスターの前の展開手順は、CTP 3.0 ではサポートされていません。 代替の展開手順を調査しています。 ここでは、混乱を避けるために、「GPU サポートを使用したビッグデータクラスターのデプロイと、このようにして、実行されていないフローを実行する」をご覧ください。

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > 最新のリリースをデプロイする前に、データをバックアップしてから、(以前のバージョンの**azdata**を使用して) 既存のビッグデータクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="external-tables"></a>外部テーブル

- ビッグデータクラスターのデプロイでは、 **SqlDataPool**および**sqlstoragepool**外部データソースは作成されなくなりました。 これらのデータソースを手動で作成して、データプールと記憶域プールに対するデータの仮想化をサポートすることができます。

   > [!NOTE]
   > これらの外部データソースを作成するための URI は、Ctp 間で異なります。 次の Transact-sql コマンドを参照して、それらを作成する方法を確認してください。 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc/default');
   ```

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用する外部テーブルを Oracle に対して作成する場合、Azure Data Studio 仮想化ウィザードでは、これらの列は外部テーブル定義では VARCHAR として解釈されます。 これにより、外部テーブル DDL でエラーが発生します。 NVARCHAR2 型を使用するように Oracle スキーマを変更するか、外部テーブルステートメントを手動で作成して、ウィザードを使用せずに NVARCHAR を指定してください。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すと、呼び出しは5分でタイムアウトします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp25"></a>CTP 2.5 (4 月)

以下のセクションでは、SQL Server 2019 CTP 2.5 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| 展開プロファイル | ビッグ データ クラスターの展開には、環境変数の代わりに、既定およびカスタマイズした[展開構成 JSON ファイル](deployment-guidance.md#configfile)を使用します。 |
| 入力が求められる展開 | `azdata cluster create` では、既定の展開に必要な設定の入力が求められるようになりました。 |
| サービス エンドポイントとのポッド名の変更 | 次の外部エンドポイントには変更された名前があります。<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **エンドポイント-セキュリティ** => **ゲートウェイ-svc-外部**<br/>&nbsp;&nbsp;&nbsp;- **エンドポイント-アプリケーション-プロキシ** => -**svc-外部**|
| **azdata**の機能強化 | **Azdata**を使用して[外部エンドポイントを一覧表示し](deployment-guidance.md#endpoints)、 `--version`パラメーターを使用して**azdata**のバージョンを確認します。 |
| オフライン インストール | オフラインのビッグデータクラスターの展開に関するガイダンス。 |
| HDFS 階層の機能強化 | S3 の階層化、マウントキャッシュ、および ADLS Gen2 の OAuth サポート。 |
| 新しい`mssql` Spark SQL Server コネクタ | |

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > 最新のリリースをデプロイする前に、データをバックアップしてから、(以前のバージョンの**azdata**を使用して) 既存のビッグデータクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="external-tables"></a>外部テーブル

- ビッグデータクラスターのデプロイでは、 **SqlDataPool**および**sqlstoragepool**外部データソースは作成されなくなりました。 これらのデータソースを手動で作成して、データプールと記憶域プールに対するデータの仮想化をサポートすることができます。

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用する外部テーブルを Oracle に対して作成する場合、Azure Data Studio 仮想化ウィザードでは、これらの列は外部テーブル定義では VARCHAR として解釈されます。 これにより、外部テーブル DDL でエラーが発生します。 NVARCHAR2 型を使用するように Oracle スキーマを変更するか、外部テーブルステートメントを手動で作成して、ウィザードを使用せずに NVARCHAR を指定してください。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すと、呼び出しは5分でタイムアウトします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp24"></a>CTP 2.4 (3 月)

以下のセクションでは、SQL Server 2019 CTP 2.4 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| Spark で TensorFlow を使用しディープ ラーニングを実行する場合の GPU でのサポートに関するガイダンス。 | [GPU をサポートしているビッグ データ クラスターを展開し、TensorFlow を実行します](spark-gpu-tensorflow.md)。 |
| データ ソース **SqlDataPool** と **SqlStoragePool** は、既定では作成されなくなりました。 | 必要に応じてこれらを手動で作成します。 [既知の問題](#externaltablesctp24)を参照してください。 |
| データ プール用の `INSERT INTO SELECT` のサポート。 | 例については、「[Tutorial:Ingest data into a SQL Server data pool with Transact-SQL](tutorial-data-pool-ingest-sql.md)」 (チュートリアル: Transact SQL を使用して SQL Server のデータ プールにデータを取り込む) を参照してください。 |
| オプション `FORCE SCALEOUTEXECUTION` と `DISABLE SCALEOUTEXECUTION` | 外部テーブルに対するクエリに対して、コンピューティングプールの使用を強制または無効にします。 たとえば、`SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)` のようにします。 |
| 更新された AKS の展開に関する推奨事項 | AKS でビッグ データ クラスターを評価するときには、サイズ **Standard_L8s** の単一ノードを使用することをお勧めします。 |
| Spark 2.4 への Spark のランタイムのアップグレード。 | |

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > 最新のリリースをデプロイする前に、データをバックアップしてから、(以前のバージョンの**azdata**を使用して) 既存のビッグデータクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="kubeadm-deployments"></a>kubeadm のデプロイ

Kubeadm を使用して複数のコンピューターに Kubernetes をデプロイする場合、クラスター管理ポータルでは、ビッグデータクラスターへの接続に必要なエンドポイントが正しく表示されません。 この問題が発生している場合は、次の回避策を使用して、サービスエンドポイントの IP アドレスを検出します。

- クラスター内から接続している場合は、接続先のエンドポイントのサービス IP の Kubernetes をクエリします。 たとえば、次の**kubectl**コマンドを実行すると、SQL Server マスターインスタンスの IP アドレスが表示されます。

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- クラスターの外部から接続する場合は、次の手順を使用して接続します。

   1. SQL Server マスターインスタンス`kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`を実行しているノードの IP アドレスを取得します。

   1. この IP アドレスを使用して SQL Server master インスタンスに接続します。

   1. 他の外部エンドポイントについては、master データベースの**cluster_endpoint_table**に対してクエリを実行します。

      接続のタイムアウトによって失敗した場合は、それぞれのノードにファイアウォールが設定されている可能性があります。 この場合、Kubernetes クラスター管理者に連絡して、外部に公開されているノード IP を要求する必要があります。 任意のノードを指定できます。 その後、その IP と対応するポートを使用して、クラスターで実行されているさまざまなサービスに接続できます。 たとえば、管理者は次を実行してこの IP を見つけることができます。

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>クラスターの削除失敗

**Azdata**を使用してクラスターを削除しようとすると、次のエラーで失敗します。

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

新しい Python Kubernetes クライアント (バージョン 9.0.0) によって、 **azdata**を現在中断している DELETE namespace API が変更されました。 これは、新しい Kubernetes python クライアントがインストールされている場合にのみ発生します。 この問題を回避するには、 **kubectl** (`kubectl delete ns <ClusterName>`) を使用してクラスターを直接削除するか、を使用`sudo pip install kubernetes==8.0.1`して古いバージョンをインストールします。

#### <a id="externaltablesctp24"></a>外部テーブル

- ビッグデータクラスターのデプロイでは、 **SqlDataPool**および**sqlstoragepool**外部データソースは作成されなくなりました。 これらのデータソースを手動で作成して、データプールと記憶域プールに対するデータの仮想化をサポートすることができます。

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用する外部テーブルを Oracle に対して作成する場合、Azure Data Studio 仮想化ウィザードでは、これらの列は外部テーブル定義では VARCHAR として解釈されます。 これにより、外部テーブル DDL でエラーが発生します。 NVARCHAR2 型を使用するように Oracle スキーマを変更するか、外部テーブルステートメントを手動で作成して、ウィザードを使用せずに NVARCHAR を指定してください。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すと、呼び出しは5分でタイムアウトします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp23"></a>CTP 2.3 (2 月)

以下のセクションでは、SQL Server 2019 CTP 2.3 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
| :---------- | :------ |
| IntelliJ のビッグ データ クラスターでの Spark ジョブの送信。 | [IntelliJ の SQL Server ビッグ データ クラスターで Spark ジョブを送信する](spark-submit-job-intellij-tool-plugin.md) |
| アプリケーションの展開およびクラスター管理の一般的な CLI。 | [SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリを展開する方法](big-data-cluster-create-apps.md) |
| ビッグ データ クラスターにアプリケーションを展開するための VS Code の拡張機能。 | [VS Code を使用して SQL Server のビッグ データ クラスターにアプリケーションを展開する方法](app-deployment-extension.md) |
| **Azdata** tool コマンドの使用に対する変更。 | 詳細については、 [azdata に関する既知の問題](#azdatactp23)を参照してください。 |
| ビッグデータクラスターで Sparklyr を使用する | [SQL Server 2019 のビッグ データ クラスターで Sparklyr を使用する](sparklyr-from-RStudio.md) |
| **HDFS 階層**を使用した、外部の HDFS 互換ストレージのビッグ データ クラスターへのマウント。 | [HDFS 階層](hdfs-tiering.md)に関するページを参照してください。 |
| SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイの新しい統一された接続エクスペリエンス。 | [SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイ](connect-to-big-data-cluster.md)に関するページを参照してください。 |
| **Azdata クラスター**を削除してクラスターを削除すると、ビッグデータクラスターに含まれていた名前空間内のオブジェクトのみが削除されるようになりました。 | 名前空間は削除されません。 ただし、以前のリリースでは、このコマンドを使用すると、名前空間全体が削除されました。 |
| _セキュリティ_ エンドポイントの名前が変更され、統合されました。 | **service-security-lb** と **service-security-nodeport** は、**endpoint-security** エンドポイントに統合されました。 |
| _プロキシ_ エンドポイントの名前が変更され、統合されました。 | **service-proxy-lb** と **service-proxy-nodeport** は、**endpoint-service-proxy** エンドポイントに統合されました。 |
| _コントローラー_ エンドポイントの名前が変更され、統合されました。 | **service-mssql-controller-lb** と **service-mssql-controller-nodeport** は、**endpoint-controller** エンドポイントに統合されました。 |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > 最新のリリースをデプロイする前に、データをバックアップしてから、(以前のバージョンの**azdata**を使用して) 既存のビッグデータクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- 使用許諾契約書に同意するには、 **ACCEPT_EULA**環境変数を "yes" または "yes" に設定する必要があります。 以前のリリースでは "y" と "Y" が許可されていましたが、これらは受け入れられず、デプロイは失敗します。

- **CLUSTER_PLATFORM**環境変数には、以前のリリースと同様に既定値がありません。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="kubeadm-deployments"></a>kubeadm のデプロイ

Kubeadm を使用して複数のコンピューターに Kubernetes をデプロイする場合、クラスター管理ポータルでは、ビッグデータクラスターへの接続に必要なエンドポイントが正しく表示されません。 この問題が発生している場合は、次の回避策を使用して、サービスエンドポイントの IP アドレスを検出します。

- クラスター内から接続している場合は、接続先のエンドポイントのサービス IP の Kubernetes をクエリします。 たとえば、次の**kubectl**コマンドを実行すると、SQL Server マスターインスタンスの IP アドレスが表示されます。

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- クラスターの外部から接続する場合は、次の手順を使用して接続します。

   1. SQL Server マスターインスタンス`kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`を実行しているノードの IP アドレスを取得します。

   1. この IP アドレスを使用して SQL Server master インスタンスに接続します。

   1. 他の外部エンドポイントについては、master データベースの**cluster_endpoint_table**に対してクエリを実行します。

      接続のタイムアウトによって失敗した場合は、それぞれのノードにファイアウォールが設定されている可能性があります。 この場合、Kubernetes クラスター管理者に連絡して、外部に公開されているノード IP を要求する必要があります。 任意のノードを指定できます。 その後、その IP と対応するポートを使用して、クラスターで実行されているさまざまなサービスに接続できます。 たとえば、管理者は次を実行してこの IP を見つけることができます。

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="azdatactp23"></a>azdata

- **Azdata**ツールは、動詞と名詞のコマンド順序から名詞動詞の順序に変更されました。 たとえば、 `azdata create cluster`はになり`azdata cluster create`ます。

- `--name` で`azdata cluster create`クラスターを作成するときに、パラメーターが必要になりました。

   ```bash
   azdata cluster create --name <cluster_name>
   ```

- ビッグデータクラスターと**azdata**の最新バージョンへのアップグレードに関する重要な情報については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

#### <a name="external-tables"></a>外部テーブル

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用する外部テーブルを Oracle に対して作成する場合、Azure Data Studio 仮想化ウィザードでは、これらの列は外部テーブル定義では VARCHAR として解釈されます。 これにより、外部テーブル DDL でエラーが発生します。 NVARCHAR2 型を使用するように Oracle スキーマを変更するか、外部テーブルステートメントを手動で作成して、ウィザードを使用せずに NVARCHAR を指定してください。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すと、呼び出しは5分でタイムアウトします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp22"></a>CTP 2.2 (2018 年12月)

以下のセクションでは、SQL Server 2019 CTP 2.2 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- クラスター管理ポータルにアクセス`/portal`するに **\<\>は、(https://: 30777/Portal**) を使用します。
- マスタープールのサービス名が`service-master-pool-lb`と`service-master-pool-nodeport`から`endpoint-master-pool`に変更されました。
- 新しいバージョンの**azdata**および更新されたイメージ。
- その他のバグの修正と改善。

### <a name="known-issues"></a>既知の問題

以下のセクションでは、このリリースの既知の問題と制限事項について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。 最新のリリースをデプロイする前に、既存のビッグデータクラスターをバックアップして削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="cluster-administration-portal"></a>クラスターの管理ポータル

クラスター管理ポータルには、SQL Server マスターインスタンスのエンドポイントは表示されません。 マスターインスタンスの IP アドレスとポートを検索するには、次の**kubectl**コマンドを使用します。

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>外部テーブル

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp21"></a>CTP 2.1 (2018 年11月)

以下のセクションでは、SQL Server 2019 CTP 2.1 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- ビッグデータクラスターに[Python および R アプリをデプロイ](big-data-cluster-create-apps.md)します。
- 新しいバージョンの**azdata**および更新されたイメージ。 
- その他のバグの修正と改善。

### <a name="known-issues"></a>既知の問題

以下のセクションでは、CTP 2.1 の SQL Server ビッグデータクラスターに関する既知の問題について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグデータデータクラスターのアップグレードはサポートされていません。 最新のリリースをデプロイする前に、既存のビッグデータクラスターをバックアップして削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="admin-portal"></a>管理ポータル

- [Msqlctl-ctp コマンドを使用してアプリを作成](big-data-cluster-create-apps.md)し、それを SQL Server ビッグデータクラスターにデプロイすると、クラスター管理ポータルに、管理者の部分のコントローラーセクションで、アプリケーションが "不明" として展開されたポッドが表示されます。

#### <a name="external-tables"></a>外部テーブル

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a id="ctp20"></a>CTP 2.0 (2018 年10月)

以下のセクションでは、SQL Server 2019 CTP 2.0 のビッグデータクラスターの新機能と既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- Azdata management tool を使用した簡単なデプロイエクスペリエンス
- Azure Data Studio でのネイティブ notebook エクスペリエンス
- SQL Server のストレージインスタンスを使用して HDFS ファイルを照会する
- Master から SQL Server、Oracle、MongoDB、および HDFS を使用したデータの仮想化
- Azure Data Studio での SQL Server および Oracle 用のデータ仮想化ウィザード
- マスター上の ML サービス
- 監視とトラブルシューティングに使用できるクラスター管理ポータル
- Azure Data Studio での Spark ジョブの送信 
- クラスター管理ポータルの Spark UI
- ストレージクラスへのボリュームのマウント
- マスターからのデータプールに対するクエリ
- SSMS での分散クエリの計画を表示する
- Azdata management tool 用の Pip パッケージ
- コントローラーサービスを介した組み込みの展開エンジン

### <a name="known-issues"></a>既知の問題

以下のセクションでは、CTP 2.0 の SQL Server ビッグデータクラスターに関する既知の問題について説明します。

#### <a name="deployment"></a>展開

- Azure Kubernetes Service (AKS) を使用している場合、推奨されるバージョンの Kubernetes は 1.10. * で、ディスクのサイズ変更はサポートされていません。 デプロイ時にストレージのサイズを変更することを確認してください。 ストレージサイズを調整する方法の詳細については、[データの永続](concept-data-persistence.md)化に関する記事を参照してください。 Vm にデプロイされている Kubernetes の場合、推奨されるバージョンは1.11 です。

- AKS にデプロイすると、デプロイから次の2つの警告イベントが表示される場合があります。 これらのイベントはどちらも既知の問題ですが、AKS にビッグデータクラスターを正常にデプロイすることはできません。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグデータクラスターの展開が失敗した場合、関連付けられている名前空間は削除されません。 これにより、クラスターで孤立した名前空間が発生する可能性があります。 回避策としては、名前空間を手動で削除してから、同じ名前のクラスターを展開します。

#### <a name="external-tables"></a>外部テーブル

- サポートされていない列の型を持つテーブルに対して、データプールの外部テーブルを作成することができます。 外部テーブルに対してクエリを実行すると、次のようなメッセージが表示されます。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルに対してクエリを実行した場合、基になるファイルが HDFS に同時にコピーされていると、エラーが発生することがあります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッドが再起動すると、Kubernetes 環境でポッド IP アドレスが変更される可能性があります。 マスターポッドが再起動するシナリオでは、Spark セッションがで`NoRoteToHostException`失敗する場合があります。 これは、新しい IP アドレスで更新されない JVM キャッシュによって発生します。

- Jupyter が既にインストールされており、別の Python が Windows にインストールされている場合、Spark notebook は失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook では、 **[テキストの追加]** コマンドをクリックすると、テキストセルは編集モードではなくプレビューモードで追加されます。 プレビューアイコンをクリックして編集モードに切り替え、セルを編集することができます。

#### <a name="hdfs"></a>HDFS

- HDFS 内のファイルを右クリックしてプレビューすると、次のエラーが表示される場合があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点では、Azure Data Studio で 30 MB を超えるファイルをプレビューする方法はありません。

- Hdfs-site.xml の変更を伴う HDFS に対する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は環境の一部であり、(たとえば、コードダンプファイルで) 検出可能です。 デプロイ後に master インスタンスの SA_PASSWORD をリセットする必要があります。 これはバグではなく、セキュリティ手順です。 Linux コンテナーの SA_PASSWORD を変更する方法の詳細については、「 [SA パスワードを変更](../linux/quickstart-install-connect-docker.md#sapassword)する」を参照してください。

- AKS ログには、ビッグデータクラスターデプロイの SA パスワードを含めることができます。

## <a name="next-steps"></a>次のステップ

ビッグデータクラスター SQL Server の詳細については、「 [SQL Server 2019 ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
