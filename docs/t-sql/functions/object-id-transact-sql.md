---
title: "OBJECT_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_ID
- OBJECT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], IDs
- identification numbers [SQL Server], database objects
- checking object exists
- IDs [SQL Server], database objects
- OBJECT_ID function
- database objects [SQL Server], IDs
- displaying object IDs
- viewing object IDs
- verifying object exists
ms.assetid: f89286db-440f-4218-a828-30881ce3077a
caps.latest.revision: 63
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a612928c3a30b48d3dc8e1dedd4375ca564555d8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="objectid-transact-sql"></a>OBJECT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  スキーマ スコープ オブジェクトのデータベース オブジェクト ID 番号を返します。  
  
> [!IMPORTANT]  
>  DDL トリガーなど、スキーマ スコープ オブジェクトでないオブジェクトは、OBJECT_ID を使用して照会できません。 ないオブジェクトに対して、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューには、適切なカタログ ビューをクエリすることによって、オブジェクト id 番号を取得します。 たとえば、DDL トリガーのオブジェクト id 番号を返す、次のように使用します。`SELECT OBJECT_ID FROM sys.triggers WHERE name = 'DatabaseTriggerLog``'`です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
OBJECT_ID ( '[ database_name . [ schema_name ] . | schema_name . ]   
  object_name' [ ,'object_type' ] )  
```  
  
## <a name="arguments"></a>引数  
 **'** *object_name* **'**  
 使用するオブジェクトを指定します。 *object_name*か**varchar**または**nvarchar**です。 場合*object_name*は**varchar**、暗黙的に変換されます**nvarchar**です。 データベース名とスキーマ名の指定は省略可能です。  
  
 **'** *object_type* **'**  
 スキーマ スコープのオブジェクトの種類を指定します。 *object_type*か**varchar**または**nvarchar**です。 場合*object_type*は**varchar**、暗黙的に変換されます**nvarchar**です。 オブジェクトの種類の一覧は、次を参照してください。、**型**内の列[sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="exceptions"></a>例外  
 空間インデックスに対して、OBJECT_ID は NULL を返します。  
  
 エラーが発生した場合は NULL を返します。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECT_ID など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 システム関数のパラメーターを指定しない場合は、現在のデータベース、ホスト コンピューター、サーバー ユーザー、またはデータベース ユーザーを指定したと見なされます。 組み込み関数の後には、必ずかっこが必要です。  
  
 一時テーブル名を指定すると、データベース名でなければなりません一時テーブル名の前に、現在のデータベースがない限り、 **tempdb**です。 たとえば、 `SELECT OBJECT_ID('tempdb..#mytemptable')`のようにします。  
  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 詳細については、次を参照してください。[式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)と[場所 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-object-id-for-a-specified-object"></a>A. 指定したオブジェクトのオブジェクト ID を返す  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `Production.WorkOrder` テーブルのオブジェクト ID を返します。  
  
```  
USE master;  
GO  
SELECT OBJECT_ID(N'AdventureWorks2012.Production.WorkOrder') AS 'Object ID';  
GO  
```  
  
### <a name="b-verifying-that-an-object-exists"></a>B. オブジェクトが存在することを確認する  
 次の例では、指定したテーブルにオブジェクト ID があることを確認して、テーブルが存在するかどうかをチェックします。 テーブルが存在する場合は、削除されます。 テーブルが存在しない場合、`DROP TABLE` ステートメントは実行されません。  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'dbo.AWBuildVersion', N'U') IS NOT NULL  
DROP TABLE dbo.AWBuildVersion;  
GO  
```  
  
### <a name="c-using-objectid-to-specify-the-value-of-a-system-function-parameter"></a>C. OBJECT_ID を使用して、システム関数パラメーターの値を指定する  
 次の例は、すべてのインデックスとパーティションの情報を返します、`Person.Address`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースを使用して、 [sys.dm_db_index_operational_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)関数。  
  
> [!IMPORTANT]  
>  使用する場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]関数 DB_ID および OBJECT_ID が、パラメーター値を返すは常に有効な ID が返されることを確認してください。 データベースまたはオブジェクト名が存在しないか、スペルが間違っていることが原因で見つからない場合は、両方の関数で NULL が返されます。 **Sys.dm_db_index_operational_stats**関数は、この値は、すべてのデータベースまたはすべてのオブジェクトを指定するワイルドカード値として NULL を解釈します。 これによって意図しない操作が実行される可能性があるので、この例では安全な方法を使用してデータベース ID とオブジェクト ID を特定します。  
  
```  
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-returning-the-object-id-for-a-specified-object"></a>D: が指定されたオブジェクトのオブジェクト ID を返す  
 次の例では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベース内の `FactFinance` テーブルのオブジェクト ID を返します。  
  
```  
SELECT OBJECT_ID(AdventureWorksPDW2012.dbo.FactFinance') AS 'Object ID';  
```  
  
## <a name="see-also"></a>参照  
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.dm_db_index_operational_stats & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-name-transact-sql.md)  
  
  


