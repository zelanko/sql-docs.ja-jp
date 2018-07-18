---
title: 対象サーバーのクロックの同期 (SQL Server Management Studio) | Microsoft Docs
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
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df6882d1424990ab746e45e299d2cb3ce205b100
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297817"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a>対象サーバーのクロックの同期 (SQL Server Management Studio)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の対象サーバーのクロックとマスター サーバーのクロックの同期をとる方法について説明します。 これらのシステム クロックの同期をとると、ジョブのスケジュールを効果的に管理できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **対象サーバーのクロックの同期をとる方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-synchronize-target-server-clocks"></a>対象サーバーのクロックの同期をとるには  
  
1.  **オブジェクト エクスプローラー** で、対象サーバーのクロックとマスター サーバーのクロックの同期をとるサーバーをプラス記号をクリックして展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[対象サーバーの管理]** を選択します。  
  
3.  **[対象サーバーの管理]** ダイアログ ボックスで **[命令を通知]** をクリックします。  
  
4.  **[命令の種類]** ボックスの一覧で、 **[クロックの同期]** を選択します。  
  
5.  **[受信者]** で、次のいずれかの操作を行います。  
  
    -   すべての対象サーバーのクロックとマスター サーバーのクロックの同期をとるには、 **[すべての対象サーバー]** をクリックします。  
  
    -   特定のサーバーのクロックと同期をとるには、 **[特定の対象サーバー]** をクリックし、マスター サーバーのクロックと同期をとる対象サーバーを選択します。  
  
6.  完了したら、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-synchronize-target-server-clocks"></a>対象サーバーのクロックの同期をとるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_resync_targetserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)します。  
  
  
