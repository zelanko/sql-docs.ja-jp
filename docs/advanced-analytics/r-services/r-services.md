---
title: "R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# R Services
  Microsoft R Services では、よく使われるオープン ソース R 言語とビジネス アプリケーションを統合するための 2 つのサーバー プラットフォームが提供されます。1 つは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との統合用の **SQL Server R Services (データベース内)**、もう 1 つは **Microsoft R Server** です。  
  
-   **R Services (データベース内)**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の目的は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プラットフォームとそれに関連するサービスに基づいて、R ソリューションを迅速に開発し、使用できるようにすることです。  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、R をデータベースと同じコンピューターで実行できるようにして、データにコンピューティングを適用します。 これには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの外部で実行され、R ランタイムと安全に通信を行うデータベース サービスが含まれます。 R モデルをトレーニングし、R プロットを生成し、スコア付けして、R と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 間でデータを簡単に移動することができます。 ソリューションのテストと開発を行っているデータ サイエンティストは、リモート開発コンピューターからサーバーと通信し、サーバーに対して R コードを実行して、ストアド プロシージャに R への呼び出しを埋め込むことで SQL Server に完成したソリューションをデプロイできます。  
  
     このダウンロードには、オープン ソース R 言語のディストリビューションと、ScaleR (高パフォーマンスでスケーラブルな一連の R パッケージ) が含まれます。 また、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テクノロジを利用してより簡単にすばやく接続するためのプロバイダーも含まれます。  
  
     詳細については、「 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)」を参照してください。 シナリオ例については、「[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)」を参照してください。  
  
-   **Microsoft R Server**  
  
     このスタンドアロン サーバー システムでは、複数のプラットフォームでの、Linux、Hadoop、Teradata などの複数のエンタープライズ データ ソースを使用する分散型スケーラブル R ソリューションがサポートされます。  
  
     詳細については、「 [Microsoft R Server (MSDN)](https://msdn.microsoft.com/microsoft-r/index)」を参照してください。  
  
## <a name="related-technologies"></a>関連技術情報  
 Microsoft ではオープン ソース R 言語エコシステムを幅広くサポートします。これには、ツール、プロバイダー、拡張 R パッケージ、および統合開発環境が含まれます。  
  
-   **R Tools for Visual Studio**  
  
     Visual Studio では、R 言語用の完全な開発環境が提供されます。 プラグインには、エディター、対話型のウィンドウ、プロット、デバッガーなどが含まれます。 R から .NET 言語を使用したり、R.NET や rClr などのオープン ソース ライブラリを介して .NET から R を呼び出したりすることができます。  
  
     詳細については、「[R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)」を参照してください。  
  
-   **Azure Machine Learning における R**  
  
     プリロードされている 400 を超える R パッケージにアクセス可能な、Azure Machine Learning Studio で独自のワークスペースを作成します。 モデルを構築し、トレーニングを行い、Web サービスとしてデプロイしたり、カスタム スクリプトを記述してデータを転送したりします。 独自の R パッケージを作成し、Azure にアップロードしてカスタム モジュールとして実行し、ソリューションを [Machine Learning Marketplace](http://datamarket.azure.com/browse/data?category=machine-learning)にパブリッシュします。  
  
     詳細については、「[R を使用した実験の拡張](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r)」および「[Azure Machine Learning でカスタム R モジュールを作成する](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules)」を参照してください。  
  
-   **データ サイエンス仮想マシン**  
  
     Microsoft Azure でプレインストールと構成済みバージョンの [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] をデプロイできます。これにより、オンプレミスの完全に構成されたシステムをセットアップすることなく、データ探索の開始やクラウドでの即時モデリングが容易になります。  
  
     Azure Marketplace には、データ サイエンスをサポートする次のようないくつかの仮想マシンが含まれています。
     + **Microsoft データ サイエンス仮想マシン**には、Microsoft R Server、Python (Anaconda ディストリビューション)、Jupyter ノートブック サーバー、Visual Studio Community エディション、Power BI Desktop、Azure SDK、および SQL Server Express Edition が構成されています。 
     + **Microsoft R Server 2016 for Linux** には、最新バージョンの R Server (バージョン 9.0.1) が含まれています。 CentOS バージョン 7.2 および Ubuntu バージョン 16.04 では別の VM を使用できます。 
     + **R Server Only SQL Server 2016 Enterprise** 仮想マシンには、新しい Modern Software Lifecycle ライセンス モデルをサポートする R Server 9.0.1 用のスタンドアロン インストーラーが含まれています。
 

## <a name="see-also"></a>参照  
[SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md) 

[Microsoft R Server の概要](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  

 [SQL Server データベース エンジンのインストール](../../database-engine/install-windows/install-sql-server-database-engine.md)  
  
  