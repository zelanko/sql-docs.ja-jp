---
title: "R コードの運用 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f15696b1-2479-4e5f-ac5e-4beaf958a043
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# R コードの運用
  データベース開発者は、企業全体で共有できるように、多数のテクノロジを統合し、結果をまとめる任務を負っています。 データベース開発者は、アプリケーション開発者、SQL 開発者、およびデータ サイエンティストと協力して、ソリューションを設計し、データの管理方法を推奨して、ソリューションを構築して展開します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] はデータ サイエンティストと協力する開発者に多くのメリットを提供します。  
  
-   **使用して、R スクリプトの対話 [!INCLUDE[tsql](../../includes/tsql-md.md)]します。** アプリケーションおよびデータベース開発者だけでなく、レポートを作成するアナリストは、システム ストアド プロシージャから、呼び出すことによって、R スクリプトを呼び出すことができます。  
  
     基本的な構文の詳細については、次を参照してください。 [sp_execute_external_script & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  [T-SQL で R コードを使用して](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)します。  
 
    ストアド プロシージャを使用して、コードの R は運用に対応する方法の詳細な例は、「 [SQL 開発者向けデータベースに Analytics](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)します。
  
     また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と統合することで、 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して R スクリプトを実行し、その結果をアプリケーションに埋め込むこともできます。 たとえば、R スクリプトを実行する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成し、そのレポートにプロットと予測を表示できます。  
  
-   **パフォーマンスとスケール。** によって RevoScaleR パッケージ Api が提供されるが、オープン ソース R 言語の制限がありますがわかっている [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 大規模なデータセットに対して機能し、マルチ スレッド、マルチコア、マルチ プロセスのデータベースで計算の恩恵をことができます。  
  
     R ソリューションで複雑な集計が使用されている場合、または大規模なデータセットが含まれる場合は、SQL の効率的なインメモリ集計と列ストア インデックスを利用して、R コードで統計の計算結果とスコア付けを処理できます。  
  
-   **標準の開発および管理ツール。** 管理や展開のための追加のツールが必要ありません。ストアド プロシージャを呼び出すことで、すべての R ジョブを呼び出すことができます。  
  
     さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データに対して実行したものと同じ R コードを、Hadoop などの他のデータ ソースに対して利用できます。  
  
 このセクションでは、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用して、R ソリューションを適切に変換し、運用環境に配置するために理解しておく必要がある概念について説明します。  
  
## このセクションの内容

[R データ型の処理](../../advanced-analytics/r-services/working-with-r-data-types.md)

[R のサービスで使用するための R コードに変換します。](../../advanced-analytics/r-services/converting-r-code-for-use-in-r-services.md)

##  <a name="bkmk_RelatedTasks"></a> 関連タスク  
  
[パフォーマンス チューニングの R の SQL Server のサービス](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
## 参照  
 [SQL Server R Services の機能とタスク](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)   
 [sp_execute_external_script & #40 です。Transact SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  
  