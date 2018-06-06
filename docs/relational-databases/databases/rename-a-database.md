---
title: データベースの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 26021dfab23092edbfdea5ec94e114301695f044
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34582484"
---
# <a name="rename-a-database"></a>データベースの名前変更
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ユーザー定義のデータベースの名前を変更する方法について説明します。 識別子の規則に従っていれば、データベースの名前にはいずれの文字も使用できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **以下を使用してデータベースの名前を変更するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After renaming a database](#FollowUp)  

> [!NOTE]
> Azure SQL Database でデータベースの名前を変更するには、[ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md) ステートメントを使用します。 Azure SQL Data Warehouse または Parallel Data Warehouse でデータベースの名前を変更するには、[RENAME (Transact-SQL)](../../t-sql/statements/rename-transact-sql.md) ステートメントを使用します。
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   システム データベースの名前は変更できません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データベースに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-rename-a-database"></a>データベースの名前を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  データベースを使用している人がいないことを確認し、 [データベースをシングル ユーザー モードに設定します](../../relational-databases/databases/set-a-database-to-single-user-mode.md)。  
  
3.  **[データベース]** を展開し、名前を変更するデータベースを右クリックして、 **[名前の変更]** をクリックします。  
  
4.  新しいデータベース名を入力し、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-rename-a-database"></a>データベースの名前を変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 `AdventureWorks2012` データベースの名前を `Northwind`に変更します。  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="FollowUp"></a> 補足情報: データベースの名前を変更した後  
 データベースの名前を変更した後は、 **master** データベースをバックアップします。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [データベース識別子](../../relational-databases/databases/database-identifiers.md)  
  
  
