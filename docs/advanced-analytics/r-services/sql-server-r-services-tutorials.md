---
title: "SQL Server R Services のチュートリアル | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 31
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# SQL Server R Services のチュートリアル
ここで紹介するチュートリアルでは、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] と、そのサポートする次のようなデータ サイエンスのシナリオを学習できます。

+ R でのモデルの開発と SQL Server への展開
+ データ科学者が開発した R ソリューションをサーバーまたはその他の実稼働環境に展開する R コードの運用
+ R と SQL Server 間のデータの移動
+ リモートおよびローカルの計算コンテキストを使用する方法
  

## <a name="a-namebkmkend-to-endadeveloping-an-end-to-end-advanced-analytics-solution"></a><a name="bkmk_end-to-end"></a>エンド ツー エンドの高度な分析ソリューションの開発  

[データ サイエンスのエンド ツー エンド チュートリアル](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md) 

データの取得から分析、スコアリングまで、データ サイエンス プロセス全体を経験できます。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータを使用する方法と、モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に保存して運用する方法について説明します。  
PowerShell を使用してニューヨーク市のタクシーのデータ セットを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にインポートし、R を使用してデータを探索します。 

次に、予測モデルを構築し、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に展開して、両方のモデルと単一予測モデルでスコア付けします。 

  
このチュートリアルは、R と、PowerShell や SQL Server Management Studio などの開発者ツールをある程度理解している方を対象としています。 R 開発環境にアクセス可能で、R コマンドを理解している必要があります。 
  
## <a name="a-namebkmkdatascienceadata-science-deep-dive"></a><a name="bkmk_dataScience"></a>データ サイエンスの詳細情報  

[RevoScaleR と SQL Server の概要](http://go.microsoft.com/fwlink/?LinkID=691640&clcid=0x809)  

このチュートリアルは、R 言語を理解しているデータ科学者や開発者、Revolution Analytics が強化した R のパッケージや Microsoft R の関数について学習したい方に最適です。 

ScaleR パッケージの関数を利用し、R と SQL の間でデータを移動する方法と特定のタスクに合わせて計算コンテキストを切り替える方法について学習します。 モデルとプロットを作成し、開発環境と SQL Server の間で移行します。  
  
このチュートリアルは、既に R を使用しており、RevoScaleR と SQL Server で R の機能を改善する方法について理解を深めたい方を対象としています。

## <a name="in-database-advanced-analytics-for-the-sql-developer"></a>SQL 開発者向けの高度な分析 (データベース内)  
  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)

このチュートリアルでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] を利用し、高度な分析ソリューションを完全に構築し、展開します。 この例では、オープン ソースの R 言語を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンに統合する方法に焦点を当てています。 ストアド プロシージャに R コードをラップし、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存し、パラメーター化された呼び出しを R モデルに行い、予測を実行する方法について学習します。 
  
このチュートリアルは、R ソリューションをサポートし、R モデルを SQL Server に展開する方法を学習したい SQL 開発者、アプリケーション開発者、SQL DBA を対象としています。  R 環境は必要ありません。すべての R コードが用意されているので、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と使い慣れたビジネス インテリジェンス ツールと SQL 開発ツールを使用してソリューション全体を構築できます。   

## <a name="use-r-services-in-an-application"></a>アプリケーションで R Services を使用する

[SQL Server と R を使用してインテリジェンス アプリを構築する](https://www.microsoft.com/sql-server/developer-get-started/r)

このチュートリアルでは、スキー レンタル ビジネスで機械学習を使用して、今後のレンタルを予測する方法を学習します。これは、今後の需要にこたえるための事業計画と人員配置に役立ちます。


## <a name="using-r-code-in-t-sql"></a>T-SQL の R コードを利用する  

[SQL Server での R コードの使用 (SQL Server R Services)](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  

これは、[!INCLUDE[tsql](../../includes/tsql-md.md)] で R を利用するための基本的な構文が使われた短いスタンドアロンの例です。 

SQL から R ランタイムを呼び出す方法、R と SQL のデータ型の主な違い、SQL コードで R 関数をラップする方法、R 出力を SQL テーブルに保存するストアド プロシージャを実行する方法について説明します。
  
このチュートリアルは、R Services の初心者で、T-SQL を使用して R を呼び出す基本的な方法を学習したい方を対象としています。 R の経験は必要ありませんが、SQL Server Management Studio や、データベースに接続して単純な T-SQL クエリを実行できる他のツールの使い方を理解している必要があります。

  
## <a name="a-namebkmkprerequisitesaprerequisites"></a><a name="bkmk_Prerequisites"></a>前提条件
  
これらのいずれかのチュートリアルを実行するには、「[Set up SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」 (SQL Server R Services をセットアップする) の説明に従って **R Services (in-Database)** をダウンロードおよびインストールする必要があります。

SQL Server セットアップの実行後は、必ず次の手順を実行してください。
+ *sp_configure* を実行して R Services を有効にする
+ サーバーの再起動
+ R ランタイムを呼び出すサービスに必要なアクセス許可があることを確認する
+ R コードに使用する SQL ログインまたは Windows ユーザー アカウントに、サーバーとそのデータベースに接続するために必要なアクセス許可があることを確認する

問題が発生した場合、一般的な問題については、「[Upgrade and Installation of SQL Server R Services](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)」 (SQL Server R Services のアップグレードとインストール) を参照してください。

推奨される R 開発環境がまだない場合は、次のいずれかのツールをインストールして利用できます。

+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
+ [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)

これらのチュートリアルを利用する場合、標準の R ライブラリでは不十分です。R 開発環境と、R を実行する SQL Server コンピューターの両方に Microsoft の ScaleR パッケージがインストールされている必要があります。 Microsoft R の内容の詳細については、「[Microsoft R Products](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#compare-prods)」(Microsoft R 製品) を参照してください。

## <a name="additional-resources"></a>その他のリソース

これらのチュートリアルを完了したら、次のリンク先で、より高度なシナリオとサンプルを参照してください。
  
### <a name="end-to-end-solution-templates-for-key-machine-learning-tasks"></a>機械学習の主要タスク用のエンド ツー エンド ソリューション テンプレート  

[Machine Learning Templates with SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) (SQL Server 2016 R Services を使用した機械学習テンプレート)  

次の主な機械学習タスクに対応する機械学習ソリューションをすぐに使えるように、Microsoft 機械学習チームがカスタマイズ可能なテンプレートを用意しました。  
* 不正行為の検出  
* 顧客離れ予測  
* 予測メンテナンス  
  
すべての T-SQL と R コードが提供され、SQL Server ストアド プロシージャでスコア付けするためにモデルをトレーニングし、展開する方法を記した指示も付きます。 

### <a name="sample-data-and-sample-scripts"></a>サンプル データとサンプル スクリプト  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の製品サンプルは Microsoft ダウンロード センターから入手できます。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のサンプルのみを入手するには、zip ファイルを選択し、**Advanced Analytics** フォルダーを開きます。  一部の手順は以前のリリース向けですが、Benford の法則に基づく保険詐欺検出のデモや、非常に小さなデータセット (Iris データセット) を使った予測モデルで、デモにも利用できそうな単純なチュートリアルがあります。
  
[SQL Server 2016 製品サンプル](https://www.microsoft.com/en-us/download/details.aspx?id=49502)  
### <a name="learn-more-about-r"></a>R の詳細情報  
R の一般的な情報については、「 [R 言語リソース](http://revolutionanalytics.com/r-language-resources)」に優れたリソースがたくさん記載されているので参考にしてください。  
  
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]で提供される R パッケージの詳細については、「[Revolution Analytics サイト](http://go.microsoft.com/fwlink/?LinkId=691541)」を参照してください。  
  
このブログ投稿「 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Using R inside SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]」 (SQL Server 内で R を使用する) では、 [が提供する R のパッケージや関数を利用して](http://blog.revolutionanalytics.com/2015/10/previewing-using-revolution-r-enterprise-inside-sql-server.html)に接続するプロセスについて説明しています。また、サンプル コードが含まれています。  
  
## <a name="see-also"></a>参照  
[SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
[SQL Server R Services の機能とタスク](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
