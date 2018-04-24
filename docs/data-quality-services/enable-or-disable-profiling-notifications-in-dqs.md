---
title: DQS のプロファイル通知の有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: ''
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 790ee9b14c229e0409a235452e53d66736b9a0bd
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a>DQS のプロファイル通知の有効化または無効化

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のプロファイル通知を有効または無効にする方法について説明します。 既定では、DQS のプロファイル通知は有効です。 プロファイル通知によって、データ ソースについての重要な情報と、データに対して行われている現在のアクティビティの有効性が伝えられます。 詳細については、「 [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md)」をご参照ください。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 通知を有効にするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="Enable"></a> プロファイル通知の有効化または無効化  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。  
  
3.  次に **[全般設定]** タブをクリックします。  
  
4.  DQS のさまざまなアクティビティのプロファイル通知を無効または有効にするには、 **[通知の有効化]** チェック ボックスをオフまたはオンにします。  
  
5.  **[閉じる]** をクリックします。  
  
  
