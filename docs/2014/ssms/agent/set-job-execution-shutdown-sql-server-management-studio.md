---
title: ジョブ実行のシャットダウンの設定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca9343fe8a6f9e89ba9f26dbbbb12dd7362aff91
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033604"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Set Job Execution Shutdown (SQL Server Management Studio)
  このトピックでは、で[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]して、エージェント自体が終了する前に、実行中のジョブの終了をエージェントが待機する時間を設定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **SQL Server エージェント ジョブのシャットダウン時間を設定する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント自体が終了する前に、実行中のジョブの終了を [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが待機する時間を設定できるのは、**sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-set-job-execution-shutdown"></a>ジョブ実行のシャットダウンを設定するには  
  
1.  **オブジェクト エクスプ ローラー** で、プラス記号をクリックして、ジョブ実行のシャットダウン間隔を設定するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。  
  
3.  **[ページの選択]** の **[ジョブ システム]** を選択します。  
  
4.  **[シャットダウン タイムアウト間隔]** (秒単位) を増やすか、または減らしてシャットダウン タイムアウト間隔を調整します。 この値により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント自体が終了される前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行中のジョブの終了を待機する時間が決まります。  
  
  
