---
title: "テーブル (SQL グラフ) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_GRAPH_TSQL
- TABLE
- CREATE_TABLE_TSQL
- NODE
- NODE_TSQL
- AS_NODE
- AS_NODE_TSQL
- EDGE
- EDGE_TSQL
- AS_EDGE
- AS_EDGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- graph
- SQL graph
- CREATE TABLE SQL graph
- NODE
- EDGE
- SQL graph, CREATE TABLE statement
ms.assetid: 
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c32a8c4f683f20c4384089c1d2552614090f9b3d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-sql-graph"></a>テーブル (SQL グラフ) を作成します。
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

いずれかで新しい SQL グラフ テーブルを作成、`NODE`または`EDGE`テーブル。 
  
> [!NOTE]   
>  標準の TRANSACT-SQL ステートメントでは、次を参照してください。 [CREATE TABLE (TRANSACT-SQL)](../../t-sql/statements/create-table-transact-sql.md)です。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
    AS [ NODE | EDGE ]
[ ; ]  
```  
  
  
## <a name="arguments"></a>引数  
このドキュメントでは、SQL のグラフに関連する引数のみが一覧表示します。 完全な一覧とサポートされている引数の説明では、「 [CREATE TABLE (TRANSACT-SQL)](../../t-sql/statements/create-table-transact-sql.md)

 *database_name*    
 テーブルが作成されたデータベースの名前を指定します。 *database_name*既存のデータベースの名前を指定する必要があります。 指定しない場合、 *database_name*既定値は、現在のデータベースです。 現在の接続のログインがで指定されたデータベース内の既存のユーザー ID を関連付ける必要がある*database_name*、そのユーザー ID には、CREATE TABLE アクセス許可が必要とします。  
  
 *schema_name*    
 新しいテーブルが所属するスキーマの名前です。  
  
 *table_name*    
 ノードまたはエッジ テーブルの名前です。 テーブル名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 *table_name*できるローカル一時テーブル名を除いて、128 文字の最大値 (名前は、1 つの番号記号で始まります (#)) 116 文字を超えることはできません。  
  
 ノード   
 ノードのテーブルを作成します。

 エッジ  
 エッジ テーブルを作成します。  
  
## <a name="remarks"></a>解説  
一時テーブル ノードまたはエッジ テーブルを作成することはできません。  

テンポラル テーブルとしてのノードまたはエッジ テーブルを作成することはサポートされていません。

ノードまたはエッジ テーブルの stretch database がサポートされていません。

ノードまたはエッジ テーブルは、テーブルの外部 (polybase はサポートされませんグラフ テーブル) にすることはできません。 
  
 
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-node-table"></a>A. 作成、`NODE`テーブル
 次の例を作成する方法を示しています、`NODE`テーブル

```
 CREATE TABLE Person (
        ID INTEGER PRIMARY KEY, 
        name VARCHAR(100), 
        email VARCHAR(100)
 ) AS NODE;
```

### <a name="b-create-an-edge-table"></a>B. 作成、`EDGE`テーブル
次の例を作成する方法を示して`EDGE`テーブル

```
 CREATE TABLE friends (
    id integer PRIMARY KEY,
    start_date date
 ) AS EDGE;

```

```
 -- Create a likes edge table, this table does not have any user defined attributes   
 CREATE TABLE likes AS EDGE;

```


## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [挿入 (SQL グラフ)](../../t-sql/statements/insert-sql-graph.md)]  
 [SQL Server 2017 を使用した処理グラフ](../../relational-databases/graphs/sql-graph-overview.md)


