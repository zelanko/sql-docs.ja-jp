---
title: "_ (ワイルドカード - 一致する 1 文字) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- Match
- wildcard
- _TSQL
- Match One
- _
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 96a529dd77d0d76ecf8fe85dba2d211c71b4c398
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (ワイルドカード - 1 文字に一致) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

など、パターン マッチを伴う文字列比較操作で単一の文字をアンダー スコア文字 _ を使用して`LIKE`と`PATINDEX`です。  
  
## <a name="examples"></a>使用例  

## <a name="a-simple-example"></a>A: 簡単な例   

次の例では、すべてのデータベースの文字で始まる名前を返します`m`文字があると`d`3 番目の文字として。 アンダー スコア文字では、名前の 2 番目の文字が任意の文字にできることを指定します。 `model`と`msdb`データベースは、この条件を満たしています。 `master`データベースはありません。

```sql
SELECT name FROM sys.databases
WHERE name LIKE 'm_d%';
```   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-----
model
msdb
```   
この条件を満たすデータベースを追加するがあります。

複数のアンダー スコアを使用すると、複数の文字を表します。 変更、`LIKE`を 2 つのアンダー スコアを含める条件`'m__%`結果で、master データベースが含まれています。

### <a name="b-more-complex-example"></a>B: より複雑な例
 次の例では、_ 演算子が、内のすべてのユーザーの検索を使用して、`Person`で終わる 3 文字の姓を持つテーブルは、`an`です。  
  
```sql  
-- USE AdventureWorks2012
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C: アンダー スコア文字のエスケープ   
次の例と同様に、固定データベース ロールの名前を返します`db_owner`と`db_ddladmin`も返されますが、`dbo`ユーザー。 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

3 番目の文字位置にアンダー スコアが、ワイルドカードとして扱わし、文字で始まるプリンシパルのみにフィルター処理されていない`db_`です。 エスケープするために、アンダー スコアかっこで囲む`[_]`です。 

```sql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
これで、`dbo`ユーザーを除外します。   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a>参照  
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)   
  [% (ワイルドカード - 一致する文字列)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [& #91。&#93;です。(ワイルドカード - 一致する文字列)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [& #91、^ (& a) #93 です。(ワイルドカード - 一致しない文字列)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
