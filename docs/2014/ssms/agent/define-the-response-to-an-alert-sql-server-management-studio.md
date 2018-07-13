---
title: 警告への応答の定義 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91eebf84cdcb9750e7a5aef10b88b1c3b0bbc31e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200702"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>警告への応答の定義 (SQL Server Management Studio)
  このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がどのように応答するかを定義する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **警告に対する応答を定義する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   今後のバージョンの **では、** エージェントからポケットベル オプションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプションが削除される予定です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。  
  
-   SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。 詳細については、「 [オペレーターへの警告の割り当て](http://msdn.microsoft.com/library/ms190038.aspx)」を参照してください。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 警告に対する応答を定義できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-define-the-response-to-an-alert"></a>警告に対する応答を定義するには  
  
1.  **オブジェクト エクスプローラー**で、応答を定義する警告を格納するサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[警告]** フォルダーを展開します。  
  
4.  応答を定義する警告を右クリックし、 **[プロパティ]** を選択します。  
  
5.  *[<アラート名> 警告のプロパティ]* ダイアログ ボックスの **[ページの選択]** で **[応答]** を選択します。  
  
6.  **[ジョブの実行]** チェック ボックスをオンにし、 **[ジョブの実行]** チェック ボックスの下に表示されている一覧から、警告の発生時に実行するジョブを選択します。 **[新しいジョブ]** をクリックすることで、新しいジョブを作成できます。 **[ジョブの表示]** をクリックすると、ジョブに関するより詳しい情報を表示できます。 **[新しいジョブ]** ダイアログ ボックスと *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで使用できるオプションの詳細については、「[ジョブの作成](create-a-job.md)」と「[ジョブの表示](view-a-job.md)」を参照してください。  
  
7.  警告がアクティブになったときにオペレーターに通知する場合は、 **[オペレーターに通知する]** チェック ボックスをオンにします。 **[オペレーター一覧]** の **[電子メール]**、 **[ポケットベル]**、 **[Net Send]** から、オペレーターに通知する方法を選択します (複数選択可)。 **[新しいオペレーター]** をクリックすることで、新しいオペレーターを作成できます。 **[オペレーターの表示]** をクリックすることで、オペレーターに関するより詳しい情報を表示できます。 **[新しいオペレーター]** ダイアログ ボックスと **[オペレーターのプロパティの表示]** ダイアログ ボックスで使用できるオプションの詳細については、「 [Create an Operator](create-an-operator.md) 」と「 [View Information About an Operator](view-information-about-an-operator.md)」を参照してください。  
  
8.  完了したら、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-define-the-response-to-an-alert"></a>警告に対する応答を定義するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that François Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_add_notification &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)します。  
  
  
