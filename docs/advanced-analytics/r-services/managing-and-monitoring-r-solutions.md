---
title: "R ソリューションの管理と監視 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# R ソリューションの管理と監視
  データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 データベース管理者は、運用とレポート用のデータ ストアの正常性を維持しながら、データ サイエンティストに対してだけでなく、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにデータのアクセス権を与える必要があります。 企業において、DBAは、データ サイエンス用の効率的なインフラストラクチャのビルドと展開のきわめて重要な部分です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] データ サイエンスの役割をサポートするデータベース管理者が、多くの利点を提供します。  
  
-   **セキュリティ。** アーキテクチャ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] セキュリティで保護されたデータベースを保持およびデータベース インスタンスの操作から R セッションの実行を分離します。  
  
     R スクリプトを実行するアクセス許可を持つユーザーを指定し、R ジョブで使用されるデータが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に定義されている同じセキュリティ ロールを使用して管理されるようにします。  
  
-   **信頼性。** R セッションで問題が発生した場合でも、サーバーが通常どおりに実行し続けるように、R セッションは個別のプロセスで実行されます。 特権の低い物理ユーザー アカウントは、含み R インスタンスの特定に使用されます。   
  
-   **リソース管理。** R ランタイムに割り当てられるリソースの量を制御し、大規模な計算によりサーバーの全体的なパフォーマンスが損なわれないようにすることができます。  
  
  
## このセクションの内容  
 [R のサービスの監視](../../advanced-analytics/r-services/monitoring-r-services.md)
 
 [R のサービスのリソース管理](../../advanced-analytics/r-services/resource-governance-for-r-services.md)
 
[インストールして、R パッケージを管理します。](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)
  
[構成](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 

+ [高度な分析拡張機能の構成および管理](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)  
  
+  [SQL Server R サービスのユーザー アカウント プールを変更する](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  

 [SQL Server での R ランタイムのセキュリティに関する考慮事項](../../advanced-analytics/r-services/security-considerations-for-the-r-runtime-in-sql-server.md)  
  
 
  
## 参照  
 [SQL Server R Services の機能とタスク](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
  