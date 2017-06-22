---
title: "SQL Server 以外のパブリッシャー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 72a1a8c69a7c18f02da6439af94fefffe73a03a3
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="non-sql-server-publishers"></a>SQL Server 以外のパブリッシャー
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のソースからパブリッシュされたデータは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に統合できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、Oracle データベースからパブリッシュされたスナップショット データまたはトランザクション データをサブスクライブできます。 Oracle からのパブリッシュの詳細については、「[Oracle Publishing Overview](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)」 (Oracle パブリッシングの概要) を参照してください。  
  
 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 Oracle パブリッシングは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 以下のような場合には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースからのパブリッシュが理想的です。  
  
|Scenario|説明|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アプリケーションの配置|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。|  
|データ ウェアハウジング ステージング サーバー|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステージング データベースと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースとの同期を保ちます。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への移行|ソース システムの変更のレプリケーション中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。 移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。|  
  
## <a name="see-also"></a>参照  
 [Heterogeneous Database Replication](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
