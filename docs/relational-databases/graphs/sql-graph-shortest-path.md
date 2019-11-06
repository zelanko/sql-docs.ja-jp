---
title: 最短のパス (SQL グラフ) |Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- SHORTEST PATH
- SHORTEST_PATH
dev_langs:
- TSQL
helpviewer_keywords:
- MATCH statement [SQL Server], SQL graph
- SQL graph, MATCH statement
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b4e07c8aa0c7911b02f7df5386c03b1860df38c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035883"
---
# <a name="shortestpath-transact-sql"></a>SHORTEST_PATH (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssver2015-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  これは、グラフの検索条件を再帰的の検索を指定しますまたは繰り返し。 SELECT ステートメントで、グラフ ノードとエッジのテーブル SHORTEST_PATH MATCH 内で使用できます。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="shortest-path"></a>最短のパス
SHORTEST_PATH 関数を使用して、検索できます。    
* 2 つの特定のノード/エンティティ間の最短パス
* 最短のパスを 1 つのソース。
* 複数のソース ノードから複数のターゲット ノードへの最短のパス。

入力として、任意の長さのパターンを受け取り、2 つのノード間に存在するための最短パスを返します。 この関数は、MATCH 内でのみ使用できます。 関数は、指定した 2 つのノード間の最短パスを 1 つだけを返します。 場合、ソースと宛先ノードを検査中に最初に見つかった関数を返します。 1 つだけパスのすべてのペアの間で同じ長さの 2 つ以上の最短パスが存在があります。 任意の長さのパターンが SHORTEST_PATH 関数内でのみ指定すること、注意してください。 

参照してください、 [MATCH (SQL グラフ)](../../t-sql/queries/match-sql-graph.md)構文。 

## <a name="for-path"></a>パス
任意の長さのパターンに参加する、FROM 句内のノードまたはエッジにあるテーブル名とパスを使用する必要があります。 パスのノードまたはエッジ テーブルでは、ノードまたはエッジ スキャンされるパスに沿ったのリストを表す、順序付けられたコレクションを返します、エンジンを示します。 SELECT 句で直接これらのテーブルから属性を投影することはできません。 属性はこれらのテーブルからのプロジェクトで、グラフの集計関数のパスを使用する必要があります。  

## <a name="arbitrary-length-pattern"></a>任意の長さのパターン
このパターンには、ノードが含まれていて、目的のノードに到達するまで、またはパターンで指定されているイテレーションの最大数まで繰り返しトラバースする必要がある端を満たします。 クエリが実行されるたびにこのパターンの実行結果のノードとエッジの終了ノードに、開始ノードからパスに沿って走査の順序付きコレクション値になります。 これは、正規表現の構文スタイル パターンと、次の 2 つのパターン量指定子がサポートされています。

* **'+'** :パターンを 1 回以上繰り返します。 最短パスが見つかったらすぐに終了します。
* **{1,n}** : パターンを 1 から "n" 回繰り返します。 最短が見つかるとすぐに終了します。

## <a name="lastnode"></a>LAST_NODE
LAST_NODE() 関数では、任意の長さの 2 つのトラバーサル パターンのチェーンを許可します。 シナリオのために使用できる場所。    
* 1 つ以上の最短パス パターンが、クエリで使用され、パターンの 1 つは、前のパターンの最後のノードで開始されます。
* 2 つの最短パス パターンは、同じ LAST_NODE() にマージします。

## <a name="graph-path-order"></a>グラフのパスの順序
グラフのパスの順序では、出力パスのデータを順序です。 出力パスの順序は、常に、再帰部分に表示されるノード/エッジが続くパターンの非再帰的な部分から開始されます。 クエリ最適化/実行中に、グラフを走査する順序を持つで出力された順序とは無関係です。 同様に、再帰的なパターンの矢印の方向もには影響しません、グラフのパスの順序。 

## <a name="graph-path-aggregate-functions"></a>グラフのパスの集計関数
ノードとエッジは、コレクション (ノードとそのパスに走査 edge(s)) の戻り値の任意の長さパターンに関連する、ために、ユーザーは、従来 tablename.attributename 構文を使用して直接属性を投影できません。 クエリが必要なプロジェクトの属性値を中間ノードやエッジ テーブルから、パスが走査するには、次のグラフのパスの集計関数を使用。STRING_AGG、LAST_VALUE、SUM、AVG、MIN、MAX、COUNT。 SELECT 句でこれらの集計関数を使用する一般的な構文です。

```
<GRAPH_PATH_AGGREGATE_FUNCTION>(<expression> , <separator>)  <order_clause>

    <order_clause> ::=
        { WITHIN GROUP (GRAPH PATH) }

    <GRAPH_PATH_AGGREGATE_FUNCTION> ::=
          STRING_AGG
        | LAST_VALUE
        | SUM
        | COUNT
        | AVG
        | MIN
        | MAX

```

### <a name="stringagg"></a>STRING_AGG
STRING_AGG 関数は、式と区切り記号の入力として受け取りし、文字列を返します。 ユーザーこの関数で使用できます、SELECT 句プロジェクト属性から中間のノードまたはエッジでスキャンされるパス。 

### <a name="lastvalue"></a>LAST_VALUE
プロジェクト パスの走査、LAST_VALUE 集計関数の最後のノードから属性を使用できます。 ノード テーブル名のみ、この関数への入力としてのエッジ テーブルの別名を提供するエラーまたはエイリアスを使用できます。

**最後のノード**:最後のノードは、一致述部の矢印の方向に関係なく、走査するパスの最後に表示するノードを参照します。 たとえば、「 `MATCH(SHORTEST_PATH(n(-(e)->p)+) )`」のように入力します。 ここで、パスの最後のノードは、訪問した P の最後のノードになります。 

一方、最後のノードでは、このパターンの出力グラフのパスの最後の n 番目のノードです。 `MATCH(SHORTEST_PATH((n<-(e)-)+p))`    

### <a name="sum"></a>SUM
この関数は、スキャン対象のパスで指定されたノード/エッジ属性値または表示される式の合計を返します。

### <a name="count"></a>COUNT
この関数は、パスで目的のノード/エッジ属性の null 以外の値の数を返します。 COUNT 関数をサポートしています、'\*' ノードまたはエッジ テーブルの別名を持つ演算子。 エイリアスがなければノードまたはエッジ テーブルでの使用状況\*があいまいであり、エラーが発生します。

    {  COUNT( <expression> | <node_or_edge_alias>.* )  <order_clause>  }


### <a name="avg"></a>AVG
スキャン対象のパスで指定されたノード/エッジ属性値または表示される式の平均を返します。

### <a name="min"></a>MIN
指定されたノード/エッジ属性値またはスキャン対象のパスに表示された式から最小値を返します。

### <a name="max"></a>MAX
指定されたノード/エッジ属性値またはスキャン対象のパスに表示された式から最大値を返します。

## <a name="remarks"></a>コメント  
shortest_path 関数は、MATCH 内でのみ使用できます。     
LAST_NODE が shortest_path 内でのみサポートされます。     
加重の最短パス、すべてのパス、またはすべての最短パスを検索することはサポートされていません。         
場合によってより高いクエリの実行時間が多数のホップ数、使用してクエリの不適切なプランが生成されます。 ハッシュ結合のヒントを使用に役立つ場合があります。    


## <a name="examples"></a>使用例 
ここに注記をここに示すクエリの例は、ノードを使用して、エッジ テーブルに作成[SQL グラフのサンプル](./sql-graph-sample.md)

### <a name="a--find-shortest-path-between-2-people"></a>A.  2 人との間の最短パスを検索します。
 次の例では、Jacob と Alice 間の最短パスを検索します。 //People/person ノードとグラフのサンプル スクリプトから作成された FriendOf edge 必要になります。 

 ```
SELECT PersonName, Friends
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

 ### <a name="b--find-shortest-path-from-a-given-node-to-all-other-nodes-in-the-graph"></a>B.  グラフで、特定のノードから他のすべてのノードへの最短パスを検索します。 
 次の例では、グラフと Jacob からすべての人を開始していますの最短パスで Jacob に接続されているすべてのユーザーを検索します。 

 ```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
AND Person1.name = 'Jacob'
 ```

### <a name="c--count-the-number-of-hopslevels-traversed-to-go-from-one-person-to-another-in-the-graph"></a>C.  ホップ/レベルに、グラフ内の別の 1 人のユーザーから移動するためにスキャンの数をカウントします。
 次の例では、Jacob と Alice 間の最短パスを検索し、Alice に Jacob から移動にかかるホップの数を出力します。 

 ```
 SELECT PersonName, Friends, levels
FROM (  
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        LAST_VALUE(Person2.name) WITHIN GROUP (GRAPH PATH) AS LastNode,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2)+))
    AND Person1.name = 'Jacob'
) AS Q
WHERE Q.LastNode = 'Alice'
 ```

### <a name="d-find-people-1-3-hops-away-from-a-given-person"></a>D. 特定の人物からホップの 1 ~ 3 人の検索します。
次の例では、彼の連絡先から 1 ~ 3 のグラフのホップで Jacob と彼に接続されているすべてのユーザーの間の最短パスを検索します。 

```
SELECT
    Person1.name AS PersonName, 
    STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends
FROM
    Person AS Person1,
    friendOf FOR PATH AS fo,
    Person FOR PATH  AS Person2
WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
AND Person1.name = 'Jacob'
```

### <a name="e-find-people-exactly-2-hops-away-from-a-given-person"></a>E. 特定の人物からホップ数を正確に 2 人の検索します。
次の例では、Jacob とグラフで彼の連絡先から 2 ホップしている人たちの間の最短パスを検索します。 

```
SELECT PersonName, Friends
FROM (
    SELECT
        Person1.name AS PersonName, 
        STRING_AGG(Person2.name, '->') WITHIN GROUP (GRAPH PATH) AS Friends,
        COUNT(Person2.name) WITHIN GROUP (GRAPH PATH) AS levels
    FROM
        Person AS Person1,
        friendOf FOR PATH AS fo,
        Person FOR PATH  AS Person2
    WHERE MATCH(SHORTEST_PATH(Person1(-(fo)->Person2){1,3}))
    AND Person1.name = 'Jacob'
) Q
WHERE Q.levels = 2
```

## <a name="see-also"></a>関連項目  
 [MATCH (SQL グラフ)](../../t-sql/queries/match-sql-graph.md)    
 [CREATE TABLE &#40;SQL グラフ&#41;](../../t-sql/statements/create-table-sql-graph.md)   
 [INSERT (SQL グラフ)](../../t-sql/statements/insert-sql-graph.md)  
 [SQL Server 2017 でのグラフ処理](../../relational-databases/graphs/sql-graph-overview.md)     
 
