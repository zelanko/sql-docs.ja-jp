---
title: "SQL Server 以外のパブリッシャー | Microsoft Docs"
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
  - "異種データベース レプリケーション, SQL Server 以外のパブリッシャー"
  - "SQL Server 以外のパブリッシャー"
  - "異種データ ソース, SQL Server 以外のパブリッシャー"
  - "パブリッシャー [SQL Server replication], Oracle"
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# SQL Server 以外のパブリッシャー
  以外のデータを公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ソースでは、データを統合することができます [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スナップショット パブリケーションまたは Oracle データベースからパブリッシュされるトランザクションのデータにサブスクライブできます。 Oracle からの発行に関する詳細については、次を参照してください。 [発行の概要は Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)します。  
  
 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 Oracle パブリッシングは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 以下のような場合には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースからのパブリッシュが理想的です。  
  
|Scenario|説明|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET framework アプリケーションの展開|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。|  
|データ ウェアハウジング ステージング サーバー|保持 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外の同期ステージング データベース[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースです。|  
|移行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|ソース システムの変更のレプリケーション中に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。 移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。|  
  
## 参照  
 [異種データベース レプリケーション](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  