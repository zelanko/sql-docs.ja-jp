---
title: "DQS のプロファイル通知の有効化または無効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enable notifications"
  - "notifications,enable"
  - "通知, 無効化"
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# DQS のプロファイル通知の有効化または無効化
  このトピックでは、[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のプロファイル通知を有効または無効にする方法について説明します。 既定では、DQS のプロファイル通知は有効です。 プロファイル通知によって、データ ソースについての重要な情報と、データに対して行われている現在のアクティビティの有効性が伝えられます。 詳細については、「 [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md)」をご参照ください。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 通知を有効にするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="Enable"></a> プロファイル通知の有効化または無効化  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Data Quality Client アプリケーションを実行](../data-quality-services/run-the-data-quality-client-application.md)します。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]**をクリックします。  
  
3.  次に **[全般設定]** タブをクリックします。  
  
4.  DQS のさまざまなアクティビティのプロファイル通知を無効または有効にするには、 **[通知の有効化]** チェック ボックスをオフまたはオンにします。  
  
5.  **[閉じる]**をクリックします。  
  
  