---
title: "正常性ポリシーの構成 (SQL Server ユーティリティ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# 正常性ポリシーの構成 (SQL Server ユーティリティ)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスおよびデータ層アプリケーションに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのリソース パラメーターを表示するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティのダッシュボードを使用します。 詳細については、「[SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーの結果を表示するには、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] からユーティリティ コントロール ポイントに接続します。 詳細については、「[ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの正常性ポリシーは、データ層アプリケーション、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンス用に構成できます。 正常性ポリシーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのデータ層アプリケーションおよびマネージ インスタンスに対してグローバルに定義できます。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ層アプリケーションごと、およびマネージ インスタンスごとに個別に定義することもできます。  
  
## データ層アプリケーションのポリシーの監視  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ層アプリケーションの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   データ層アプリケーションのプロセッサ使用率  
  
-   データ層アプリケーションのデータベース ファイル用のファイル領域  
  
-   データ層アプリケーションの記憶域ボリューム用のファイル領域  
  
-   コンピューターのプロセッサ使用率  
  
> [!NOTE]  
>  データ層アプリケーションの場合、記憶域ボリュームとプロセッサ使用率は読み取り専用ポリシーです。  
  
 データ層アプリケーションのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md)」をご覧ください。  
  
 データ層アプリケーション個々の監視ポリシーの表示および変更の詳細については、「[配置済みのデータ層アプリケーションの詳細 &#40;SQL Server ユーティリティ&#41;](../Topic/Deployed%20Data-tier%20Application%20Details%20\(SQL%20Server%20Utility\).md)」をご覧ください。  
  
## SQL Server のマネージ インスタンスのポリシーの監視  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスの過大使用ポリシーと過小使用ポリシーは次のとおりです。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのプロセッサ使用率。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベース ファイル用のファイル領域。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの記憶域ボリューム用のファイル領域。  
  
-   コンピューターのプロセッサ使用率  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージ インスタンスのグローバルな監視ポリシーの表示および変更の詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md)」をご覧ください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の個々のマネージ インスタンスの監視ポリシーの表示および変更の詳細については、「[マネージ インスタンスの詳細 &#40;SQL Server ユーティリティ&#41;](../Topic/Managed%20Instance%20Details%20\(SQL%20Server%20Utility\).md)」を参照してください。  
  
## 参照  
 [SQL Server ユーティリティの機能とタスク](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  