---
title: "警告用のポケットベル アドレスの形式設定 | Microsoft Docs"
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
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f202f1e48ca7c9ef030b5434514c4c5d6a93300b
ms.lasthandoff: 04/11/2017

---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] または [!INCLUDE[tsql](../../includes/tsql_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの警告で使用するポケットベル アドレスの形式を設定する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ポケットベル アドレスの形式を設定する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
既定では、警告に関する情報を表示できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-format-pager-addresses"></a>ポケットベル アドレスの形式を設定するには  
  
1.  **オブジェクト エクスプローラー**で、ポケットベルに送信する警告を含むサーバーをプラス記号をクリックして展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]**を選択します。  
  
3.  **[ページの選択]**の **[警告システム]**を選択します。  
  
4.  **[ポケットベル メールのアドレス形式]** フィールドの **[[宛先] 行]** ボックスおよび **[[CC] 行]** ボックスに、ポケットベル アドレスのプレフィックスまたはサフィックスを入力します。 オペレーターの実際のポケットベル アドレスは、通知の送信時に挿入されます。  
  
5.  **[件名]** ボックスに、件名行のプレフィックスまたはサフィックスを入力します。  
  
6.  **[通知メッセージに電子メールの本文を含める]** チェック ボックスをオンにして、ポケットベルのメッセージに (件名行のみではなく) 完全な電子メール メッセージを含めます。  
  
7.  完了したら、 **[OK]**をクリックします。  
  

