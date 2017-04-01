---
title: "R のサービスをサポートする SQL Server の新しいコンポーネント | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54e9ef3f-1136-471e-865a-7cf013673186
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# R のサービスをサポートする SQL Server の新しいコンポーネント

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] によって提供される新しいコンポーネントを含む、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、R 言語の機能拡張をサポートするデータベース エンジンです。 これらのコンポーネントのセキュリティ管理は [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] し、後で詳しく説明します。

## 新しい SQL Server コンポーネントとプロバイダー

R を読み込んで、アーキテクチャの概要」の説明に従って R コードを実行するシェルだけでなく [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] これらの追加コンポーネントが含まれています。

### **スタート パッド** 
   [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] によって提供される新しいサービスは、 [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] フルテキスト インデックス作成とクエリ サービスが、フルテキスト クエリを処理するための別のホストを起動するときと同様に、外部のスクリプトの実行をサポートするためです。 
  
  スタート パッド サービスは、Microsoft がパブリッシュされているかを microsoft でのパフォーマンスとリソース管理の要件を満たすとして認定されている信頼されたランチャーのみで開始されます。  [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)], 、R でサポートされる唯一の外部の言語では現在、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]です。
  
   [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービス独自のユーザー アカウントで実行します。 特定の言語ランタイムの場合は、各サテライト プロセスでは、スタート パッドのユーザー アカウントを継承します。 構成とスタート パッドのセキュリティ コンテキストに関する詳細については、次を参照してください。 [セキュリティの概要](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)します。

### **BxlServer と SQL サテライト**
  BxlServer は実行可能ファイル間の通信を管理している Microsoft 製 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R ランタイムともスケーラ関数を実装します。 R セッションで、R のジョブごとにセキュリティで保護された作業フォルダーを規定を格納するための R の間データ転送を管理する SQL サテライトを使用して Windows ジョブ オブジェクトを作成し、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。  

  BxlServer が連携する R に対応するには実際には、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] "R"SQL Server の統合をサポートします。 BXL するバイナリ Exchange 言語に対して、SQL Server と R. などの外部プロセス間でデータを効率的に移動するためのデータ形式を参照 

 SQL のサテライトは、外部コードまたは C または C++ を使用して実装される外部のランタイムをサポートするために、データベース エンジンによって提供される SQL Server 2016 で新しい拡張性 API です。 現在 R には、唯一サポートされているランタイムです。 BxlServer と通信するための SQL のサテライトを使用して [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。
 
  SQL サテライト間で高速なデータを転送用に最適化されたカスタム データ形式を使用して [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と外部のスクリプト言語です。 型変換を実行して間の通信中に入力と出力データセットのスキーマを定義 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R. と

  BxlServer は、これらのタスクの SQL のサテライトを使用します。 
  - 入力データの読み取り
  - 出力データの書き込み
  - 入力引数を取得します。
  - 書き込みの出力引数
  - エラー処理
  - STDOUT および STDERR に書き戻してクライアント

  SQL のサテライトは、拡張イベントを使用して監視できます。 詳細については、次を参照してください。 [SQL Server の R のサービスの拡張イベント](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md)です。


## コンポーネント間の通信チャネル

+ **TCP/IP** 既定では、間の内部通信 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL サテライト TCP/IP を使用するとします。

+ **名前付きパイプ**

  BxlServer 間の内部のデータ転送と [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] SQL 衛星を通じてパフォーマンスを向上させる財産的価値、圧縮されたデータ形式を使用します。 メモリからデータを R に BxlServer は BXL 形式で名前付きパイプ経由で交換されます。 
  
+ **ODBC** 外部データ サイエンスのクライアント間の通信、および [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスは、ODBC を使用します。 R を送信するアカウントのジョブを [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスに接続し、外部のスクリプトを実行するには、両方のアクセス許可を持つ必要があります。 さらに、アカウントは、(たとえば、テーブルに結果を保存する場合)、データを書き込むか、(たとえば、新しいストアド プロシージャの一部として R 関数を保存する) 場合は、データベース オブジェクトを作成、ジョブによって使用されるデータにアクセスする権限を持っている必要があります。

  ときに [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] が使用するように、R のジョブに対して計算コンテキストはリモート クライアントから送信され、R コマンドは、外部ソースからデータを取得する必要があります、ODBC が使用の書き戻し用です。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 現在のインスタンスでは、ユーザーの id をリモートの R コマンドを発行したユーザーの id をマップし、そのユーザーの資格情報を使用する ODBC コマンドを実行します。 この ODBC 呼び出しを実行するために必要な接続文字列は、クライアント コードから取得されます。
  
  その他の ODBC 呼び出し可能である、スクリプトの中を使用して **RODBC**します。 RODBC はリレーショナル データベースのデータにアクセスに使用される一般的な R パッケージです。ただし、パフォーマンスが得られるによって使用される比較可能なプロバイダよりも一般に低速 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。 多くの R スクリプトは、分析に使用できるデータセットを「セカンダリ」を取得する方法として RODBC に埋め込まれた呼び出しを使用します。 たとえば、モデルをトレーニングするストアド プロシージャは、モデルのトレーニング データを取得する SQL クエリの定義が、参照、またはテキスト ファイルや Excel などの外部ソースから新しいデータを取得するその他の要素を取得するには、埋め込みの RODBC 呼び出しを使用しています。

  次のコードは、R スクリプトに埋め込まれて RODBC 呼び出しを示しています。
   ~~~~
  library(RODBC);
  connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
  dbhandle <- odbcDriverConnect(connStr)
  OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
  ~~~~

+ **その他のプロトコル** "チャンク"単位で動作するか、リモート クライアントにデータを転送する必要があるプロセスが使用できるもします。Microsoft R. 実際のデータ転送のサポートおよび XDF 形式でエンコードされた blob です。

## コンポーネントの相互作用

ここで説明したコンポーネントのアーキテクチャが有姿」でオープン ソース R コードを操作できることを保証するために用意されてで実行されるコードのパフォーマンスの向上が大幅に提供することになる一方で、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューター。 コンポーネントと R ランタイムとやり取りするメカニズムと [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] データベース エンジンが R コードが起動した方法に応じて、多少異なります。 このセクションでは、主なシナリオをまとめたものです。 
 
### SQL Server (データベース) から実行された R スクリプト

""の中から実行される R コード [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] を呼び出してストアド プロシージャを実行します。 したがって、ストアド プロシージャを呼び出すと、任意のアプリケーションでは、R コードの実行を開始できます。  その後 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] の次の図に示すように、R コードの実行を管理します。

![rsql_indb780 01](../../advanced-analytics/r-services/media/rsql-indb780-01.png)

1. R の実行時の要求が、パラメーターで示される _@language = 'R'_ ストアド プロシージャに渡される [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] スタート パッド サービスには、この要求を送信します。
2. スタート パッド サービスは、適切なランチャー; を開始します。この場合は RLauncher です。
3. RLauncher では、外部の R プロセスを開始します。
4. 使用してデータの交換を管理する R ランタイムと BxlServer 座標 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] と作業結果のストレージです。
5. SQL サテライトが全体で、関連するタスクについての通信を管理しを処理し、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。
6. BxlServer SQL サテライトを使用して状態を通信し、結果を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]します。
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 結果を取得し、関連するタスクとプロセスを終了します。 


### リモート クライアントから実行された R スクリプト

コンテキストで R 関数を実行するには Microsoft R をサポートしているリモート データ サイエンス クライアントから接続するときに [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] スケーラ関数を使用しています。 これは、1 つ前からさまざまなワークフローであり、次の図に示します。


![rsql_fromR2db 01](../../advanced-analytics/r-services/media/rsql-fromr2db-01.png)

1. スケーラ関数の場合は、R のランタイムは、BxlServer を呼び出してリンク関数を呼び出します。 
2. BxlServer は Microsoft R と共に提供され、R のランタイムが別のプロセスで実行されています。
3. BxlServer では、接続のターゲットを決定し、R のデータ ソース オブジェクトで接続文字列の一部として提供された資格情報を渡して、ODBC を使用して接続を開始します。
4. BxlServer への接続を開き、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンス。
5. R 呼び出しサービスを起動すると、スタート パッドには有効にすると、適切なランチャー、RLauncher が起動します。 その後、R コードの処理は、T-SQL で R コードを実行するためのプロセスに似ています。
6. RLauncher にインストールされている R ランタイムのインスタンスへの呼び出しを行い、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューター。 
7. BxlServer には、結果が返されます。
8. SQL サテライトとの通信を管理する [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] および関連するジョブ オブジェクトのクリーンアップします。
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 結果をクライアントに渡します。

## 参照
[アーキテクチャの概要](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)
