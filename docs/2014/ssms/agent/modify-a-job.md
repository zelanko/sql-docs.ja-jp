---
title: ジョブの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df29ac669fba94afb386132c2368cc61cd6b5ccd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189542"
---
# <a name="modify-a-job"></a>Modify a Job
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのプロパティを変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**   
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **ジョブを変更する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
###  <a name="Security"></a> セキュリティ  
 **sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-a-job"></a>ジョブを変更するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、変更するジョブを右クリックします。次に、 **[プロパティ]** をクリックします。  
  
3.  **[ジョブのプロパティ]** ダイアログ ボックスの対応するページを使用して、ジョブのプロパティ、ステップ、スケジュール、警告、および通知を変更します。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-modify-a-job"></a>ジョブを変更するには  
  
1.  オブジェクト エクスプローラーで、データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリ ウィンドウで、次のシステム ストアド プロシージャを使用してジョブを変更します。  
  
    -   実行[sp_update_job &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)ジョブの属性を変更します。  
  
    -   実行[sp_update_schedule &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)ジョブ定義のスケジューリングの詳細を変更します。  
  
    -   実行[sp_add_jobstep &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)新しいジョブ ステップを追加します。  
  
    -   実行[sp_update_jobstep &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)の既存のジョブ ステップを変更します。  
  
    -   実行[sp_delete_jobstep &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)ジョブからジョブ ステップを削除します。  
  
    -   任意の SQL Server エージェント マスター ジョブを変更するための追加のストアド プロシージャ:  
  
        -   実行[sp_delete_jobserver &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql)ジョブに関連付けられているサーバーを削除します。  
  
        -   実行[sp_add_jobserver &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)にサーバーを現在のジョブに関連付けます。  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブを変更するには**  
  
 使用して、 `Job` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
  
