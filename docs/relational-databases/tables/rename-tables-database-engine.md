---
title: "テーブル名の変更 (データベース エンジン) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d65c475509d57577f691e656157c7754c7d8549f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="rename-tables-database-engine"></a>テーブル名の変更 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してテーブルの名前を変更することができます。  
  
> [!CAUTION]  
>  テーブル名の変更については、十分に検討してください。 そのテーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムが存在する場合、テーブル名を変更すると、各オブジェクトが無効になります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **テーブル名を変更する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 テーブル名を変更しても、そのテーブルに対する参照の名前は自動的には変更されません。 名前を変更したテーブルを参照しているオブジェクトに対しては、手動で変更を加える必要があります。 たとえば、テーブルの名前を変更するとき、そのテーブルがトリガーで参照されている場合は、新しいテーブル名が反映されるようにトリガーに変更を加える必要があります。 オブジェクトの名前を変更する前には、 [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) を使ってテーブルの従属関係を一覧表示できます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-rename-a-table"></a>テーブル名を変更するには  
  
1.  オブジェクト エクスプローラーで、名前を変更するテーブルを右クリックし、ショートカット メニューの **[デザイン]** をクリックします。  
  
2.  **[表示]** メニューの **[プロパティ]**をクリックします。  
  
3.  **[プロパティ]** ウィンドウの **[オブジェクト名]** ボックスに、テーブルの新しい名前を入力します。  
  
4.  この操作を取り消すには、このフィールド外に移動する前に Esc キーを押します。  
  
5.  **ファイル** メニューの **table name***の保存*を選びます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-rename-a-table"></a>テーブル名を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例では、 `SalesTerritory` スキーマの `SalesTerr` テーブルの名前を `Sales` に変更します。 次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 その他の例については、「[sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)」を参照してください。  
  
  

