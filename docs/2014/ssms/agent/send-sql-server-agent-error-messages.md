---
title: SQL Server エージェントのエラー メッセージの送信 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1aa0faafc6fb1cca693fe58665c7344db84c9f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62666789"
---
# <a name="send-sql-server-agent-error-messages"></a>Send SQL Server Agent Error Messages
  このトピックでは、を使用し[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]て、で[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] net send を使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]してエラーメッセージを送信するようにエージェントを構成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントエラーメッセージを送信するには](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   net send イベントを受信するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger サービスを実行している必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 **固定サーバー ロールの **sysadmin[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
 エージェントサービスアカウントに必要な Windows アクセス許可の詳細については、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-send-sql-server-agent-error-messages"></a>SQL Server エージェントのエラー メッセージを送信するには  
  
1.  
  **オブジェクト エクスプローラー**で、プラス記号をクリックして、net send によるエラー メッセージの送信元となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログを含むサーバーを展開します。  
  
2.  **SQL Server エージェント**を右クリックし、[**プロパティ**] を選択します。  
  
3.  [ **SQL Server エージェントのプロパティ-**_server_name_ ] ダイアログボックスの [**全般**] ページで、[**エラーログ**] の下の [ **Net send 受信者**] ボックスに、エラーメッセージの送信先となるユーザー名またはコンピューター名を入力します。  
  
4.  **[OK]** をクリックします。  
  
  
