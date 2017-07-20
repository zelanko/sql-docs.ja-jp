---
title: "ジョブ履歴ログのサイズの変更 | Microsoft Docs"
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
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 47182ebd082dfae0963d761e54c4045be927d627
ms.openlocfilehash: 77a39273f5fa02bac3255ea0436341db2342c236
ms.contentlocale: ja-jp
ms.lasthandoff: 07/11/2017

---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブ履歴ログのサイズ制限を設定する方法について説明します。
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ履歴ログのサイズ制限を設定する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>生のサイズに基づいてジョブ履歴ログのサイズを変更するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[履歴]** ページを選択し、 **[ジョブ履歴ログのサイズを制限する]**チェック ボックスがオンになっていることを確認します。  
  
4.  **[ジョブ履歴ログの最大サイズ (行)]** ボックスで、ジョブ履歴ログに使用できる最大行数を入力します。  
  
5.  **[ジョブごとのジョブ履歴の最大行数]** ボックスで、1 つのジョブに使用できるジョブ履歴の最大行数を入力します。  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>時間に基づいてジョブ履歴ログのサイズを変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[履歴]** ページを選択し、 **[自動的にエージェントの履歴を削除する]**チェック ボックスをオンにします。  
  
4.  適切な **[日]**、 **[週]**、または **[月]**を選択します。  
  

