---
title: "ジョブ履歴ログのセットアップ | Microsoft Docs"
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
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82d09693143af337c03a54e653f029fb50710a17
ms.lasthandoff: 04/11/2017

---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブ履歴ログをセットアップする方法について説明します。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **ジョブ履歴ログをセットアップする方法:** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
**ジョブ履歴ログをセットアップするには**  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[SQL Server エージェントのプロパティ]** ダイアログ ボックスで **[履歴]** ページをクリックします。  
  
4.  次のいずれかのオプションを選択します。  
  
    1.  **[ジョブ履歴ログのサイズを制限する]**チェック ボックスをオンにして、ジョブ履歴ログの最大行数と、ジョブあたりの最大行数を入力します。  
  
    2.  **[自動的にエージェントの履歴を削除する]**チェック ボックスをオンにして、期間を指定します。この期間を過ぎると、履歴がログから削除されます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
[ジョブの利用状況の監視](../../ssms/agent/monitor-job-activity.md)  
[ジョブの作成](../../ssms/agent/create-jobs.md)  
  

