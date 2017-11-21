---
title: "SET QUOTED_IDENTIFIER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/03/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUOTED_IDENTIFIER_TSQL
- SET_QUOTED_IDENTIFIER_TSQL
- SET QUOTED_IDENTIFIER
- QUOTED_IDENTIFIER
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- identifiers [SQL Server], delimited
- QUOTED_IDENTIFIER option
- quoted identifiers
- ISO delimited identifiers rules
- SET QUOTED_IDENTIFIER statement
ms.assetid: 10f66b71-9241-4a3a-9292-455ae7252565
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c6ba7962a9721dad3c3f043f960c72f718f6062
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-quotedidentifier-transact-sql"></a>SET QUOTED_IDENTIFIER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対して、識別子とリテラル文字列を区切る引用符に関して、ISO 規格に従うことを指定します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] の予約済みキーワードを指定する場合や、[!INCLUDE[tsql](../../includes/tsql-md.md)] の構文規則で通常は識別子として許可されない文字がある場合は、二重引用符で識別子を区切ることができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET QUOTED_IDENTIFIER { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET QUOTED_IDENTIFIER ON   
```  
  
## <a name="remarks"></a>解説  
 SET QUOTED_IDENTIFIER が ON の場合は、識別子を二重引用符で区切ることができます。リテラルは単一引用符で区切る必要があります。 SET QUOTED_IDENTIFIER が OFF の場合、識別子を引用符で区切ることはできません。識別子に関しては [!INCLUDE[tsql](../../includes/tsql-md.md)] のすべての規則に従う必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。 リテラルは単一引用符と二重引用符のどちらで区切ることもできます。  
  
 SET QUOTED_IDENTIFIER が ON (既定値) の場合、二重引用符で区切られた文字列はすべてオブジェクト識別子として解釈されます。 したがって、引用符で区切られた識別子は、識別子に関する [!INCLUDE[tsql](../../includes/tsql-md.md)] の規則に従う必要はありません。 このような識別子では予約済みキーワードを使用でき、通常は [!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子として許可されない文字を含めることもできます。 リテラル文字列式を二重引用符で区切ることはできません。リテラル文字列を区切るには、単一引用符を使用する必要があります。 場合、単一引用符 (**'**) 一部であること、リテラルの文字列の 2 つの単一引用符で表すことが (**"**)。 データベース内のオブジェクト名に対して予約済みキーワードを使用する場合は、SET QUOTED_IDENTIFIER を ON にする必要があります。  
  
 SET QUOTED_IDENTIFIER が OFF (既定値) の場合、式の内部のリテラル文字列は、単一引用符と二重引用符のどちらで区切ることもできます。 リテラル文字列を二重引用符で区切る場合は、文字列の内部でアポストロフィなどの埋め込み単一引用符を使用できます。  
  
 計算列やインデックス付きビューのインデックスを作成または操作するときには、SET QUOTED_IDENTIFIER を ON に設定する必要があります。 SET QUOTED_IDENTIFIER が OFF の場合、計算列上にインデックスが設定されているテーブルやインデックス付きビューに対して CREATE、UPDATE、INSERT、および DELETE ステートメントを実行しようとすると失敗します。 計算列でインデックス付きビューとインデックスを持つ必要な SET オプション設定に関する詳細についてを参照してください「の考慮事項とする SET ステートメントの使用」 [SET ステートメント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statements-transact-sql.md).  
  
 フィルター選択されたインデックスを作成する場合は、SET QUOTED_IDENTIFIER を ON に設定する必要があります。  
  
 XML データ型のメソッドを呼び出す場合は、SET QUOTED_IDENTIFIER を ON に設定する必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに、ON に QUOTED_IDENTIFIER を自動的に設定します。 これは、ODBC データ ソース、ODBC 接続属性、または OLE DB 接続プロパティを使って構成できます。 DB-Library アプリケーションからの接続に対しては、SET QUOTED_IDENTIFIER は既定で OFF に設定されています。  
  
 テーブルの作成時に QUOTED IDENTIFIER オプションが OFF に設定されていても、作成されるテーブルのメタデータでは、このオプションは常に ON として格納されます。  
  
 ストアド プロシージャを作成すると、SET QUOTED_IDENTIFIER と SET ANSI_NULLS の設定が取得され、以降そのストアド プロシージャを呼び出すときに使用されます。  
  
 SET QUOTED_IDENTIFIER をストアド プロシージャの内部で実行する場合、この設定は変更されません。  
  
 SET ANSI_DEFAULTS が ON の場合、SET QUOTED_IDENTIFIER は有効になります。  
  
 SET QUOTED_IDENTIFIER は、ALTER DATABASE の QUOTED_IDENTIFIER 設定にも対応します。 データベースの設定の詳細については、次を参照してください。 [ALTER DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
 SET QUOTED_IDENTIFIER は解析時では、有効で、のみに影響を与える解析では、クエリを実行できません。  
  
 最上位のアドホック バッチの解析を開始 QUOTED_IDENTIFIER のセッションの現在の設定を使用します。  バッチの解析し出現するすべての SET QUOTED_IDENTIFIER が、その時点から解析動作を変更し、そのセッションの設定を保存します。  したがって、バッチを解析して実行すると、セッションの QUOTED_IDENTIFER 設定はバッチで SET QUOTED_IDENTIFIER の最後に見つかったに従って設定されます。  
 ストアド プロシージャ内の静的な SQL を解析するには、ストアド プロシージャを変更または作成したバッチの QUOTED_IDENTIFIER 設定を有効に使用されます。  静的 SQL としてストアド プロシージャの本体に書き込まれたときは、SET QUOTED_IDENTIFIER を指定しても効果はありません。  
  
 Sp_executesql または exec() を使用して入れ子になったバッチの解析を開始、セッションの QUOTED_IDENTIFIER 設定を使用します。  文字列の解析 ストアド プロシージャ内の入れ子になったバッチがある場合は、ストアド プロシージャの QUOTED_IDENTIFIER 設定を使ってを起動します。  入れ子になったバッチが解析されると、出現するすべての SET QUOTED_IDENTIFIER は、その時点から解析動作を変更するが、セッションの QUOTED_IDENTIFIER 設定は更新されません。  
  
 角かっこを使用して**[**と**]**識別子を区切るために、QUOTED_IDENTIFIER 設定の影響を受けません。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @QUOTED_IDENTIFIER VARCHAR(3) = 'OFF';  
IF ( (256 & @@OPTIONS) = 256 ) SET @QUOTED_IDENTIFIER = 'ON';  
SELECT @QUOTED_IDENTIFIER AS QUOTED_IDENTIFIER;  
  
```  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-quoted-identifier-setting-and-reserved-word-object-names"></a>A. 引用符で囲まれた識別子の設定と、予約済みキーワードを用いたオブジェクト名を使用する  
 次の例では、予約済みキーワード名を含むオブジェクト名を作成して使用するときに、`SET QUOTED_IDENTIFIER` の設定を `ON` にして、テーブル名のキーワードを二重引用符で区切る必要があることを示しています。  
  
```  
SET QUOTED_IDENTIFIER OFF  
GO  
-- An attempt to create a table with a reserved keyword as a name  
-- should fail.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Will succeed.  
CREATE TABLE "select" ("identity" INT IDENTITY NOT NULL, "order" INT NOT NULL);  
GO  
  
SELECT "identity","order"   
FROM "select"  
ORDER BY "order";  
GO  
  
DROP TABLE "SELECT";  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
### <a name="b-using-the-quoted-identifier-setting-with-single-and-double-quotation-marks"></a>B. 引用符で囲まれた識別子の設定と、単一引用符および二重引用符を使用する  
 次の例では、`SET QUOTED_IDENTIFIER` を `ON` に設定した場合と `OFF` に設定した場合のそれぞれに対して、文字列式で単一引用符と二重引用符を使用する方法を示しています。  
  
```  
SET QUOTED_IDENTIFIER OFF;  
GO  
USE AdventureWorks2012;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'Test')  
   DROP TABLE dbo.Test;  
GO  
USE AdventureWorks2012;  
CREATE TABLE dbo.Test (ID INT, String VARCHAR(30)) ;  
GO  
  
-- Literal strings can be in single or double quotation marks.  
INSERT INTO dbo.Test VALUES (1, "'Text in single quotes'");  
INSERT INTO dbo.Test VALUES (2, '''Text in single quotes''');  
INSERT INTO dbo.Test VALUES (3, 'Text with 2 '''' single quotes');  
INSERT INTO dbo.Test VALUES (4, '"Text in double quotes"');  
INSERT INTO dbo.Test VALUES (5, """Text in double quotes""");  
INSERT INTO dbo.Test VALUES (6, "Text with 2 """" double quotes");  
GO  
  
SET QUOTED_IDENTIFIER ON;  
GO  
  
-- Strings inside double quotation marks are now treated   
-- as object names, so they cannot be used for literals.  
INSERT INTO dbo."Test" VALUES (7, 'Text with a single '' quote');  
GO  
  
-- Object identifiers do not have to be in double quotation marks  
-- if they are not reserved keywords.  
SELECT ID, String   
FROM dbo.Test;  
GO  
  
DROP TABLE dbo.Test;  
GO  
  
SET QUOTED_IDENTIFIER OFF;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ID          String 
 ----------- ------------------------------ 
 1           'Text in single quotes' 
 2           'Text in single quotes' 
 3           Text with 2 '' single quotes 
 4           "Text in double quotes" 
 5           "Text in double quotes" 
 6           Text with 2 "" double quotes 
 7           Text with a single ' quote
 ```  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET ansi_defaults] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [sp_rename & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)  
  
  

