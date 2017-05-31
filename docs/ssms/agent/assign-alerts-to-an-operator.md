---
title: "オペレーターへの警告の割り当て | Microsoft Docs"
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
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dc10ef2ce9fd666cef48bc286ae5c0d4acc6514
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="assign-alerts-to-an-operator"></a>オペレーターへの警告の割り当て
このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] または [!INCLUDE[tsql](../../includes/tsql_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの警告をオペレーターに割り当てて、ジョブに関する通知を受信できるようにする方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **オペレーターに警告を割り当てる方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] は、警告システム全体を簡単に管理できるグラフィカルなツールです。 警告システムを構成するときには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] を使用することをお勧めします。  
  
-   警告に対応して通知を送るには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがメールを送れるようにあらかじめ構成しておく必要があります。 詳細については、「 [Configure SQL Server Agent Mail to Use Database Mail](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)」を参照してください。  
  
-   電子メールのメッセージやポケットベルによる通知に失敗した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス エラー ログに失敗がレポートされます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
オペレーターに警告を割り当てることができるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-assign-alerts-to-an-operator"></a>オペレーターに警告を割り当てるには  
  
1.  **オブジェクト エクスプローラー**で、警告を割り当てるオペレーターを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  プラス記号をクリックして **[オペレーター]** フォルダーを展開します。  
  
4.  警告を割り当てるオペレーターを右クリックし、**[プロパティ]** を選択して、**[通知]** ページを選択します。  
  
5.  [*operator_name* **のプロパティ]** ダイアログ ボックスで、**[ページの選択]** の **[通知]** を選択します。  
  
6.  **[このユーザーに送信された通知の表示方法]**で、 **[警告]** を選択してこのオペレーターに送信する警告の一覧を表示するか、または **[ジョブ]** を選択してこのオペレーターに通知を送信するジョブの一覧を表示します。 **[電子メール]**、 **[ポケットベル]**、 **[Net Send]**のチェック ボックスの中から 1 つ以上を選択し、必要に応じて通知ごとに通知方法を定義します。  
  
7.  完了したら、 **[OK]**をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-assign-alerts-to-an-operator"></a>オペレーターに警告を割り当てるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists
    -- and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
詳細については、「 [sp_add_notification (Transact-SQL)](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd)」を参照してください。  
  

