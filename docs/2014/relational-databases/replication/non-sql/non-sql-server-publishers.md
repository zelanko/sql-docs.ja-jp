---
title: SQL Server 以外のパブリッシャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19db106c43007259754bace7f0e9d2938ad9cf1e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52752574"
---
# <a name="non-sql-server-publishers"></a>SQL Server 以外のパブリッシャー
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のソースからパブリッシュされたデータは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に統合できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、Oracle データベースからパブリッシュされたスナップショット データまたはトランザクション データをサブスクライブできます。 Oracle からのパブリッシュの詳細については、「[Oracle Publishing Overview](oracle-publishing-overview.md)」 (Oracle パブリッシングの概要) を参照してください。  
  
 SQL Server 以外のサブスクライバーへの異種レプリケーションは非推奨とされます。 Oracle パブリッシングは非推奨とされます。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 以下のような場合には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースからのパブリッシュが理想的です。  
  
|シナリオ|説明|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アプリケーションの配置|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。|  
|データ ウェアハウジング ステージング サーバー|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステージング データベースと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースとの同期を保ちます。|  
| [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|ソース システムの変更のレプリケーション中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。 移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。|  
  
## <a name="see-also"></a>参照  
 [Heterogeneous Database Replication](heterogeneous-database-replication.md)  
  
  
