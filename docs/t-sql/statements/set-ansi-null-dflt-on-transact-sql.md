---
title: "セット ANSI_NULL_DFLT_ON (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ANSI_NULL_DFLT_ON
- ANSI_NULL_DFLT_ON_TSQL
- SET ANSI_NULL_DFLT_ON
- SET_ANSI_NULL_DFLT_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULL_DFLT_ON statement
- ANSI_NULL_DFLT_ON option
- default nullability
- null values [SQL Server], overriding
- overriding default nullability
ms.assetid: 8c925924-a466-4c8b-aeb2-7e0d341f32db
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17bd1817d8f7f04401f49f9a02562bcf577c9088
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldflton-transact-sql"></a>SET ANSI_NULL_DFLT_ON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  新しい列の既定の null 値をオーバーライドするセッションの動作を変更してときに、 **ANSI null default**オプションを使用しないデータベースが**false**です。 値の設定の詳細については**ANSI null default**を参照してください[ALTER DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_ON {ON | OFF}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_ON ON;  
```  
  
## <a name="remarks"></a>解説  
 この設定は、新しい列に対する NULL 値の許容にのみ影響を与えます。また、この影響が生じるのは、CREATE TABLE および ALTER TABLE ステートメントで、列に対して NULL 値の許容が設定されていない場合です。 SET ANSI_NULL_DFLT_ON が ON の場合、ALTER TABLE ステートメントと CREATE TABLE ステートメントを使用して作成した新しい列では、明示的に指定しない限り NULL 値が許容されます。 NULL または NOT NULL を明示的に指定して作成した列に対して、SET ANSI_NULL_DFLT_ON は影響しません。  
  
 SET ANSI_NULL_DFLT_OFF と SET ANSI_NULL_DFLT_ON の両方を同時に ON に設定することはできません。 いずれかのオプションを ON に設定すると、もう一方のオプションは OFF に設定されます。 したがって、SET ANSI_NULL_DFLT_OFF と SET ANSI_NULL_DFLT_ON はいずれかを ON に設定するか、両方を OFF に設定することだけが可能です。 いずれかのオプションを ON に設定した場合、その設定 (SET ANSI_NULL_DFLT_OFF または SET ANSI_NULL_DFLT_ON) が有効になります。 両方のオプションが OFF に設定されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の値を使用して、 **is_ansi_null_default_on**内の列、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 動作の信頼性を高めるため[!INCLUDE[tsql](../../includes/tsql-md.md)]NULL を指定するか、CREATE TABLE および ALTER TABLE ステートメントで NOT NULL の方が優れている異なる null 許容属性の設定を持つデータベースで使用されているスクリプト、します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を ON に接続するときに ANSI_NULL_DFLT_ON を自動的に設定します。 DB-Library アプリケーションからの接続に対して、既定では SET ANSI_NULL_DFLT_ON は OFF に設定されています。  
  
 SET ANSI_DEFAULTS が ON の場合、SET ANSI_NULL_DFLT_ON は有効になります。  
  
 SET ANSI_NULL_DFLT_ON は、解析時ではなく実行時に設定されます。  
  
 SELECT INTO ステートメントを使用してテーブルを作成した場合は、SET ANSI_NULL_DFLT_ON の設定は適用されません。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @ANSI_NULL_DFLT_ON VARCHAR(3) = 'OFF';  
IF ( (1024 & @@OPTIONS) = 1024 ) SET @ANSI_NULL_DFLT_ON = 'ON';  
SELECT @ANSI_NULL_DFLT_ON AS ANSI_NULL_DFLT_ON;  
  
```  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例の効果を示します`SET ANSI_NULL_DFLT_ON`両方の設定を使用、 **ANSI null default**データベース オプション。  
  
```  
USE AdventureWorks2012;  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON  
-- has an effect when the 'ANSI null default' for the database is false.  
-- Set the 'ANSI null default' database option to false by executing  
-- ALTER DATABASE.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t2.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL insert should succeed.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t3.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t3 (a TINYINT);  
GO  
-- NULL insert should fail.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON   
-- has no effect when the 'ANSI null default' for the database is true.  
-- Set the 'ANSI null default' database option to true.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON  
GO  
  
-- Create table t4.  
CREATE TABLE t4 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t4 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t5.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t5 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t5 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t6.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t6 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t6 (a) VALUES (NULL);  
GO  
  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1,t2,t3,t4,t5,t6;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET ansi_defaults] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [セット ANSI_NULL_DFLT_OFF & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)  
  
  
