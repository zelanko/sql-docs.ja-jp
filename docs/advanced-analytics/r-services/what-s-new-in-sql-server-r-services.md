---
title: "SQL Server R Services の新機能 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 35
---
# SQL Server R Services の新機能
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および SQL Server vNext の機能であり、エンタープライズ規模のデータ サイエンスをサポートします。  R は高度な分析ができる最も人気のあるプログラミング言語であり、非常に豊富なパッケージ セットと急成長中の活気のある開発者コミュニティを提供します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を利用すれば、人気の高いオープン ソースの R 言語をビジネスで活用できます。 
  
 > [!TIP] SQL Server 2016 R Services を既にお持ちですか?
 > Microsoft R Server の最新バージョンを 2016 インスタンスにインストールして、頻繁に更新される R コンポーネントを利用できるようになりました。 詳細については、[Microsoft R Server 9.0.1](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) に関する記事を参照してください。  

## <a name="whats-new-in-sql-server-vnext"></a>SQL Server vNext の新機能
  
+ **MicrosoftML** パッケージの概要

   MicrosoftML は、Microsoft R Server チームと Microsoft データ サイエンス チームによって提供される R 用の新しい機械学習パッケージです。 MicrosoftML を使用すると、速度、パフォーマンス、およびスケールが向上し、数行のコードだけで、テキスト データの大規模なコーパスおよび高次元のカテゴリ データを R モデルで処理することができます。 さらに、Microsoft R Server のお客様には、Azure Machine Learning に含まれる高速でとても精度が高い&5; つの学習ツールへのアクセス権限が付与されます。 
   
   詳細については、[「SQL Server R Services の MicrosoftML パッケージを使用する」](../../advanced-analytics/r-services/using-the-microsoftml-package-with-sql-server-r-services.md) を参照してください。
   
+ データ サイエンティスト向けの簡単なパッケージ管理

  SQL Server で必要な R パッケージをインストールする場合に、データベース管理者に頼らずに済むようになります。 **RevoScaleR** の新規パッケージのインストールおよびアンインストール機能を使用すると、クライアント コンピューターから R Services のパッケージをインストールおよび更新することができます。 
  
  [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] には、パッケージに関連付けられたアクセス許可をインスタンス レベルとデータベース レベルの両方で管理するための、データベース管理者用の新しいロールが含まれています。 
  
  詳細については、[「R Package Management for SQL Server R Services」](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (SQL Server R Services の R パッケージ管理) を参照してください。 
     
+ R モデル オブジェクトの読み込みおよび書き込みを行うための、**RevoScaleR** の新しい関数

  RevoScaleR には、新しいシリアル化関数と、よりコンパクトなモデル ストレージの形式が追加されました。これにより、モデルのローディングと読み込みが高速になります。 
  
  詳細については、[「ODBC を使用して SQL Server に R オブジェクトを保存して読み込む」](../../advanced-analytics/r-services/save-and-load-r-objects-from-sql-server-using-odbc.md) を参照してください。 

+ SQL の統合を容易にする **sqlrutils** パッケージ

  この R パッケージでは、R コードの SQL ストアド プロシージャ呼び出しを容易に生成できます。 生成された SQL ストアド プロシージャは、SQL Server R Services で使用できます。 SQL ストアド プロシージャでパラメーター化できる関数に R コードを統合するのに役立つ例が提供されています。
  
  詳細については、[「sqlrutils パッケージを使用した R コード用の R ストアド プロシージャの生成」](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md) を参照してください。 
  

+ SSAS 接続を容易にする **olapR** パッケージ

   この新しいパッケージは、R および SQL Server Analysis ServicesR に対して新しい次元の接続を提供します。これにより、R での分析で OLAP データを使いやすくなります。既存の MDX クエリを実行して R データ フレームを取り戻したり、キューブ軸とスライサーを R コードで定義することで単純な MDX ステートメントを作成したりできます。 
   
   詳細については、[「R での OLAP キューブからのデータの使用」](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md) を参照してください。
   

  
## <a name="features-in-sql-server-2016-r-services-and-sql-server-vnext"></a>SQL Server 2016 R Services と SQL Server vNext の新機能  
  
- R での並行化可能な機械学習を実現する **RevoScaleR**。

-   SQL ログインと統合 Windows 認証の両方をサポート。  
    
-   大幅なパフォーマンスの向上。たとえば、R と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を接続する SQL Satellite プロセスの最適化、大量のデータ使用を可能にするデータ ページングのサポート、何十億もの行の高速処理を可能にするストリーミングなどが挙げられます。 
  
-   R プロセスで使用されるメモリを SQL Server リソース プールを使用して管理。 詳細については、[「CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;」](../../t-sql/statements/create-external-resource-pool-transact-sql.md) を参照してください。  
  

### <a name="tools-and-setup"></a>ツールとセットアップ

-   すべてのコンポーネントを簡単にセットアップできます。 SQL Server セットアップ ウィザードで、**SQL Server R Services (データベース内)** または **Microsoft R Server (スタンドアロン)** をインストールできます。   セットアップ ウィザードを実行するとき、SQL Server インスタンスを設定する場合は R Services を選択し、データ サイエンス ワークステーションをセットアップする場合は R Server (スタンドアロン) を選択します。   セットアップ オプションの詳細については、[「SQL Server R Services &#40;データベース内&#41; をセットアップする」](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md) または [「スタンドアロン R Server の作成」](../../advanced-analytics/r-services/create-a-standalone-r-server.md) を参照してください。  

-   SQL Server のデータを使用する必要がない場合は、[!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] を検討してください。これはさまざまなプラットフォーム上で実行され、一般的なオープン ソース R 言語にエンタープライズのスケールとパフォーマンスをもたらします。 [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)]。 詳細については、MSDN にある [「R Server &#40;スタンドアロン&#41;」](../../advanced-analytics/r-services/r-server-standalone.md) または [「Introducing R Server」](https://msdn.microsoft.com/microsoft-r/rserver) (R Server の概要) を参照してください。

- SQL Server 2016 インスタンスをアップグレードして Microsoft R Server 9.0.1 を使用するには、[SqlBindR.exe ユーティリティ](https://msdn.microsoft.com/library/mt791781.aspx) を使用します。  

- [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install) は、R Services または R Server で実行される R ソリューションを構築する上で必要なツールおよびライブラリがすべて含まれている無料の R 環境です。  

-   R Tools for Visual Studio は、R のサポートが充実している Visual Studio 用の無料プラグインです。たとえば、R の標準的な対話型の変数ウィンドウ、R 関数のインテリジェンス、デバッグ、R マークダウン (Word および HTML へのエクスポートで完了) などがサポートされています。  詳細については、「[R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。  

## <a name="learn-more"></a>詳細情報
  
-  SQL Server 統合に関する知識を必要としているデータ サイエンティストと、T-SQL と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の使い慣れた環境を使用して R ソリューションを作成したい SQL 開発者を対象にしたリソースが用意されています。 
   + [SQL Server R Services のチュートリアル](https://msdn.microsoft.com/library/mt591993.aspx)
   + [無料の電子ブック: SQL Server 2016 を使用したデータ サイエンス](https://mva.microsoft.com/ebooks/)
 
+ あらかじめ用意されているソリューションが必要な場合は、Microsoft データ サイエンス チームから提供されている[機械学習テンプレート](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/)を使用します。このテンプレートでは、予測メンテナンスやチャーン防止など、一般的な分析タスクのための実用的なソリューションが示されています。
 

  
## <a name="see-also"></a>参照  
[SQL Server vNext の新機能](../../sql-server/what-s-new-in-sql-server-vnext.md)
  