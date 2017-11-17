---
title: "挿入 (SQL グラフ) |Microsoft ドキュメント"
description: "SQL のグラフのノードまたはエッジ テーブルの構文を挿入します。"
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e694d89efef130d2abcd5cd6424e2be576ef09de
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="insert-sql-graph"></a>挿入 (SQL グラフ)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  1 つまたは複数の行を追加、`node`または`edge`テーブルに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 

> [!NOTE]   
>  標準の TRANSACT-SQL ステートメントでは、次を参照してください。 [INSERT TABLE (TRANSACT-SQL)](../../t-sql/statements/insert-transact-sql.md)です。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>ノード Table 構文に挿入します。 
ノードのテーブルに挿入するための構文は、通常のテーブルのと同じです。 

```  
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
## <a name="arguments"></a>引数  
 このドキュメントでは、SQL のグラフに関連する引数について説明します。 完全な一覧と INSERT ステートメントでサポートされている引数の説明では、「 [INSERT TABLE (TRANSACT-SQL)](../../t-sql/statements/insert-transact-sql.md)

 INTO  
 オプションのキーワードの間で使用できる`INSERT`と対象のテーブルです。  
  
 *search_condition_with_match*   
 `MATCH`句は、ノードまたはエッジ テーブルへの挿入中に、サブクエリで使用できます。 `MATCH`ステートメントの構文を参照してください[グラフ一致 (TRANSACT-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 指定された検索パターン`MATCH`グラフ述語の一部としての句。

 *edge_table_column_list*   
 ユーザーがの値を指定する必要があります`$from_id`と`$to_id`エッジに挿入するときにします。 値が指定されていないか、null 値は、これらの列に挿入された場合、エラーが返されます。 
  

## <a name="remarks"></a>解説  
ノードへの挿入は、すべてのリレーショナル テーブルに挿入すると同じです。 $Node_id 列の値が自動的に生成されます。

エッジ テーブルを挿入中に、ユーザーがの値を指定する必要があります`$from_id`と`$to_id`列です。   

一括挿入ノード テーブルは、リレーショナル テーブルのと同じままです。

エッジ テーブルに挿入する一括、前にノード テーブルをインポートする必要があります。 値を`$from_id`と`$to_id`から抽出できます、`$node_id`ノード テーブルの列およびエッジとして挿入します。 

  
### <a name="permissions"></a>Permissions  
 対象のテーブルに対する INSERT 権限が必要です。  
  
 メンバーにアクセス許可の既定値の挿入、 **sysadmin**固定サーバー ロール、 **db_owner**と**db_datawriter**固定データベース ロール、およびテーブル所有者です。 メンバー、 **sysadmin**、 **db_owner**、および**db_securityadmin**ロール、およびテーブル所有者は、他のユーザーに権限を譲渡できます。  
  
 OPENROWSET 関数の BULK オプションで、挿入を実行するには、メンバーである、 **sysadmin**固定サーバー ロールまたはの**bulkadmin**固定サーバー ロール。  
  

## <a name="examples"></a>使用例  
  
#### <a name="a--insert-into-node-table"></a>A.  ノードのテーブルに挿入します。  
 次の例では、Person ノード テーブルを作成し、そのテーブルに 2 行を挿入します。

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>B.  エッジ テーブルに挿入します。  
 次の例では、フレンド エッジ テーブルを作成し、エッジ テーブルに挿入します。

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>参照  
 [TABLE &#40; を挿入します。TRANSACT-SQL と #41 です。](../../t-sql/statements/insert-transact-sql.md)   
 [SQL Server 2017 を使用した処理グラフ](../../relational-databases/graphs/sql-graph-overview.md)  



