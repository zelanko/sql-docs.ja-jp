---
title: "SQL 開発者向けの高度な分析 (データベース内) (チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: c18cb249-2146-41b7-8821-3a20c5d7a690
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)
このチュートリアルの目標は、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用して高度な分析ソリューションを構築するための実践的な知識を SQL プログラマーに提供することにあります。 このチュートリアルでは、ストアド プロシージャに R コードをラップすることでアプリケーションまたは BI ソリューションに R を統合する方法について説明します。  
  
## 概要  
エンド ツー エンド ソリューションを構築するプロセスは、通常、データの取得とクリーニング、データ探索およびデータ機能のエンジニアリング、モデルのトレーニングおよびチューニング、実稼働環境へのモデルの展開によって構成されます。 実際の R コードの開発および試験は、RStudio や [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]の、R 用に構築された開発環境を使用して適切に実施されます。 ただし、ソリューションの作成後は、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の使い慣れた環境で [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを使用して、ソリューションを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に容易に展開することができます。  
  
したがって、このチュートリアルでは、ソリューションに必要な R コードがすべて与えられていることを前提としており、R でコード化済みの高度な分析ソリューションをビルドし展開することに重点を置いて説明します。  
  
-   [手順 1: サンプル データのダウンロード](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)。    サンプル データセットとサンプル SQL スクリプト ファイルをローカル コンピューターにダウンロードします。  
  
-   [手順 2: PowerShell を使用した SQL Server へのデータのインポート](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)。  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンス上でデータベースとテーブルを作成し、テーブルにサンプル データを読み込むための PowerShell スクリプトを実行します。  
  
-   [手順 3: データの探索と視覚化](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)。   R パッケージおよび関数を [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャから呼び出して、基本的なデータの探索および視覚化を実行します。  
  
-   [手順 4: T-SQL を使用してデータ機能を作成する](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)。  カスタム SQL 関数を使用して新しいデータ機能を作成します。  
  
-   [手順 5: T-SQL を使用してモデルをトレーニングし保存する](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md)  ストアド プロシージャを使用して機械学習モデルを構築し保存します。  
  
-   [手順 6: モデルを運用する](../../advanced-analytics/r-services/step-6-operationalize-the-model-in-database-advanced-analytics-tutorial.md)。  データベースにモデルが保存されたら、ストアド プロシージャを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] から予測モデルを呼び出します。  
  
> [!NOTE]  
> R コードの記述またはテストには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用しないことをお勧めします。 ストアド プロシージャに埋め込んだ R コードに問題がある場合、ストアド プロシージャから返される情報は、通常、エラーの原因を把握する上で十分なものではありません。   
>   
> デバッグでは、RStudio または [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)] などのツールを使用することをお勧めします。 このチュートリアルで示す R スクリプトは、従来の R ツールを使用して既に開発およびデバッグされています。  
>   
> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で実行可能な R スクリプトの開発方法の詳細については、チュートリアル [「Data Science End-to-End Walkthrough」](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)) (データ サイエンスのエンド ツー エンド チュートリアル) を参照してください。  
  
### Scenario  
このチュートリアルでは、よく知られている NYC タクシー データセットを使用します。 このパブリック データ セットには、20 GB の圧縮された CSV ファイル (未圧縮の状態で約 48 GB) が含まれています。これらのファイルの内容は、2013 年における 1 億 7300 万件を超える個々のタクシー乗車に関する詳細と、各乗車に対して支払われた料金の説明です。 このチュートリアルを簡単にするために、データの 1% (1,703,957 行と 23 列) を使用して代表的なサンプル データを作成しました。 このチュートリアルではこのデータを使用します。その上で、特定の乗車でチップをもらう見込みがあるかどうかを、時刻、距離、乗車場所などの列に基づいて予測する二項分類モデルを構築します。  
  
  
### 必要条件  
このチュートリアルは、データベースとテーブルの作成、テーブルへのデータのインポート、SQL クエリの作成など、基本的なデータベース操作に既に精通しているユーザーを対象としています。 すべての R コードが提供されるため、R の開発環境は必要ありません。 経験豊富な SQL プログラマーであれば、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用するか、提供されている PowerShell スクリプトを実行して、このチュートリアルを完了することができます。  
  
ただし、このチュートリアルを開始する前に、次の準備を完了しておく必要があります。  
  
-   SQL Server R Services を有効にした状態で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスのインスタンスに接続します (CTP 3 以降が必要)。 詳細については、インストールの手順 [「Set up SQL Server R Services (In-Database)」](https://msdn.microsoft.com/library/mt696069.aspx) (SQL Server R Services をセットアップする(データベース内) ) を参照してください。  
  
 -   このチュートリアルで使用するログインでは、データベースやその他のオブジェクトを作成し、データをアップロードし、データを選択し、ストアド プロシージャを実行するためのアクセス許可が付与されている必要があります。  
  
## 次の手順  
[手順 1: サンプル データのダウンロード](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## 参照  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
[SQL Server R サービス](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  
  
