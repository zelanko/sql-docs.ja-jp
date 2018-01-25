---
title: "レプリケーション モニターの開始 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
caps.latest.revision: "36"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f5e9b5a38bbd6ef2468a21683b3279602edf8336
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="start-the-replication-monitor"></a>レプリケーション モニターの開始
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] レプリケーション モニターは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の任意のインスタンスに対して起動するか、コマンド プロンプトから起動できます。 レプリケーション モニターを起動した後、1 つ以上のパブリッシャーをモニターに追加します。 詳細については、「 [レプリケーション モニターのパブリッシャーの追加および削除](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)」を参照してください。  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>SQL Server Management Studio からレプリケーション モニターを起動するには  
  
1.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]のインスタンスに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーまたはそのサブフォルダーを右クリックして、 **[レプリケーション モニターの起動]**をクリックします。  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>コマンド プロンプトからレプリケーション モニターを起動するには  
  
1.  コマンド プロンプトで、ツールをインストールしたディレクトリに移動します。 既定のパスは [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ です。  
  
2.  sqlmonitor.exe を実行します。  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
