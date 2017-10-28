---
title: "SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 950c4d2fdef0359042ebbed168c761e44316ab03
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成
このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent_md.md)] で、SQL Server ツールにサーバーの状態を表示するように WMI を構成する方法について説明します。 サーバーに接続する際には、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]構成マネージャーだけでなく [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] のコンポーネントである登録済みサーバーおよびオブジェクト エクスプローラーの両方で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] (MSSQLSERVER) サービスおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] エージェント (MSSQLSERVER) サービスの状態を取得するために、WMI (Windows Management Instrumentation) が使用されます。 サービスの状態を表示するには、WMI オブジェクトに対するリモート アクセスの権限が必要です。 このアクセス許可を構成するには、サーバーに WMI をインストールする必要があります。  
  
## <a name="SSMSProcedure"></a>WMI のアクセス許可を構成するには  
  
1.  リモート サーバーの **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]**をクリックします。  
  
2.  **[名前]** ボックスに「 **wmimgmt.msc**」と入力し、 **[OK]**をクリックします。  
  
3.  **[Windows Management Infrastructure (WMI)]** の **[WMI コントロール (ローカル)]**を右クリックし、 **[プロパティ]**をクリックします。  
  
4.  **[WMI コントロール (ローカル) のプロパティ]** ダイアログ ボックスの **[セキュリティ]** タブで、 **[Root]**を展開し、 **[CIMV2]**をクリックします。  
  
5.  **[セキュリティ]** をクリックして **[セキュリティ ROOT\CIMV2]** ダイアログ ボックスを開きます。  
  
6.  **[グループ名またはユーザー名]** ボックスにグループまたはユーザーを追加して選択します。  
  
7.  **[***<group or user> のアクセス許可]* ボックスで、サービスの状態をリモートから確認できるようにするユーザーの **[リモートの有効化]** の **[許可]** 列にあるチェック ボックスをオンにします。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント サービスの開始、停止、または一時停止](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  

