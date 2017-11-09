---
title: "名前の変更 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/13/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
caps.latest.revision: 15
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d58470957ab58085ddd6a733cf30dbc77ce7439a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="rename-transact-sql"></a>名前の変更 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  内のユーザーが作成したテーブルの名前を変更[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 ユーザーが作成したテーブルまたはデータベースの名前を変更[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
> [!NOTE]  
>  データベースの名前を変更する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または[!INCLUDE[ssSDS](../../includes/sssds-md.md)]ストアド プロシージャを使用して[sp_renamedb & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md).  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
-- Rename a table.  
RENAME OBJECT [ :: ]  [ [ database_name .  [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name  
[;]  
  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- Rename a table  
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name  
[;]  
  
-- Rename a database  
RENAME DATABASE [::] database_name TO new_database_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 オブジェクト [::] の名前変更します。   
          [*database_name*です。 [ *schema_name* ] です。 ] |[ *schema_name*です。 ]*table_name* TO *new_table_name*  
 **適用対象:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 ユーザー定義テーブルの名前を変更します。 1 つの 2 部、または 3 部構成の名前と名前を変更するテーブルを指定します。    新しいテーブルを指定して*new_table_name*を 1 つの要素名として。  
  
 データベース [::] の名前を変更します。   
          [ *database_name* TO *new_database_name*  
 **適用されます。**  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 ユーザー定義のデータベースの名前を変更*database_name*に*new_database_name*です。  これらのいずれかに、データベースの名前を変更することはできません[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベース名に予約されています。  
  
-   master  
  
-   model  
  
-   msdb  
  
-   tempdb  
  
-   pdwtempdb1  
  
-   pdwtempdb2  
  
-   DWConfiguration  
  
-   DWDiagnostics  
  
-   DWQueue  
  
## <a name="permissions"></a>Permissions  
 このコマンドを実行するには、このアクセス許可が必要です。  
  
-   **ALTER**テーブルに対する権限  
   
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
  
### <a name="cannot-rename-an-external-table-indexes-or-views"></a>外部テーブル、インデックス、またはビューの名前を変更できません。
外部テーブル、インデックス、またはビューの名前を変更することはできません。 この名前を変更するには、代わりには、外部テーブル、インデックス、またはビューを削除し、し、新しい名前を指定して再作成します。

### <a name="cannot-rename-a-table-in-use"></a>使用中のテーブルの名前を変更できません。  
 使用中に、テーブルまたはデータベースを変更することはできません。 テーブルの名前を変更するには、テーブルに排他ロックが必要です。 テーブルを使用している場合は、テーブルを使用しているセッションを終了する必要があります。 セッションを終了するには、KILL コマンドを使用することができます。 使用 KILL ので注意して、セッションが終了すると、コミットされていない作業はロールバックされます。 SQL データ ウェアハウス内のセッションには、'SID' が付きます。 KILL コマンドを呼び出すときに、これとセッション数を含める必要があります。 この例では、アクティブまたはアイドル状態のセッションの一覧を表示し、'SID1234' のセッションを終了します。  
  
### <a name="views-are-not-updated"></a>ビューは更新されません。  
 データベースの名前を変更するには、ときに、以前のデータベース名を使用するすべてのビューは無効になります。 これは、データベースの内外両方のビューに適用されます。 たとえば、Sales データベースの名前を変更する場合、ビューを含む`SELECT * FROM Sales.dbo.table1`が無効になります。 これを解決するのには、ビューでは、3 部構成の名前は使用しないでくださいするか、新しいデータベース名を参照するビューを更新します。  
  
 テーブルの名前を変更するには、新しいテーブルの名前を参照するビューは更新されません。 ビューごとに、元のテーブル名を参照すると、データベースの内外は無効になります。 これを解決するには、新しいテーブルの名前を参照するには、各ビューを更新することができます。  
  
## <a name="locking"></a>ロック  
 テーブルの名前を変更すると、データベース オブジェクトに対する共有ロックのスキーマ オブジェクトの共有ロックとテーブルに対する排他ロックが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-rename-a-database"></a>A. データベースの名前変更します。  
 **適用対象:** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]のみ    
  
 この例では、AdWorks2 を AdWorks ユーザー定義のデータベースを変更します。  
  
```  
-- Rename the user defined database AdWorks  
RENAME DATABASE AdWorks to AdWorks2;  
  
```  
  
 テーブルの名前を変更するには、新しいテーブルの名前を参照するすべてのオブジェクトと、テーブルに関連付けられたプロパティが更新されます。 たとえば、テーブルの定義、インデックス、制約、およびアクセス許可が更新されます。 ビューは更新されません。  
  
### <a name="b-rename-a-table"></a>B. テーブル名の変更  
 **適用対象:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 この例では、Customer1 を Customer テーブルを変更します。  
  
```  
-- Rename the customer table  
RENAME OBJECT Customer TO Customer1;  
  
RENAME OBJECT mydb.dbo.Customer TO Customer1;  
```  
  
 テーブルの名前を変更するには、新しいテーブルの名前を参照するすべてのオブジェクトと、テーブルに関連付けられたプロパティが更新されます。 たとえば、テーブルの定義、インデックス、制約、およびアクセス許可が更新されます。 ビューは更新されません。  
   
  
### <a name="c-move-a-table-to-a-different-schema"></a>C. 別のスキーマにテーブルを移動します。  
 **適用対象:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 ユーザーの意図が別のスキーマにオブジェクトを移動する場合を使用して[ALTER SCHEMA & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-schema-transact-sql.md). たとえば、テーブルの項目は、製品スキーマから、dbo スキーマにこの移動します。  
  
```  
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;  
```  
  
### <a name="d-terminate-sessions-before-renaming-a-table"></a>D. テーブルの名前を変更する前にセッションを終了します  
 **適用対象:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 ことが重要の使用中に、テーブルを変更することはできないことに注意してください。 テーブルの名前を変更するには、テーブルに排他ロックが必要です。 テーブルを使用している場合は、テーブルを使用してセッションを終了する必要があります。 セッションを終了するには、KILL コマンドを使用することができます。 使用 KILL ので注意して、セッションが終了すると、コミットされていない作業はロールバックされます。 SQL データ ウェアハウス内のセッションには、'SID' が付きます。 KILL コマンドを呼び出すときに、これとセッション数を含める必要があります。 この例では、アクティブまたはアイドル状態のセッションの一覧を表示し、'SID1234' のセッションを終了します。  
  
```  
-- View a list of the current sessions  
SELECT session_id, login_name, status   
FROM sys.dm_pdw_exec_sessions   
WHERE status='Active' OR status='Idle';  
  
-- Terminate a session using the session_id.  
KILL 'SID1234';  
```  
  
  

