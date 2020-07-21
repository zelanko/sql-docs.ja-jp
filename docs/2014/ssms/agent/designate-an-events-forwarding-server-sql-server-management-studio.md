---
title: イベント転送サーバーを指定する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1617038a42dcef9103613e4d0164ba0f796000fa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995282"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
  このトピックでは、を使用して、でイベントを転送するサーバーを指定する方法について説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。 イベントの転送の適用対象は、単一のコンピューターでホストされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間で転送されるイベントではなく、サーバー間で転送されるイベントであることに注意してください。 また、転送されたイベントを受信するには、警告管理サーバーが SQL Server の既定のインスタンスでなければならないことにも注意してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **イベントの転送先サーバーを指定する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-designate-an-events-forwarding-server"></a>イベントの転送先サーバーを指定するには  
  
1.  **オブジェクト エクスプ ローラー** で、プラス記号をクリックして、別のサーバーにイベントを転送するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。  

3.  **[SQL Server エージェントのプロパティ - **_<サーバー名>]_ ダイアログ ボックスの **[ページの選択]** で **[詳細設定]** を選択します。  

4.  **[SQL Server イベントの転送]** で、 **[イベントを別のサーバーに転送する]** チェック ボックスをオンにします。  
  
5.  **[サーバー]** ボックスの一覧でサーバーを選択し、 **[イベント]** で次のいずれかの操作を行います。  
  
    -   ローカルの警告で処理されていないイベントのみを転送する場合は、 **[未処理のイベント]** をクリックします。  
  
    -   ローカルの警告によって処理されたかどうかにかかわらず、すべてのイベントを転送する場合は、 **[すべてのイベント]** をクリックします。  
  
6.  **[次のレベル以上のイベント発生時]** ボックスの一覧で、選択したサーバーにイベントを転送するときの重大度レベルをクリックします。  
  
7.  完了したら、[**OK**] をクリックします。  
  
  
