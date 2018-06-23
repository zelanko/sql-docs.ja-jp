---
title: DQS のプロファイル通知の有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c75e3e72811e70be60faed522be0958122bb3e8c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075809"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a>DQS のプロファイル通知の有効化または無効化
  このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のプロファイル通知を有効または無効にする方法について説明します。 既定では、DQS のプロファイル通知は有効です。 プロファイル通知によって、データ ソースについての重要な情報と、データに対して行われている現在のアクティビティの有効性が伝えられます。 詳細については、次を参照してください。 [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)です。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 通知を有効にするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="Enable"></a> プロファイル通知の有効化または無効化  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。  
  
3.  次に **[全般設定]** タブをクリックします。  
  
4.  DQS のさまざまなアクティビティのプロファイル通知を無効または有効にするには、 **[通知の有効化]** チェック ボックスをオフまたはオンにします。  
  
5.  **[閉じる]** をクリックします。  
  
  