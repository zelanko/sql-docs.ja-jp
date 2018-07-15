---
title: ジョブ カテゴリ情報の一覧の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33cf862e752618b35c56d2e5c58f534ca03a347d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280818"
---
# <a name="list-job-category-information"></a>ジョブ カテゴリ情報の一覧の表示
  ジョブ カテゴリ情報を一覧表示する方法[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]または SQL Server 管理オブジェクト。  

  
##  <a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  

  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-list-job-category-information"></a>ジョブ カテゴリ情報の一覧を表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_help_category &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql)します。  
  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブ カテゴリ情報の一覧を表示するには**  
  
 使用して、 `JobCategory` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス. 詳細については、次を参照してください。 [SQL Server 管理オブジェクト&#40;SMO&#41;プログラミング ガイド](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)します。  
  
  
  
