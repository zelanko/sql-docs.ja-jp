---
title: "(ワイルドカード - 一致する文字列) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Match
- wildcard
- '[ ]'
- '[_]_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[ ] (wildcard - character(s) to match)'
ms.assetid: 57817576-0bf1-49ed-b05d-fac27e8fed7a
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 04fcf0d9e76db380430bfbf4c4ed6e5fadf14afb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="--wildcard---characters-to-match-transact-sql"></a>\[\] (ワイルドカード - 一致する文字列) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した範囲または角かっこの間で指定されているセット内の任意の 1 文字と一致する`[ ]`です。 これらのワイルドカード文字をパターンに一致するなどを含む文字列比較で使用できます`LIKE`と`PATINDEX`です。  
  
## <a name="examples"></a>使用例  
### <a name="a-simple-example"></a>A: 簡単な例   
次の例は、文字で始まるの名前を返します`m`です。 `[n-z]`2 番目の文字が、範囲内でどこかにする必要がありますを指定します`n`に`z`です。 ワイルドカードのパーセント記号`%`の先頭 3 文字またはない任意の文字が許可されています。 `model`と`msdb`データベースは、この条件を満たしています。 `master`データベースがないし、結果セットから除外されます。
 
```sql
SELECT name FROM sys.databases
WHERE name LIKE 'm[n-z]%';
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]  

```
name
-----
model
msdb
```   
 インストールされている該当するデータベースを追加するがあります。


### <a name="b-more-complex-example"></a>B: より複雑な例   
 次の例では、4 桁の郵便番号付きの住所を持つ [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] のすべての従業員の ID と名前を [] 演算子を使用して検索します。  
  
```sql  
-- Uses AdventureWorks  
  
SELECT e.BusinessEntityID, p.FirstName, p.LastName, a.PostalCode  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p ON e.BusinessEntityID = p.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS ea ON e.BusinessEntityID = ea.BusinessEntityID  
INNER JOIN Person.Address AS a ON a.AddressID = ea.AddressID  
WHERE a.PostalCode LIKE '[0-9][0-9][0-9][0-9]';  
```  
  
 Here is the result set:  
  
```  
EmployeeID      FirstName      LastName      PostalCode  
----------      ---------      ---------     ----------  
290             Lynn           Tsoflias      3000  
```  



  
## <a name="see-also"></a>参照  
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)   
  [% &#40;です。ワイルドカード - 文字 &#40; s &#41;一致と #41 です。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
 [& #91、^ (& a) #93 です。&#40;です。ワイルドカード - 文字 &#40; s &#41;一致と #41 です。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
 [\_&#40;です。ワイルドカード - 一致する 1 文字 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
    
  
