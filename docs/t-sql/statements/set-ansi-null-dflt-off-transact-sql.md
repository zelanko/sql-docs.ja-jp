---
title: "セット ANSI_NULL_DFLT_OFF (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ANSI_NULL_DFLT_OFF_TSQL
- ANSI_NULL_DFLT_OFF
- SET ANSI_NULL_DFLT_OFF
- SET_ANSI_NULL_DFLT_OFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- default nullability
- ANSI_NULL_DFLT_OFF option
- null values [SQL Server], overriding
- overriding default nullability
- SET ANSI_NULL_DFLT_OFF statement
ms.assetid: 8ed5c512-f5de-4741-a18a-de85a3041295
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1eeb95a4fdeb8e0db5ed08f3f5728a38f512bc2f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldfltoff-transact-sql"></a>SET ANSI_NULL_DFLT_OFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースの ANSI null default オプションが、新しい列の既定の null 値をオーバーライドするセッションの動作を変更**true**です。 ANSI null default の値の設定の詳細については、次を参照してください。 [ALTER DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_OFF { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_OFF OFF  
```  
  
## <a name="remarks"></a>解説  
 この設定は、新しい列に対する NULL 値の許容にのみ影響を与えます。また、この影響が生じるのは、CREATE TABLE および ALTER TABLE ステートメントで、列に対して NULL 値の許容が設定されていない場合です。 既定では、SET ANSI_NULL_DFLT_OFF が ON の場合、ALTER TABLE ステートメントと CREATE TABLE ステートメントで作成される新しい列は、NULL 値を許可するかどうかを明示的に指定しない限り NOT NULL になります。 SET ANSI_NULL_DFLT_OFF は、NULL または NOT NULL を明示して作成した列には影響しません。  
  
 SET ANSI_NULL_DFLT_OFF と SET ANSI_NULL_DFLT_ON の両方を同時に ON に設定することはできません。 いずれかのオプションを ON に設定すると、もう一方のオプションは OFF に設定されます。 つまり、SET ANSI_NULL_DFLT_OFF と SET ANSI_NULL_DFLT_ON のいずれか一方を ON に設定するか、または両方を OFF に設定することだけが可能です。 いずれかのオプションを ON に設定した場合、その設定 (SET ANSI_NULL_DFLT_OFF または SET ANSI_NULL_DFLT_ON) が有効になります。 両方のオプションが OFF に設定されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にある is_ansi_null_default_on 列の値を使用して、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを、NULL 値の許容に関する設定が異なっているデータベースで使用する場合、このスクリプトによる動作の信頼性を高めるには、CREATE TABLE ステートメントと ALTER TABLE ステートメントで常に NULL または NOT NULL を指定することをお勧めします。  
  
 SET ANSI_NULL_DFLT_OFF は、解析時ではなく実行時に設定されます。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @ANSI_NULL_DFLT_OFF VARCHAR(3) = 'OFF';  
IF ( (2048 & @@OPTIONS) = 2048 ) SET @ANSI_NULL_DFLT_OFF = 'ON';  
SELECT @ANSI_NULL_DFLT_OFF AS ANSI_NULL_DFLT_OFF;  
  
```  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、Ansi Null Default データベース オプションに 2 種類の設定を使用した場合の `SET ANSI_NULL_DFLT_OFF` の効果を示します。  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Set the 'ANSI null default' database option to true by executing   
-- ALTER DATABASE.  
GO  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT);  
GO  
-- NULL INSERT should succeed.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t2.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL INSERT should fail.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t3.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t3 (a TINYINT) ;  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- This illustrates the effect of having both the database  
-- option and SET option disabled.  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t4.  
CREATE TABLE t4 (a tinyint) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t4 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t5.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t5 (a tinyint);  
GO   
-- NULL insert should fail.  
INSERT INTO t5 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t6.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t6 (a tinyint);   
GO   
-- NULL insert should fail.  
INSERT INTO t6 (a) VALUES (null);  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1, t2, t3, t4, t5, t6;  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [セット ANSI_NULL_DFLT_ON & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)  
  
  
