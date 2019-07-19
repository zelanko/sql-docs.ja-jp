---
title: SQL グラフのアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0124126556967800e37b296a73bd951a18d3936e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035978"
---
# <a name="sql-graph-architecture"></a>SQL グラフ アーキテクチャ  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

SQL グラフを構築する方法について説明します。 基本事項を知ることは容易にできるように SQL グラフの他の記事を理解します。
 
## <a name="sql-graph-database"></a>SQL グラフ データベース
ユーザーは、データベースごとに 1 つのグラフを作成できます。 グラフは、ノードとエッジ テーブルのコレクションです。 データベース内の任意のスキーマでノードまたはエッジ テーブルを作成できますが、すべて 1 つの論理グラフに属する。 ノード テーブルには、ノードの類似する型のコレクションです。 たとえば、Person ノード テーブルは、グラフに属しているすべての人のノードを保持します。 同様に、エッジ テーブルは、エッジの類似する型のコレクションです。 たとえば、Friend エッジ テーブルは、別のユーザーにユーザーを接続するすべての端を保持します。 テーブルには、ノードとエッジが格納されているために、通常のテーブルでサポートされる操作のほとんどは、ノードまたはエッジ テーブルでサポートされます。 
 
 
![sql のアーキテクチャ グラフ](../../relational-databases/graphs/media/sql-graph-architecture.png "Sql グラフ データベース アーキテクチャ")   

図 1: SQL グラフ データベース アーキテクチャ
 
## <a name="node-table"></a>ノード テーブル
ノード テーブルでは、グラフのスキーマのエンティティを表します。 ノード テーブルが作成されるたびに、ユーザー定義の列と共に暗黙`$node_id`列を作成すると、データベース内の特定のノードを一意に識別します。 内の値`$node_id`の組み合わせは、自動的に生成される`object_id`のノード テーブルと内部的に生成された bigint 値。 ただし、ときに、`$node_id`列を選択すると、JSON 文字列の形式での計算値が表示されます。 また、`$node_id`は、16 進数の文字列と内部名にマップされる擬似列です。 選択すると`$node_id`として、テーブルから列名が表示されます`$node_id_<hex_string>`します。 内部クエリを実行する推奨される方法は、クエリで擬似列名を使用して`$node_id`列と 16 進文字列と内部名を使用を避ける必要があります。

ユーザーが一意の制約を作成またはインデックスことをお勧め、`$node_id`のいずれかでない場合は、ノード テーブルの作成時に列を作成、既定値が一意、非クラスター化インデックスが自動的に作成します。 ただし、グラフ擬似列のすべてのインデックスは、基になる内部列に作成されます。 作成されたインデックスは、`$node_id`列を内部に表示されます`graph_id_<hex_string>`列。   


## <a name="edge-table"></a>エッジ テーブル
エッジ テーブルでは、グラフ内のリレーションシップを表します。 エッジは常に送られ、2 つのノードを接続します。 エッジ テーブルでは、グラフ内の多対多リレーションシップをモデル化することができます。 エッジ テーブルもかまいませんが、ユーザー定義の属性がない可能性があります。 ユーザー定義の属性の場合、と共に、エッジ テーブルが作成されるたびに、暗黙的な 3 つの列がエッジ テーブルで作成されます。

|列名    |説明  |
|---   |---  |
|`$edge_id`   |データベース内の指定されたエッジを一意に識別します。 生成された列であるし、値は、object_id、エッジ テーブルと内部的に生成された bigint 値の組み合わせ。 ただし、ときに、`$edge_id`列を選択すると、JSON 文字列の形式での計算値が表示されます。 `$edge_id` 16 進数の文字列と内部名にマップされる擬似列です。 選択すると`$edge_id`として、テーブルから列名が表示されます`$edge_id_\<hex_string>`します。 内部クエリを実行する推奨される方法は、クエリで擬似列名を使用して`$edge_id`列と 16 進文字列と内部名を使用を避ける必要があります。 |
|`$from_id`   |ストア、`$node_id`エッジの発生元からのノードの。  |
|`$to_id`   |ストア、`$node_id`ノード、エッジが終了するのです。 |

接続できる特定のエッジ ノードに挿入されたデータが適用されます、`$from_id`と`$to_id`列。 最初のリリースでは、ノードの 2 つの種類の接続を制限することに、エッジ テーブルの制約を定義することはできません。 つまり、エッジは、その型に関係なく、グラフに 2 つのノードを接続できます。

ような`$node_id`列、お勧めのユーザーでの一意のインデックスまたは制約を作成、`$edge_id`のいずれかでない場合は、エッジ テーブルの作成時に列を作成、既定値に一意、非クラスター化インデックスが自動的に作成この列です。 ただし、グラフ擬似列のすべてのインデックスは、基になる内部列に作成されます。 作成されたインデックスは、`$edge_id`列を内部に表示されます`graph_id_<hex_string>`列。 お勧め、ユーザーのインデックスを作成する OLTP シナリオ (`$from_id`、 `$to_id`) のエッジの方向に高速参照の列。  

図 2 では、データベース内のノードとエッジ テーブルを格納する方法を示します。 

![テーブル-人の友人](../../relational-databases/graphs/media/person-friends-tables.png "/people/person ノードや友人のエッジ テーブル")   

図 2: ノードとエッジ テーブルの表現



## <a name="metadata"></a>メタデータ
これらのメタデータ ビューを使用して、ノードまたはエッジ テーブルの属性を参照してください。
 
### <a name="systables"></a>sys.tables
次の新、bit 型、sys 列が追加されます。テーブル。 場合`is_node`テーブルがノード テーブルであることを示します 1 に設定されている場合に`is_edge`テーブルがエッジ テーブルであるかを示す 1 に設定されます。
 
|列名 |データ型 |説明 |
|--- |---|--- |
|is_node |bit |1 = これは、ノード テーブル |
|is_edge |bit |1 = これは、エッジ テーブル |
 
### <a name="syscolumns"></a>sys.columns
`sys.columns`ビューには、追加の列が含まれています。`graph_type`と`graph_type_desc`、ノードとエッジ テーブル内の列の種類を表します。
 
|列名 |データ型 |説明 |
|--- |---|--- |
|graph_type |ssNoversion |内部の列値のセットを使用します。 値は 1 ~ 8 のグラフ列から他のユーザーの場合は NULL です。  |
|graph_type_desc |nvarchar(60)  |一連の値を持つ内部列 |
 
次の表に、有効な値`graph_type`列

|列の値  |説明  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns` ノードまたはエッジ テーブルで作成した暗黙の型の列に関する情報を格納もされます。 Sys.columns から以下の情報を取得できる、ただし、ユーザーは、ノードまたはエッジ テーブルからのこれらの列を選択できません。 

ノード テーブルで暗黙的な列

|列名    |データ型  |is_hidden  |解説  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |内部`graph_id`列  |
|$node_id_\<hex_string> |NVARCHAR   |0  |外部ノード`node_id`列  |

エッジ テーブルで暗黙的な列

|列名    |データ型  |is_hidden  |解説  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |内部`graph_id`列  |
|$edge_id_\<hex_string> |NVARCHAR   |0  |外部`edge_id`列  |
|from_obj_id_\<hex_string>  |INT    |1  |ノードから内部 `object_id`  |
|from_id_\<hex_string>  |bigint |1  |ノードから内部 `graph_id`  |
|$from_id_\<hex_string> |NVARCHAR   |0  |ノードから外部 `node_id`  |
|to_obj_id_\<hex_string>    |INT    |1  |ノードの内部 `object_id`  |
|to_id_\<hex_string>    |bigint |1  |ノードの内部 `graph_id`  |
|$to_id_\<hex_string>   |NVARCHAR   |0  |外部のノード `node_id`  |
 
### <a name="system-functions"></a>システム関数
次の組み込み関数が追加されます。 これらは、生成された列から情報を抽出するユーザーができます。 これらのメソッドでは、ユーザーからの入力は検証されませんが、注意してください。 ユーザーが、無効なを指定した場合`sys.node_id`メソッドは適切な部分を抽出し、それを返します。 たとえば、OBJECT_ID_FROM_NODE_ID になります、`$node_id`として入力し、object_id を返す、このノードが属するテーブルの。 
 
|組み込み   |説明  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Object_id を抽出します。 `node_id`  |
|GRAPH_ID_FROM_NODE_ID  |Graph_id を抽出します。 `node_id`  |
|NODE_ID_FROM_PARTS |Node_id を構築、`object_id`と `graph_id`  |
|OBJECT_ID_FROM_EDGE_ID |抽出`object_id`から `edge_id`  |
|GRAPH_ID_FROM_EDGE_ID  |Id を抽出します。 `edge_id`  |
|EDGE_ID_FROM_PARTS |構築`edge_id`から`object_id`と id  |



## <a name="transact-sql-reference"></a>Transact-SQL リファレンス 
学習、 [!INCLUDE[tsql-md](../../includes/tsql-md.md)] SQL Server と Azure SQL Database で導入された拡張機能を有効にするグラフ オブジェクトに対するクエリの作成とします。 クエリ言語の拡張機能では、クエリのヘルプし、ASCII アート構文を使用してグラフを走査します。
 
### <a name="data-definition-language-ddl-statements"></a>データ定義言語 (DDL) ステートメント

|タスク   |関連記事  |メモ
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE` AS ノードまたは AS エッジ テーブルの作成をサポートするために拡張されています。 エッジ テーブルは可能性がありますか、任意のユーザー定義の属性がない可能性がありますに注意してください。  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|ノードとエッジ テーブルには、リレーショナル テーブルを使用して、同じ方法を変更できる、`ALTER TABLE`します。 ユーザーでは、追加したり、ユーザー定義の列、インデックスまたは制約を変更することができます。 ただし、内部グラフ列を変更するには、ような`$node_id`または`$edge_id`エラーになります。  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |ユーザーは、擬似列およびノードとエッジ テーブル内のユーザー定義の列にインデックスを作成できます。 非クラスター化列ストア インデックスを含むすべてのインデックスの種類がサポートされます。  |
|エッジの制約を作成します。    |[エッジ制約&#40;TRANSACT-SQL&#41;](../../relational-databases/tables/graph-edge-constraints.md)  |ユーザーが特定のセマンティクスを適用するエッジ テーブルでのエッジの制約を作成およびもデータの整合性を維持  |
|DROP TABLE |[DROP TABLE (Transact-SQL)](../../t-sql/statements/drop-table-transact-sql.md)  |同様のリレーショナル テーブルを使用して、ノードとエッジ テーブルを削除することができます、`DROP TABLE`します。 ただし、このリリースではありません制約を十分に削除されたノードにエッジがポイントありませんし、ノードまたはノード テーブルの削除時に、エッジの連鎖削除がサポートされていません。 ノード テーブルが削除された場合は、ユーザー、グラフの整合性を維持するために手動でそのノード テーブル内のノードに接続されている、エッジと削除することをお勧めします。  |


### <a name="data-manipulation-language-dml-statements"></a>データ操作言語 (DML) ステートメント

|タスク   |関連記事  |メモ
|---  |---  |---  |
|INSERT |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|ノード テーブルに挿入すると、リレーショナル テーブルに挿入するよりも同じです。 値は、`$node_id`列が自動的に生成されます。 値を挿入しようとしています。`$node_id`または`$edge_id`列はエラーになります。 ユーザーが値を指定する必要があります`$from_id`と`$to_id`エッジ テーブルを挿入するときに列。 `$from_id` `$to_id`は、`$node_id`接続する特定のエッジ ノードの値。  |
|Del | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|リレーショナル テーブルから削除されると、同じ方法でノードまたはエッジ テーブルからデータを削除できます。 ただし、このリリースではありません制約を十分に削除されたノードにエッジがポイントありませんし、ノードの削除時に、エッジの連鎖削除がサポートされていません。 ノードが削除されると、そのノードに接続するすべてのエッジも削除されたこと、グラフの整合性を維持するをお勧めします。  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |ユーザー定義の列の値は、UPDATE ステートメントを使用して更新できます。 内部グラフ列を更新`$node_id`、 `$edge_id`、`$from_id`と`$to_id`は許可されていません。  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE` ステートメントは、ノードまたはエッジ テーブルでサポートされます。  |


### <a name="query-statements"></a>クエリ ステートメント

|タスク   |関連記事  |メモ
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|ノードとエッジ テーブルとして内部的に格納されます、ノードとエッジ テーブルでの SQL Server または Azure SQL Database のテーブルでサポートされている操作のほとんどをサポートするため  |
|MATCH  | [一致&#40;TRANSACT-SQL&#41;](../../t-sql/queries/match-sql-graph.md)|一致の組み込みは、パターン マッチングとグラフをトラバースをサポートするために導入されました。  |



## <a name="limitations-and-known-issues"></a>制限事項と既知の問題  
このリリースでは、ノードとエッジ テーブルにいくつかの制限があります。
* ローカルまたはグローバル一時テーブルには、ノードまたはエッジ テーブルをすることはできません。
* ノードまたはエッジ テーブルとしては、テーブルの種類とテーブル変数を宣言することはできません。 
* ノードとエッジ テーブルは、システム バージョン管理されたテンポラル テーブルとして作成することはできません。   
* ノードとエッジ テーブルには、メモリ最適化テーブルをすることはできません。  
* ユーザーが更新できない、`$from_id`と`$to_id`UPDATE ステートメントを使用してエッジの列。 エッジを接続するノードを更新するには、ユーザーは、新しいノードを指す新しいエッジを挿入し、前の 1 つを削除する必要があります。
* データベースをまたがるグラフ オブジェクトのクエリにはサポートされていません。 


## <a name="next-steps"></a>次の手順
新しい構文を使用して開始するを参照してください[SQL グラフ データベースのサンプル。](./sql-graph-sample.md)
 

