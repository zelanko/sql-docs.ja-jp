---
title: SQL Server (SQL Server 構成マネージャー) のインスタンスの自動開始の回避 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b21ac71b54c9bfee76079f86c1d6d1a32fc0f9dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073540"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>SQL Server のインスタンスの自動開始の回避 (SQL Server 構成マネージャー)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で SQL Server 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスが自動的に開始されないようにする方法について説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常、自動的に開始するように構成されます。 インスタンスの開始モードを手動に設定することによって、その構成を変更できます。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>SQL Server のインスタンスの自動開始を回避するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
2.  [SQL Server 構成マネージャー] で **[サービス]** を展開し、 **[SQL Server]** をクリックします。  
  
3.  詳細ペインで、 **[MSSQLServer]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  **SQL Server \< ***instancename***> プロパティ** ダイアログ ボックスで、**プロパティ**ボックスの値を設定**開始モード**に**手動**です。  
  
5.  **[OK]** をクリックして **[SQL Server \<***instancename***> のプロパティ]** ダイアログ ボックスを閉じ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを閉じます。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](start-stop-pause-resume-restart-sql-server-services.md)  
  
  