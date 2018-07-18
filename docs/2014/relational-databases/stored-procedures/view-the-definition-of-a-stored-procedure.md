---
title: ストアド プロシージャの定義の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09737f1b9764680e67dbb0bbefb2d0ec86df71e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288408"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>ストアド プロシージャの定義の表示
    
##  <a name="Top"></a> ストアド プロシージャの定義は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプローラーのメニュー オプションを使用するか、クエリ エディターで [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して表示できます。 このトピックでは、オブジェクト エクスプローラーでプロシージャの定義を表示する方法について説明します。さらに、クエリ エディターでのシステム プロシージャ、システム関数、およびオブジェクト カタログ ビューを使用した表示方法について説明します。  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **プロシージャの定義を**  [SQL Server Management Studio](#SSMSProcedure)または [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 システム ストアド プロシージャ: `sp_helptext`  
 ロール **public** のメンバーシップが必要です。 システム オブジェクトの定義は、公開されます。 ユーザー オブジェクトの定義は、オブジェクトの所有者、または ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION のいずれかの権限を許可された人が表示できます。  
  
 システム関数: `OBJECT_DEFINITION`  
 システム オブジェクトの定義は、公開されます。 ユーザー オブジェクトの定義は、オブジェクトの所有者、または ALTER、CONTROL、TAKE OWNERSHIP、VIEW DEFINITION のいずれかの権限を許可された人が表示できます。 これらの権限は **db_owner**、 **db_ddladmin**、および **db_securityadmin** 固定データベース ロールのメンバーが暗黙的に保有します。  
  
 オブジェクト カタログ ビュー: `sys.sql_modules`  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)」を参照してください。  
  
##  <a name="Procedures"></a> ストアド プロシージャの定義の表示方法  
 次のいずれかを使用します。  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **オブジェクト エクスプローラーでプロシージャの定義を表示するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]** を展開します。  
  
3.  **[ストアド プロシージャ]** を展開します。プロシージャを右クリックし、 **[ストアド プロシージャをスクリプト化]** を選択し、 **[CREATE]**、 **[ALTER]**、 **[DROP および CREATE]** のいずれかをクリックします。  
  
4.  **[新しいクエリ エディター ウィンドウ]** をクリックします。 プロシージャの定義が表示されます。  
  
###  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **クエリ エディターでプロシージャの定義を表示するには**  
  
 システム ストアド プロシージャ: `sp_helptext`  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリ ウィンドウで使用する、次のステートメントを入力、`sp_helptext`システム ストアド プロシージャ。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 システム関数: `OBJECT_DEFINITION`  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリ ウィンドウで、`OBJECT_DEFINITION` システム関数を使用した次のステートメントを入力します。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 オブジェクト カタログ ビュー: `sys.sql_modules`  
 1.  オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  クエリ ウィンドウで入力を使用して、次のステートメント、`sys.sql_modules`カタログ ビューです。 データベース名とストアド プロシージャ名を変更し、目的のデータベースとストアド プロシージャを参照するようにします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの作成](create-a-stored-procedure.md)   
 [ストアド プロシージャの変更](modify-a-stored-procedure.md)   
 [ストアド プロシージャの削除](delete-a-stored-procedure.md)   
 [ストアド プロシージャの名前の変更](rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)   
 [OBJECT_ID &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-id-transact-sql)  
  
  
