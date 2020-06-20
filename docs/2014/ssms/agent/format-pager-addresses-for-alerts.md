---
title: 警告用のポケットベル アドレスの形式設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3754afbc5d8f0f67dac61e785a4626c8ced4c2e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995300"
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
  このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] またはを使用して、エージェントの警告のポケットベルアドレスの形式を設定する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ポケットベル アドレスの形式を設定する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 既定では、警告に関する情報を表示できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-format-pager-addresses"></a>ポケットベル アドレスの形式を設定するには  
  
1.  **オブジェクト エクスプローラー**で、ポケットベルに送信する警告を含むサーバーをプラス記号をクリックして展開します。  
  
2.  **SQL Server エージェント**を右クリックし、[**プロパティ**] を選択します。  
  
3.  **[ページの選択]** の **[警告システム]** を選択します。  
  
4.  **[ポケットベル メールのアドレス形式]** フィールドの **[[宛先] 行]** ボックスおよび **[[CC] 行]** ボックスに、ポケットベル アドレスのプレフィックスまたはサフィックスを入力します。 オペレーターの実際のポケットベル アドレスは、通知の送信時に挿入されます。  
  
5.  **[件名]** ボックスに、件名行のプレフィックスまたはサフィックスを入力します。  
  
6.  **[通知メッセージに電子メールの本文を含める]** チェック ボックスをオンにして、ポケットベルのメッセージに (件名行のみではなく) 完全な電子メール メッセージを含めます。  
  
7.  完了したら、[**OK**] をクリックします。  
  
  
