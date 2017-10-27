---
title: "終了 (BEGIN.終了) (TRANSACT-SQL) |Microsoft ドキュメント"
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
- END
- END_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- END keyword
- BEGIN...END keyword
- END (BEGIN...END) keyword
ms.assetid: 354c4935-1375-4141-8195-61326662f4d2
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f7a3c01fd0a038d226edcf605774c3a75f49b4f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="end-beginend-transact-sql"></a>END (BEGIN...END) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  一連を囲む[!INCLUDE[tsql](../../includes/tsql-md.md)]グループとして実行されるステートメントです。 BEGIN...END ブロックは入れ子にできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
BEGIN   
     { sql_statement | statement_block }   
END   
```  
  
## <a name="arguments"></a>引数  
 { *sql_statement*| *statement_block*}  
 有効な[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメント ブロックで定義されているグループ化します。 ステートメント ブロック (バッチ) を定義するのには、BEGIN と END は、フロー制御言語キーワードを使用します。 すべて[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは内では、開始しています.終了ブロックする場合に、特定[!INCLUDE[tsql](../../includes/tsql-md.md)]同じバッチ (ステートメント ブロック) 内で一緒にグループ化できないステートメントもする必要があります。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
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
 [作業を開始してください.END &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [フロー制御言語 &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ELSE &#40; IF しています.ELSE &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/else-if-else-transact-sql.md)   
 [もし。。。ELSE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  



