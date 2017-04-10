---
title: "SQL Server のエディション間で R の機能の相違点 | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# SQL Server のエディション間で R の機能の相違点
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 次のエディションで利用可能な [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:  
  
-   **Enterprise Edition**  
    
     Windows では、さまざまなデータベースおよび一度に、分析のためのデータをプルへの接続に使用できるが、これはデータベースでは実行されません R サーバー (スタンドアロン) と同様に SQL Server 2016 でデータベースの分析用の両方の R サービスが含まれます。 含まれています **DeployR**, 、これは、Web サービスとしての R スクリプトとモデルの展開を使用できます。  

     制限はありません。 最適なパフォーマンスとスケーラビリティを並行化とストリーミングします。 使用して利用可能なメモリに適合しない大規模なデータセットの Suopprts 分析、 **スケーラ** 関数です。  
  
     SQL server データベースの分析では、サーバー リソース使用率をカスタマイズするスクリプトを外部のリソース管理をサポートします。  
  
-   **Developer Edition**  

    Enterprise Edition と同じ機能ただし、Developer Edition は、実稼働環境では使用できません。  

  
  
-   **Standard Edition**  
  
     データベースの分析のすべての機能に含まれている Enterprise Edition、柔軟なリソースのガバナンスを除く。 パフォーマンスとスケールは制限されます。 サーバー メモリに収まるように処理できるデータがあり、使用する場合でも、処理は単一の計算のスレッドに制限されて、 **スケーラ** 関数です。
  
-   **Express Edition**  
  
     のみ Express Edition with Advanced Services では、R のサービスを提供します。 パフォーマンスの制限は、Standard Edition に似ています。  
  
 その他の製品の機能の詳細については、次を参照してください [エディションの SQL Server 2016 でサポートされる機能。](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  

> [!NOTE]
>
> + Microsoft R Open は、すべてのエディションに付属します。
> + Microsoft R クライアントは、すべてのエディションを操作できます。
  
## Enterprise Edition  
 R ソリューションのパフォーマンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一般に、従来の R 実装、R は、サーバー リソースを使用して実行できるため、同じハードウェアを指定しを使用して複数のプロセスに配布場合もありますよりできると予想される、 **スケーラ** 関数です。  
  
 Vs の Enterprise Edition で実行する場合は、同じ R 関数のパフォーマンスとスケーラビリティにかなりの相違も期待できます。標準エディションです。 上の理由からには、並列処理、ストリーム、および R ワーカーの処理で使用できる増加のスレッドのサポートが含まれます。  
  
 サーバー リソースに対する競合する要求、作成されるクエリ プランの種類、スキーマの変更など、R コードの外部の多くの要因によって同一のハードウェアであってもパフォーマンスに影響することができます、統計を更新または新しいクエリ プランの作成、断片化を解消する必要があります。 R コードを含む可能性があります (秒) 1 つの作業負荷の下で動作しますが、かかるストアド プロシージャが分場合に可能であれば他のサービスが実行されています。  そのため、サーバーのパフォーマンス、R のジョブのパフォーマンスを定量化するときにネットワークのリモート コンピューティングのコンテキストを含むのさまざまな側面を監視することをお勧めします。  

構成することもお勧め [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md) (Enterprise Edition で使用可能) R のジョブは優先順位付け内またはサーバーに高い負荷を処理する方法をカスタマイズします。 R のジョブのソースを指定し、特定のワークロードを優先度付け、SQL クエリで使用されるメモリの量を制限する分類子関数を定義し、ワークロードごとに使用される並列処理の数を制御できます。  
  
## Developer Edition  
 開発者エディションは、Enterprise Edition と同等のパフォーマンスを提供します。ただし、Developer Edition の使用は、運用環境ではサポートされません。  
  
  
## Standard Edition  
 Standard Edition では、標準的な R パッケージ、同じハードウェア構成を指定すると比較して、パフォーマンスが向上を提供する必要があります。  
  
 ただし、Standard Edition はリソース ガバナーをサポートしていません。 モデルのトレーニングとスコア付けなどのさまざまな R ワークロードをサポートするサーバーのリソースをカスタマイズする最善の方法は、リソース管理を使用します。  
  
 Standard Edition では、パフォーマンスの低下と Enterprise edition および Developer Edition と比較してスケーラビリティも提供します。 具体的には、すべての **スケーラ** 関数とパッケージが Standard Edition に付属が R スクリプトの管理を起動するサービスは、使用できるプロセスの数に制限されます。 さらに、スクリプトで処理されるデータは、メモリに収まる必要があります。  
  
  
## Express Edition with Advanced Services  
 Express Edition は、Standard Edition と同じ制限が適用されます。  
  
## 参照  
 [SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
  