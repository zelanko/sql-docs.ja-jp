---
title: "異種データベース レプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "異種データベース レプリケーション, 異種データベース レプリケーションの概要"
  - "レプリケーション [SQL Server], 異種データベース レプリケーション"
  - "異種データベース レプリケーション"
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# 異種データベース レプリケーション
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] トランザクションおよびスナップショット レプリケーションの次の異種シナリオをサポートしています。  
  
-   Oracle から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのデータのパブリッシュ  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーへのデータのパブリッシュ  
  
 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 Oracle パブリッシングは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## Oracle からのデータのパブリッシュ  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スナップショット レプリケーションとトランザクション レプリケーションとほぼ同じ機能を使用し、同様の使いやすさで Oracle からのデータをパブリッシュできます。 Oracle からのデータのパブリッシュは、次のようなシナリオに適しています。  
  
|Scenario|説明|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET framework アプリケーションの展開|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。|  
|データ ウェアハウジング ステージング サーバー|保持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外の同期ステージング データベース[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースです。|  
|移行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|ソース システムの変更のレプリケーション中に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。 移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。|  
  
 詳細については、次を参照してください。 [発行の概要は Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)します。  
  
## SQL Server 以外のサブスクライバーへのデータのパブリッシュ  
 以下の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースは、スナップショット パブリケーションとトランザクション パブリケーションに対するサブスクライバーとしてサポートされています。  
  
-   Oracle (Oracle がサポートするすべてのプラットフォーム用)  
  
-   IBM DB2 (AS400、MVS、Unix、Linux、および Windows 用)  
  
 詳細については、次を参照してください。 [非 SQL Server サブスクライバー](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。  
  
  