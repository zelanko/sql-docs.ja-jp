---
title: "Microsoft R Server の概要 (スタンドアロン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 16
---
# Microsoft R Server の概要 (スタンドアロン)
  Microsoft R Server (スタンドアロン) を使用すると、一般的なオープン ソースの R 言語を利用して、高パフォーマンスの分析ソリューションを作成したり、他のビジネス アプリケーションと統合したりできます。  
  
## Microsoft R Server とは  
 Microsoft R Server (スタンドアロン) には Revolution Analytics によって開発された拡張 R パッケージが含まれており、Hadoop や Teradata などのさまざまなデータ ソースへの接続がサポートされます。 スタンドアロン サーバーをインストールすることにより、複雑で拡張性の高い R ジョブを実行するためのサーバー環境を作成できます。  
  
## Microsoft R サーバー (スタンドアロン) を使用する利点  
 R は統計的計算、機械学習、グラフィックスのための世界有数の強力なプログラミング言語であり、ユーザー、開発者、および作成協力者の活発な世界的コミュニティによってサポートされています。 従来、エンタープライズ設定で R を使用する際には、特にデータの量が増加する場合や、実稼働環境にソリューションを展開する必要がある場合に、特定の課題が発生しています。 Microsoft R Server は、R コードの配置と操作運用の問題を解決します。  
  
 Microsoft R サーバーは、任意の Windows コンピューターにインストールすることができには、すべての R パッケージや接続ツールをリモート コンピューティングのコンテキストを有効にすると、拡張性の高い、並列のソリューションをサポートします。  
  
 Microsoft R サーバー (スタンドアロン) には、これらのシナリオがサポートされています。  
  
-   **中央サーバーを使用して R ソリューションを運用可能にする**  
  
     スタンドアロン サーバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に依存することなく高い R パフォーマンスを提供します。 リソースを制限するラップトップ コンピューターや開発コンピューターではなくサーバーでは、複雑なことやリソースを消費する計算を実行できます。  
  
     ジョブを集中管理することも、R の 1 つの接続ポイントとして R Server プロットであると、予測は、レポートで使用されるため、運用環境での予測モデルをスコア付けまたは使用する必要がある場合などです。 
     
     また、頻繁に SQL Server のコンテキストの外部の R を実行する必要がある場合、SQL Server コンピューターに R サーバー (スタンドアロン) をインストールすることをお勧めします。
  
-   **強力なデータ探索および予測モデリングを可能にする**  
  
     データ サイエンティストは、任意のクライアント ワークステーションと任意の R 開発ツールを使用して、R ソリューションをビルドできます。 ソリューションが RevoScaleR パッケージ API を使用している場合、一般にはるかに高い処理能力と多くのメモリを備えたサーバーで、計算を実行できます。 それにより、ソリューションでは、はるかに大きなデータセットを処理し、マルチスレッド、マルチコア、マルチプロセスの計算を利用できます。  
  
## 入手方法  
 インストール手順については、「 [Create a Standalone R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md)」を参照してください。 使用してすべてのコンポーネントをインストールできる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップします。  
  
## その他の R のツールをインストールします。  
 推奨される R 開発環境を取得していない場合は、多くのオプションです。 詳細については、「 [セットアップまたは R ツールの構成](../../advanced-analytics/r-services/setup-or-configure-r-tools.md)します。 
 
 を Microsoft R サーバーやデータ科学ワークステーションから SQL Server の R のサービスを接続することをお勧め無料 [Microsoft R クライアント](http://aka.ms/rclient/download) (ダウンロード) します。  
  
## Microsoft R サーバー (スタンドアロン) で R スクリプトを実行します。  
 サーバー コンポーネントを設定し、ご愛用の IDE の R をインストールした後に RevoScaleR パッケージを使用して、ソリューションの開発を開始します。 これらの API を使用すると、R コマンドをリモート サーバーに送信して実行できます。  
  
-   [スケーラ](https://msdn.microsoft.com/microsoft-r/scaler-getting-started): このコレクションの高パフォーマンスを提供する再頒布可能の分析機能を活用し、R ソリューションにスケーリングして開始します。 K 平均法クラスタ リング、デシジョン ツリー、デシジョン フォレスト、およびデータを操作するためのツールなど、パッケージのモデルを作成する最も一般的な R の多くの並列バージョンが含まれます。 並列アルゴリズムを作成するのに HPC を使用することもできます。  
    
-   [DeployR](https://msdn.microsoft.com/microsoft-r/deployr-about): この省略可能なフレームワークには、Java、JavaScript または .Net を使って、サード パーティ製のパッケージで出力する R 分析統合 R プログラマのためのツールが用意されています。  

さまざまな SAS、SPSS、Hadoop、およびテキスト ファイルなどの形式でデータを使用することができます。 インプレースでデータを分析したり、.xdf ファイル形式を使用して、ローカル R 開発環境にデータを効率的に移動できます。  
  
R のサーバーで開始するには、MSDN ライブラリでは、このガイドを参照してください: [R Server - 作業の開始](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started)  
  
 スケーラ パッケージを使用する方法については、次を参照してください [25 関数での R のチュートリアル。](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#an-r-tutorial-in-25-functions-or-so)  
  
## 参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  