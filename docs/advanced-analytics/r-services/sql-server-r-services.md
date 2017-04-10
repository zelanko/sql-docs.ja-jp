---
title: "SQL Server R サービス | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 36
---
# SQL Server R サービス
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、新たな洞察を得るためのインテリジェント アプリケーションを開発し、展開するためのプラットフォームが提供されます。 豊富で強力な R 言語とコミュニティのさまざまなパッケージを使用してモデルを作成し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使用して予測を生成することができます。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では R 言語と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が統合されるため、データの近くで分析を行い、データ移動に関するコストとセキュリティ上のリスクを削減できます。  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] は、オープン ソース R 言語と、パフォーマンス、セキュリティ、信頼性に優れ、管理が簡単な一連の包括的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ツールとテクノロジをサポートします。 便利で使い慣れたツールを使用して R ソリューションをデプロイでき、実稼働アプリケーションで R ランタイムを呼び出し、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して予測および視覚効果を得ることができます。 [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler) ライブラリを入手し、R ソリューションのスケールとパフォーマンスを上げることもできます。  
  
SQL Server セットアップにより、サーバー コンポーネントとクライアント コンポーネントの両方をインストールできます。  
  
+   **R サービス (データベース内):** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にこの機能をインストールし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターで R スループットを安全に実行できるようにします。  
  
     この機能を選択すると、拡張機能がデータベース エンジンにインストールされ、R スクリプトの実行がサポートされます。また、新しいサービスの [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] が作成され、R ランタイムと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス間のすべての通信が管理されます。  
  
+   **Microsoft R サーバー (スタンドアロン):** オープン ソース R のディストリビューション。並列処理に対応し、その他のパフォーマンスが改善された独自のパッケージと組み合わされます。 R Services (データベース内) と Microsoft R サーバー (スタンドアロン) のいずれにもベース R ランタイム/パッケージと **ScaleR** ライブラリが含まれ、接続性とパフォーマンスが強化されています。 
  
+    [Microsoft R クライアント](https://msdn.microsoft.com/microsoft-r/index#mrc)は別個の無料インストーラーとして利用できます。  Microsoft R クライアントを利用し、SQL Server で実行されている R Services に、あるいは Windows、Teradata、Hadoop で実行されている Microsoft R サーバーに展開できるソリューションを開発できます。 
     

  > [!NOTE] R コードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行する必要がある場合は、[ここ](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)の説明に従って [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールしてください。
  >  
  > Microsoft R サーバー \(スタンドアロン\) は、SQL Server を実行していない Windows コンピューターで Scale R ライブラリを使用するために設計された別個のオプションです。 
>   
>  ただし、Enterprise Edition をご利用の場合、R の開発に使うラップトップまたは他のコンピューターに Microsoft R サーバー \(スタンドアロン\) をインストールし、R Services \(データベース内\) を実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに簡単に展開できる R ソリューションを作成することが推奨されます。
  
## <a name="additional-resources"></a>その他のリソース  
  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 SQL Server で R を使用する一般的なシナリオについて説明します。  
  
[SQL Server R Services (データベース内) をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
SQL Server セットアップの一環として R と関連データベース コンポーネントをインストールします。  
  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
R コードで SQL Server データ ソースを作成する方法とリモート コンピューティング コンテキストを使用する方法について説明します。 SQL 開発者を対象としているその他のチュートリアルでは、SQL Server で R モデルをトレーニングし、展開する方法について説明します。  
  
## <a name="see-also"></a>参照  
  
 [Microsoft R Server の概要 &#40;スタンドアロン&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
 
 [スタンドアロン R サーバーのセットアップ](../../advanced-analytics/r-services/create-a-standalone-r-server.md) 
  