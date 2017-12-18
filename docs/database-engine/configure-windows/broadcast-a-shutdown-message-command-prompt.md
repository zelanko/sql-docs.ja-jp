---
title: "シャットダウン メッセージのブロードキャスト (コマンド プロンプト) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
caps.latest.revision: "28"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b5df96a865ac1c34a884b0829c2c3995a300672
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>シャットダウン メッセージのブロードキャスト (コマンド プロンプト)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で **net send** コマンドを使用して、シャットダウン メッセージをブロードキャストする方法について説明します。 このメッセージには、ユーザーが現在行っている作業を終了できるように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが停止する時間を含めてください。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>シャットダウン メッセージをブロードキャストするには  
  
1.  コマンド プロンプトで、次のように入力します。  
  
     **net send /users "message"**  
  
     **/users** オプションを指定すると、サーバーに接続されたすべてのユーザーにメッセージが送信されます。  
  
> [!NOTE]  
>  **net send** コマンドを使用するには、メッセンジャー サービスを送信用コンピューターと受信用コンピューターの両方で実行しておく必要があります。 メッセンジャー サービスは Windows Server 2003 では既定で無効になっています。 **net send**の詳細については、Windows のマニュアルを参照してください。  
  
 使用しているネットワークによっては、電子メールや電話でユーザーに連絡する方が適している場合もあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に現在接続しているユーザーを確認するには、利用状況モニターを使用します。 利用状況モニターの詳細については、「[利用状況モニター](../../relational-databases/performance-monitor/activity-monitor.md)」および「[利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
