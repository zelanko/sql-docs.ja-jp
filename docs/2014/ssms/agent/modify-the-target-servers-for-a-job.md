---
title: ジョブの対象サーバーの変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dab9b2cca2848864400af2e86a47b600db2aed04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071347"
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエージェント ジョブの対象サーバーを変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ジョブの対象サーバーを変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 既定では、このストアド プロシージャを実行できるのは、sysadmin 固定サーバー ロールのメンバーです。 他のユーザーには、msdb データベースにおける次のいずれかの SQL Server エージェント固定データベース ロールが許可されている必要があります。  
  
1.  `SQLAgentUserRole`  
  
2.  `SQLAgentReaderRole`  
  
3.  SQLAgentOperatorRole  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>ジョブの対象サーバーを変更するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、ジョブを右クリックします。次に、 **[プロパティ]** をクリックします。  
  
3.  **[ジョブのプロパティ]** ダイアログ ボックスで **[対象サーバー]** ページをクリックし、 **[ローカル サーバーを対象とする]** または **[複数のサーバーを対象とする]** をクリックします。  
  
     **[複数のサーバーを対象とする]** を選択した場合は、サーバー名の左にあるチェック ボックスをオンにして、それらのサーバーがジョブの対象になるように設定します。 ジョブの対象としないサーバーのチェック ボックスがオフになっていることを確認します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>ジョブの対象サーバーを変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、マルチサーバー ジョブの Weekly Sales Backups をサーバー SEATTLE2 に割り当てます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
  
```  
  
 詳細については、次を参照してください。 [sp_add_jobserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)です。  
  
## <a name="see-also"></a>参照  
 [エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md)  
  
  
