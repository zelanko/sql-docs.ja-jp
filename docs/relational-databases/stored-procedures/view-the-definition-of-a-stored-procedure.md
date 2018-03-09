---
title: "ストアド プロシージャの定義の表示 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: d05c919b5d532434c33c269d1c287871ff818ac9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="view-the-definition-of-a-stored-procedure"></a>ストアド プロシージャの定義の表示
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
    
##  <a name="Top"></a> ストアド プロシージャの定義は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプローラーのメニュー オプションを使用するか、クエリ エディターで [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して表示できます。 このトピックでは、オブジェクト エクスプローラーでプロシージャの定義を表示する方法について説明します。さらに、クエリ エディターでのシステム プロシージャ、システム関数、およびオブジェクト カタログ ビューを使用した表示方法について説明します。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **プロシージャの定義を**  [SQL Server Management Studio](#SSMSProcedure)または [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 システム ストアド プロシージャ: **sp_helptext**  
 ロール **public** のメンバーシップが必要です。 システム オブジェクトの定義は、公開されます。 ユーザー オブジェクトの定義は、オブジェクトの所有者、または ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION のいずれかの権限を許可された人が表示できます。  
  
 システム関数: **OBJECT_DEFINITION**  
 システム オブジェクトの定義は、公開されます。 ユーザー オブジェクトの定義は、オブジェクトの所有者、または ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION のいずれかの権限を許可された人が表示できます。 これらの権限は **db_owner**、 **db_ddladmin**、および **db_securityadmin** 固定データベース ロールのメンバーが暗黙的に保有します。  
  
 オブジェクト カタログ ビュー: **sys.sql_modules**  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
##  <a name="Procedures"></a> ストアド プロシージャの定義の表示方法  
 次のいずれかを使用します。  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **オブジェクト エクスプローラーでプロシージャの定義を表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]**を展開します。  
  
3.  **[ストアド プロシージャ]**を展開します。プロシージャを右クリックし、 **[ストアド プロシージャをスクリプト化]**を選択し、 **[CREATE]**、 **[ALTER]**、 **[DROP および CREATE]**のいずれかをクリックします。  
  
4.  **[新しいクエリ エディター ウィンドウ]**をクリックします。 プロシージャの定義が表示されます。  
  
###  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **クエリ エディターでプロシージャの定義を表示するには**  
  
 システム ストアド プロシージャ: **sp_helptext**  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  クエリ ウィンドウで、 **sp_helptext** システム ストアド プロシージャを使用した次のステートメントを入力します。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 システム関数: **OBJECT_DEFINITION**  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  クエリ ウィンドウで、 **OBJECT_DEFINITION** システム関数を使用した次のステートメントを入力します。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 オブジェクト カタログ ビュー: **sys.sql_modules**  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  クエリ ウィンドウで、 **sys.sql_modules** カタログ ビューを使用した次のステートメントを入力します。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [ストアド プロシージャの変更](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [ストアド プロシージャの削除](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [ストアド プロシージャの名前の変更](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
  
  
