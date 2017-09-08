---
title: "作業を開始してください.終了 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN
- BEGIN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- BEGIN statement
- control-of-flow language [SQL Server], BEGIN...END statement
- BEGIN...END keyword
- grouping statements, BEGIN...END statement
- executing Transact-SQL statements together [SQL Server]
- statements [SQL Server], grouping
ms.assetid: fc2c7f76-f1f9-4f91-beef-bc8ef0da2feb
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1045a89eb41a7f84b4b2a2a5cbe305c67e776fb1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="beginend-transact-sql"></a>BEGIN...END (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  一連を囲む[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントようにのグループ[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを実行することができます。 BEGIN と END はフロー制御言語のキーワードです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
BEGIN  
    { sql_statement | statement_block }   
END  
```  
  
## <a name="arguments"></a>引数  
 { *sql_statement* | *statement_block* }  
 有効な 1 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、またはステートメント ブロックで定義したステートメントのグループを指定します。  
  
## <a name="remarks"></a>解説  
 BEGIN...END ブロックは入れ子にできます。  
  
 すべて[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは内では、開始しています.終了ブロックする場合に、特定[!INCLUDE[tsql](../../includes/tsql-md.md)]同じバッチまたはステートメント ブロック内で一緒にグループ化できないステートメントもする必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、`BEGIN` と `END` を使用して、まとめて実行する一連の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを定義します。 `BEGIN...END` ブロックが指定されていない場合、両方の `ROLLBACK TRANSACTION` ステートメントが実行され、両方の `PRINT` メッセージが返されます。  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
GO  
IF @@TRANCOUNT = 0  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM Person.Person WHERE LastName = 'Adams';  
    ROLLBACK TRANSACTION;  
    PRINT N'Rolling back the transaction two times would cause an error.';  
END;  
ROLLBACK TRANSACTION;  
PRINT N'Rolled back the transaction.';  
GO  
/*  
Rolled back the transaction.  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、`BEGIN`と`END`一連の定義[!INCLUDE[DWsql](../../includes/dwsql-md.md)]同時に実行されるステートメントです。 場合、`BEGIN...END`ブロックが含まれていない、次の例は、連続するループになります。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [フロー制御言語 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [END & #40 です。作業を開始してください.終了"&"#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/end-begin-end-transact-sql.md)  
  
  



