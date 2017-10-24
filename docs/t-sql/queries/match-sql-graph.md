---
title: "一致する (SQL グラフ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MATCH
- MATCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: db211fa0988f2dbe6a72291f898d670d44d3f215
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---

# <a name="match-transact-sql"></a>一致する (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

  グラフの検索条件を指定します。 一致は、WHERE 句の一部として、SELECT ステートメントで、グラフ ノードとエッジのテーブルでのみ使用できます。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
MATCH (<graph_search_pattern>)

<graph_search_pattern>::=
    {<node_alias> { 
                     { <-( <edge_alias> )- } 
                   | { -( <edge_alias> )-> }
                 <node_alias> 
                 } 
     }
     [ { AND } { ( <graph_search_pattern> ) } ]
     [ ,...n ]
  
<node_alias> ::=
    node_table_name | node_alias 

<edge_alias> ::=
    edge_table_name | edge_alias
```

## <a name="arguments"></a>引数  
*graph_search_pattern*  
パターン検索またはグラフを走査するパスを指定します。 このパターンは、グラフ内のパスをスキャンするのに ASCII アートの構文を使用します。 パターンは、提供される矢印の方向のエッジを使用して別に 1 つのノードから移動します。 Parantheses 内部エッジ名前または別名が提供されます。 ノード名またはエイリアスは、2 つの矢印端に表示されます。 矢印は、パターンのどちらの方向に移動できます。

*node_alias*  
名前または FROM 句で指定されたノードのテーブルの別名。

*edge_alias*  
名前または FROM 句で指定されたエッジ テーブルの別名です。


## <a name="remarks"></a>解説  
一致内のノード名を繰り返すことができます。  言い換えると、ノードは、同じクエリ内で時間の任意の数を走査します。  
一致する内部エッジ名を繰り返すことはできません。  
エッジは、どちらの方向ポイントできますが、明示的な方向である必要があります。  
または、一致パターンでは、NOT 演算子はサポートされていません。 使用して他の式とは、WHERE 句で、一致を組み合わせることができます。 ただし、これを使用して他の式と組み合わせると OR がサポートされていません。 またはします。 

## <a name="examples"></a>使用例  
### <a name="a--find-a-friend"></a>A.  友達を検索します。 
 次の例は、Person ノード テーブルと友人エッジ テーブルを作成、一部のデータを挿入し、一致を使用して、Alice、グラフ内のユーザーの友人を検索します。

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Insert into node table
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 INSERT INTO dbo.Person VALUES (3, 'Jacob');

-- Insert into edge table
INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2011');

INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'John'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'Jacob'), '10/15/2012');

-- use MATCH in SELECT to find friends of Alice
SELECT Person2.name AS FriendName
FROM Person Person1, friend, Person Person2
WHERE MATCH(Person1-(friend)->Person2)
AND Person1.name = 'Alice';

 ```

 ### <a name="b--find-friend-of-a-friend"></a>B.  友人の友人を検索します。
 次の例では、Alice の友人の友人を見つけようとします。 

 ```
SELECT Person3.name AS FriendName 
FROM Person Person1, friend, Person Person2, friend friend2, Person Person3
WHERE MATCH(Person1-(friend)->Person2-(friend2)->Person3)
AND Person1.name = 'Alice';

 ```

### <a name="c--more-match-patterns"></a>C.  詳細`MATCH`パターン
 内の一致パターンを指定するいくつか他の方法を次に示します。

 ```
 -- Find a friend
    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2
    WHERE MATCH(Person1-(friend)->Person2);
    
-- The pattern can also be expressed as below

    SELECT Person2.name AS FriendName
    FROM Person Person1, friend, Person Person2 
    WHERE MATCH(Person2<-(friend)-Person1);


-- Find 2 people who are both friends with same person
    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0<-(friend2)-Person2);
    
-- this pattern can also be expressed as below

    SELECT Person1.name AS Friend1, Person2.name AS Friend2
    FROM Person Person1, friend friend1, Person Person2, 
         friend friend2, Person Person0
    WHERE MATCH(Person1-(friend1)->Person0 AND Person2-(friend2)->Person0);
 ```
 

## <a name="see-also"></a>参照  
 [TABLE &#40; を作成します。グラフの SQL &#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [挿入 (SQL グラフ)](../../t-sql/statements/insert-sql-graph.md)]  
 [SQL Server 2017 を使用した処理グラフ](../../relational-databases/graphs/sql-graph-overview.md)  

