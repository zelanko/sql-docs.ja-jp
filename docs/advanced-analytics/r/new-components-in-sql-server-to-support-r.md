---
title: "SQL Server で R をサポートするコンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54e9ef3f-1136-471e-865a-7cf013673186
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: c66936108d054c5ee4772769732c8543283af3f9
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="components-in-sql-server-to-support-r"></a>R をサポートする SQL Server のコンポーネント
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 および 2017 では、データベース エンジンには、外部のスクリプト言語では、R、Python などの機能拡張をサポートする省略可能なコンポーネントが含まれています。 SQL Server 2016; で、R 言語のサポートが追加されましたSQL Server 2017 Machine Learning サービスで追加された Python のサポートです。

このトピックでは、具体的には、R 言語で動作する新しいコンポーネントについて説明します。 これらのコンポーネントがオープン ソース R を扱う方法の詳細については、次を参照してください[R の相互運用性。](r-interoperability-in-sql-server.md)

## <a name="components-and-providers"></a>コンポーネントおよびプロバイダー

R を読み込み、アーキテクチャ概要に示された方法で R コードを実行するシェルに加え、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] には、次の追加コンポーネントが含まれています。

### <a name="launchpad"></a>スタート パッド 

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]によって提供されるサービスは、[!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)]フルテキスト インデックス作成とクエリ サービスが、フルテキスト クエリを処理するため、独立したホストを起動する場合と同様に、外部のスクリプトの実行をサポートするためです。

スタート パッド サービスは、Microsoft によって公開された信頼済みのランチャーか、パフォーマンスとリソース管理の要件を満たしているものとして Microsoft に認定されたランチャーでのみ起動します。 言語固有の起動ツールの名前を付けることは簡単です。

  + R -  RLauncher.dll
  + Python - PythonLauncher.dll

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、独自のユーザー アカウント下で実行されます。 特定の言語ランタイムに対応する各サテライト プロセスは、スタート パッドのユーザー アカウントを継承します。 構成と、スタート パッドのセキュリティ コンテキストに関する詳細については、次を参照してください。[セキュリティの概要](../../advanced-analytics/r/security-overview-sql-server-r.md)です。

### <a name="bxlserver-and-sql-satellite"></a>BxlServer と SQL サテライト

BxlServer 実行可能ファイル間の通信を管理する Microsoft によって提供されるは[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]R ランタイムとも RevoScaleR 関数を実装します。 BxlServer は、R セッションを含めるために使用される Windows ジョブ オブジェクトを作成し、各 R ジョブのセキュアな作業フォルダーをプロビジョンし、SQL サテライトを使用して R と [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] の間のデータ転送を管理しす。

事実上、BxlServer は R と対を成すものであり、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と連携して R と SQL Server の統合をサポートします。 BXL はバイナリ交換言語の略し、Microsoft R Client または Microsoft R Server のインストール時にも R. BxlServer.dll がインストールされているなど、SQL Server と外部プロセスの間でデータを効率的に移動するためのデータ形式を参照します。

SQL サテライトは、データベース エンジンによって提供される、SQL Server 2016 の新しい拡張性 API です。C や C++ を使用して実装された外部コードや外部ランタイムをサポートするためのものです。 BxlServer は、SQL サテライトを使用して [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と通信します。

SQL サテライトは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と外部スクリプト言語間の高速データ転送用に最適化された、カスタム データ形式を使用します。 SQL サテライトは型変換を実行し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と R 間の通信時に、入力と出力のデータセットのスキーマを定義します。

BxlServer は、次のタスクに SQL サテライトを使用します。

  + 入力データの読み取り
  + 出力データの書き込み
  + 入力引数の取得
  + 出力引数の書き込み
  + エラー処理
  + 標準出力とエラーに書き戻すクライアント

SQL サテライトは、拡張イベントを使用して監視できます。 詳しくは、「[Extended Events for SQL Server R Services](extended-events-for-sql-server-r-services.md)」(SQL Server R Services の拡張イベント) をご覧ください。

## <a name="communication-channels-between-components"></a>コンポーネント間の通信チャネル

+ **TCP/IP**

    既定では、間の内部通信[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]SQL サテライト TCP/IP を使用するとします。

+ **名前付きパイプ**

    BxlServer 間の内部のデータ転送と[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]SQL サテライト経由でパフォーマンスを強化するために独自の圧縮データ形式を使用します。 R メモリから BxlServer へのデータは、名前付きパイプを経由して、BXL 形式で交換されます。

+ **ODBC**

    外部データ サイエンス クライアント間の通信、および[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスは、ODBC を使用します。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] に R ジョブを送信するアカウントには、インスタンスへの接続権限と、外部スクリプトの実行権限の両方が付与されている必要があります。 さらに、アカウントには、ジョブによって使用されるデータへのアクセス権限、データの書き込み権限 (たとえば、結果をテーブルに保存する場合な)、またはデータベース オブジェクトの作成権限 (たとえば、R 関数を新しいストアド プロシージャの一部として 保存する場合) が付与されている必要があります。

    [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] が、リモート クライアントから送信される R ジョブの計算コンテキストとして使用される場合、R コマンドは外部ソースからデータを取得する必要があります (ODBC は書き戻し用に使用されます)。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は、リモート R コマンドを発行しているユーザーの ID を、現在のインスタンス上のユーザーの ID にマップし、そのユーザーの資格情報を使用して ODBC コマンドを実行します。 この ODBC 呼び出しを実行するために必要な接続文字列は、クライアント コードから取得されます。

    追加の ODBC 呼び出しは、**RODBC** を使用してスクリプト内で実行できます。 RODBC は、リレーショナル データベースのデータにアクセスするために使用される、一般的な R パッケージです。ただし、パフォーマンスは [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] によって使用される同等のプロバイダよりも一般的に低速です。 多くの R スクリプトでは、分析に使用する "セカンダリ" データセットを取得するために、RODBC への埋め込み呼び出しが使用されます。 たとえば、モデルをトレーニングするストアド プロシージャでは、モデル トレーニング用のデータを取得するために SQL クエリが定義される場合もありますが、追加要素を取得したり、検索を実行したり、テキスト ファイルや Excel などの外部ソースから新しいデータを取得する場合には、埋め込みの RODBC 呼び出しが使用されます。

    次のコードは、R スクリプトに埋め込まれた RODBC 呼び出しを示したものです。

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **その他のプロトコル**

    「チャンク」で動作するか、リモート クライアントにデータを転送する必要がありますを使用することも、します。Microsoft r です。 実際のデータ転送でサポートされている XDF 形式は、エンコードされた blob を通じてです。

## <a name="interaction-of-components"></a>コンポーネントの相互作用

ここで説明したコンポーネント アーキテクチャは、オープン ソースの R コードを想定どおりに動作させると共に、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターで実行されるコードのパフォーマンスを大幅に向上させる目的で提供されています。 コンポーネントが R ランタイムや [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データベース エンジンとやり取りするメカニズムは、R コードの起動方法によって若干異なります。 このセクションでは、主なシナリオについてまとめます。

### <a name="r-scripts-executed-from-sql-server-in-database"></a>SQL Server データベースから実行された R スクリプト

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] "内部" から実行される R コードは、ストアド プロシージャを呼び出して実行されます。 したがって、R コードの実行は、ストアド プロシージャを呼び出す任意のアプリケーションによって開始できます。  その後、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は次の図に示す方法で、R コードの実行を管理します。

![rsql_indb780-01](media/script_in-db-r.png)

1. ストアド プロシージャ ([sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)) に渡されたパラメーター _@language='R'_ によって、R ランタイムに対する要求が示されます。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] が、この要求をスタート パッド サービスに送信します。
2. スタート パッド サービスが適切なランチャーを起動します (この場合は RLauncher)。
3. RLauncher が外部の R プロセスを起動します。
4. BxlServer が R ランタイムと連携して、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] とのデータ交換や、作業結果の保存を管理します。
5. SQL サテライト関連のタスクについての通信を管理および処理し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。
6. BxlServer が SQL サテライトを使用して状態を通信し、結果を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] に送信します。
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 結果を取得し、関連するタスクとプロセスを終了します。

### <a name="r-scripts-executed-from-a-remote-client"></a>リモート クライアントから実行された R スクリプト

コンテキストで R 関数を実行するには接続時に Microsoft R をサポートするリモート データ サイエンス クライアントから、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] RevoScaleR 関数を使用しています。 これは、上記のワークフローとは異なるものです。次の図に概要を示します。

![rsql_fromR2db-01](media/remote-sqlcc-from-r2.png)

1. RevoScaleR 関数では、R ランタイムは、BxlServer を呼び出してリンク関数を呼び出します。
2. BxlServer は Microsoft R と共に提供されているもので、R ランタイムとは別個のプロセスで実行されます。
3. BxlServer は接続のターゲットを決定し、ODBC を使用して接続を開始して、R データ ソース オブジェクト内の接続文字列の一部として提供された資格情報を渡します。
4. BxlServer が [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスへの接続を開きます。
5. R 呼び出し、サービスが呼び出されると、スタート パッドは有効にすると、適切なランチャー RLauncher が起動します。 その後の R コードの処理は、T-SQL から R コードを実行する場合のプロセスと同様です。
6. RLauncher が、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターにインストールされている R ランタイムのインスタンスへの呼び出しを行います。
7. 結果が BxlServer に返されます。
8. SQL サテライトは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] との通信と、関連するジョブ オブジェクトのクリーンアップを管理します。
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 結果をクライアントに渡します。

## <a name="next-steps"></a>次の手順

[アーキテクチャの概要](architecture-overview-sql-server-r.md)

[セキュリティの概要](security-overview-sql-server-r.md)

[セキュリティに関する考慮事項](security-considerations-for-the-r-runtime-in-sql-server.md)
