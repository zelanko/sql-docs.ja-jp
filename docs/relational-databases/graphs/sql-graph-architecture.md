---
title: "SQL Graph のアーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: graphs
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: 
caps.latest.revision: 
author: shkale-msft
ms.author: shkale
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 887ac78e70d529c404ee2ed3088f088ed53e4a54
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="sql-graph-architecture"></a>SQL Graph のアーキテクチャ  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

SQL のグラフを構築する方法について説明します。 基本を知ることがやすく他の SQL グラフ記事を理解します。
 
## <a name="sql-graph-database"></a>データベース ファイルのグラフ
ユーザーは、データベースごとに 1 つのグラフを作成できます。 グラフは、ノードとエッジ テーブルのコレクションです。 データベース内の任意のスキーマ ノードまたはエッジ テーブルに作成できますが、1 つの論理グラフに属しています。 ノードの表は、ノードの類似する型のコレクションです。 たとえば、Person ノード テーブルでは、グラフに属しているすべての人ノードが保持されます。 同様に、エッジ テーブルは、エッジの類似する型のコレクションです。 たとえば、友人のエッジ テーブルでは、他のユーザーにユーザーを接続するすべてのエッジが保持されます。 ノードとエッジは、テーブルに格納される、ために、通常のテーブルでサポートされる操作のほとんどは、ノードまたはエッジ テーブルでサポートされます。 
 
 
![sql のアーキテクチャ グラフ](../../relational-databases/graphs/media/sql-graph-architecture.png "Sql グラフ データベース アーキテクチャ")   

図 1: グラフの SQL データベースのアーキテクチャ
 
## <a name="node-table"></a>ノード テーブル
ノードの表では、グラフ スキーマ内のエンティティを表します。 ノードのテーブルが作成されるたびに、ユーザー定義の列と共に暗黙的な`$node_id`列を作成すると、データベース内の特定のノードを一意に識別します。 内の値`$node_id`自動的に生成され、を組み合わせた`object_id`のノードのテーブルおよび内部で生成された bigint 値。 ただし、ときに、`$node_id`列が選択されていると、JSON 文字列の形式での計算値が表示されます。 また、 `$node_id` 16 進数の文字列で、内部名にマップされる擬似列です。 選択すると`$node_id`として、テーブルから列名が表示されます`$node_id_<hex_string>`です。 擬似列名を使用して、クエリでは、内部クエリを実行することをお勧め`$node_id`列と 16 進文字列での内部名の使用を回避する必要があります。

ユーザーは unique 制約を作成または、インデックスをお勧め、`$node_id`場合 1 つはありませんが、ノードのテーブルの作成時に列を作成、既定の一意な非クラスター化インデックスが自動的に作成します。 ただし、グラフの擬似列で、インデックス、基になる内部列が作成されます。 作成されたインデックスは、`$node_id`列を内部に表示されます`graph_id_<hex_string>`列です。   


## <a name="edge-table"></a>エッジ テーブル
エッジ テーブルでは、グラフ内のリレーションシップを表します。 エッジは常に転送され、2 つのノードを接続します。 エッジ テーブルでは、グラフ内の多対多リレーションシップをモデル化することができます。 エッジ テーブルは、可能性があります。 または内の任意のユーザー定義属性がない可能性があります。 ユーザー定義属性と共に、エッジ テーブルが作成されるたびに、暗黙的な 3 つの列は、エッジ テーブルに作成されます。

|列名    |Description  |
|---   |---  |
|`$edge_id`   |データベース内の特定のエッジを一意に識別します。 生成された列であるし、値は、object_id、エッジ テーブルと内部で生成された bigint 値の組み合わせ。 ただし、ときに、`$edge_id`列が選択されていると、JSON 文字列の形式での計算値が表示されます。 `$edge_id` 16 進数の文字列で、内部名にマップされる擬似列です。 選択すると`$edge_id`として、テーブルから列名が表示されます`$edge_id_\<hex_string>`です。 擬似列名を使用して、クエリでは、内部クエリを実行することをお勧め`$edge_id`列と 16 進文字列での内部名の使用を回避する必要があります。 |
|`$from_id`   |ストア、`$node_id`エッジの発生源からのノードのです。  |
|`$to_id`   |ストア、`$node_id`エッジが終了した、ノードのです。 |

指定したエッジは接続可能なノードが挿入されたデータによって管理される、`$from_id`と`$to_id`列です。 最初のリリースでのノードの 2 つの種類の接続を制限する、エッジ テーブルに対する制約を定義することはできません。 つまり、エッジは、それらの種類に関係なく、グラフの 2 つのノードを接続できます。

ような`$node_id`列、お勧めユーザーが、上に、一意のインデックスまたは制約を作成すること、`$edge_id`場合 1 つはありませんが、エッジ テーブルの作成時に列を作成、一意、非クラスター化インデックスが自動的に作成、既定値この列です。 ただし、グラフの擬似列で、インデックス、基になる内部列が作成されます。 作成されたインデックスは、`$edge_id`列を内部に表示されます`graph_id_<hex_string>`列です。 お勧め、ユーザーのインデックスを作成する OLTP シナリオ (`$from_id`、 `$to_id`) のエッジの方向に高速参照の列です。  

図 2 では、データベース内のノードとエッジ テーブルを格納する方法を示します。 

![ユーザーの友人-テーブル](../../relational-databases/graphs/media/person-friends-tables.png "//people/person ノードや友人のエッジ テーブル")   

図 2: ノードとエッジ テーブルの表現



## <a name="metadata"></a>メタデータ
これらのメタデータのビューを使用して、ノードまたはエッジ テーブルの属性を参照してください。
 
### <a name="systables"></a>sys.tables
次の新しい、bit 型、sys 列が追加されます。テーブル。 場合`is_node`こと、テーブルですが、ノードを示す 1 に設定されている場合に`is_edge`がテーブルには、エッジ テーブルを示す 1 に設定します。
 
|列名 |データ型 |Description |
|--- |---|--- |
|is_node |bit |1 = これは、ノード テーブル |
|is_edge |bit |1 = これは、エッジ テーブル |
 
### <a name="syscolumns"></a>sys.columns
`sys.columns`ビューには、追加の列が含まれています。`graph_type`と`graph_type_desc`、ノードとエッジ テーブル内の列の型を示すです。
 
|列名 |データ型 |Description |
|--- |---|--- |
|graph_type |int |内部の列値のセット。 値は 1 ~ 8 列のグラフから他のユーザーの場合は NULL です。  |
|graph_type_desc |nvarchar(60)  |内部の列の値のセットで |
 
次の表に、有効な値の`graph_type`列

|列の値  |Description  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns` ノードまたはエッジ テーブルに作成される暗黙の列に関する情報も格納します。 Sys.columns から以下の情報を取得できる、ただし、ユーザーは、ノードまたはエッジ テーブルからのこれらの列を選択できません。 

ノードはテーブルの暗黙の列  
|列名    |データ型  |is_hidden  |解説  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |internal graph_id column  |
|$node_id_\<hex_string> |NVARCHAR   |0  |外部のノード id 列  |

エッジ テーブル内の暗黙の列  
|列名    |データ型  |is_hidden  |解説  |
|---  |---|---|---  |
|graph_id_\<hex_string> |bigint |1  |internal graph_id column  |
|$edge_id_\<hex_string> |NVARCHAR   |0  |id 列の外部境界  |
|from_obj_id_\<hex_string>  |INT    |1  |オブジェクト id のノードから内部  |
|from_id_\<hex_string>  |bigint |1  |内部ノード graph_id から  |
|$from_id_\<hex_string> |NVARCHAR   |0  |ノード id から外部  |
|to_obj_id_\<hex_string>    |INT    |1  |ノードのオブジェクト id の内部  |
|to_id_\<hex_string>    |bigint |1  |内部ノード graph_id から  |
|$to_id_\<hex_string>   |NVARCHAR   |0  |外部のノード id  |
 
### <a name="system-functions"></a>システム関数
次の組み込み関数が追加されます。 生成された列から情報を抽出するユーザーに役立つ情報します。 これらのメソッドでは、ユーザーから入力は検証されませんが、注意してください。 ユーザーが、無効なを指定した場合`sys.node_id`メソッドは適切な部分を抽出し、それを返します。 たとえば、OBJECT_ID_FROM_NODE_ID になります、`$node_id`として入力し、object_id を返すはこのノードが属するテーブルのです。 
 
|組み込み   |Description  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Object_id を node_id から抽出します。  |
|GRAPH_ID_FROM_NODE_ID  |Node_id、graph_id を抽出します。  |
|NODE_ID_FROM_PARTS |Object_id と、graph_id から node_id を構築します。  |
|OBJECT_ID_FROM_EDGE_ID |Object_id を edge_id から抽出します。  |
|GRAPH_ID_FROM_EDGE_ID  |Edge_id からの id を抽出します。  |
|EDGE_ID_FROM_PARTS |Object_id と id から edge_id を構築します。  |



## <a name="transact-sql-reference"></a>TRANSACT-SQL リファレンス 
について、 [!INCLUDE[tsql-md](../../includes/tsql-md.md)] SQL Server と Azure SQL Database で導入された拡張機能を可能にする作成とグラフのオブジェクトをクエリします。 クエリ言語拡張機能では、クエリのヘルプし、ASCII アートの構文を使用してグラフを走査します。
 
### <a name="data-definition-language-ddl-statements"></a>データ定義言語 (DDL) ステートメント
|タスク   |関連トピック  |注
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE ` 拡張された AS ノードまたは AS エッジ テーブルの作成をサポートするためにします。 エッジ テーブルがいるかが定義していないすべてのユーザー属性に注意してください。  |
|ALTER TABLE    |[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|ノードとエッジ テーブルにリレーショナル テーブルを使用して、同じ方法を変更することができます、`ALTER TABLE`です。 ユーザーでは、追加したり、ユーザー定義の列、インデックスまたは制約を変更することができます。 ただし、内部のグラフ列を変更するには、機会をいただいて`$node_id`または`$edge_id`エラーになります。  |
|CREATE INDEX   |[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  |ユーザーは、擬似列とテーブルのノードとエッジ テーブル内のユーザー定義の列にインデックスを作成できます。 クラスター化および非クラスター化列ストア インデックスを含むすべてのインデックス型がサポートされます。  |
|DROP TABLE |[DROP TABLE &#40;TRANSACT-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)  |リレーショナル テーブルを使用して、同じ方法 ノードとエッジ テーブルを削除することができます、`DROP TABLE`です。 ただし、このリリースで制約はありませんエッジ ポイントを削除したノードとノードまたはノードのテーブルの削除時に、エッジのカスケード削除はサポートされていないことを確認します。 ノードのテーブルが削除された場合、ユーザーを削除、グラフの整合性を維持するために手動でそのノードのテーブル内のノードに接続されているすべての端をお勧めします。  |


### <a name="data-manipulation-language-dml-statements"></a>データ操作言語 (DML) ステートメント
|タスク   |関連トピック  |注
|---  |---  |---  |
|INSERT |[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)|ノード テーブルに挿入するはリレーショナル テーブルに挿入すると同じです。 値は、`$node_id`列が自動的に生成します。 値を挿入しようとしています。`$node_id`または`$edge_id`列が、エラーになります。 ユーザーがの値を指定する必要があります`$from_id`と`$to_id`エッジ テーブルへの挿入中に列です。 `$from_id` および`$to_id`は、`$node_id`の特定のエッジに接続するノードの値。  |
|DELETE | [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|リレーショナル テーブルから削除されると、同じ方法でノードまたはエッジ テーブルからデータを削除できます。 ただし、このリリースで制約はありませんエッジ ポイントを削除したノードとノードの削除時に、エッジのカスケード削除はサポートされていないことを確認します。 ノードが削除されると、そのノードへのすべての接続エッジも削除すること、グラフの整合性を維持するをお勧めします。  |
|UPDATE |[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  |ユーザー定義の列の値は、UPDATE ステートメントを使用して更新できます。 内部のグラフ列を更新する`$node_id`、 `$edge_id`、`$from_id`と`$to_id`は許可されていません。  |
|MERGE |[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  |`MERGE` ステートメントは、ノードまたはエッジ テーブルでサポートされていません。  |


### <a name="query-statements"></a>クエリ ステートメント
|タスク   |関連トピック  |注
|---  |---  |---  |
|SELECT |[SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)|ノードとエッジ テーブルとして内部的に格納されます、ノードとエッジ テーブルで SQL Server または Azure SQL データベースのテーブルでサポートされる操作のほとんどをサポートするため  |
|MATCH  | [一致&#40;TRANSACT-SQL&#41;](../../t-sql/queries/match-sql-graph.md)|一致する組み込みは、パターンに一致して、グラフの通過をサポートするために導入されました。  |



## <a name="limitations-and-known-issues"></a>制限事項と既知の問題  
このリリースでのノードとエッジ テーブルで特定の制限があります。
* ローカルまたはグローバル一時テーブルには、ノードまたはエッジ テーブルをすることはできません。
* ノードまたはエッジ テーブルとしては、テーブルの種類とテーブル変数を宣言することはできません。 
* ノードとエッジ テーブルは、システム バージョン管理されたテンポラル テーブルとして作成できません。   
* ノードとエッジ テーブルは、メモリ最適化テーブルにすることはできません。  
* ユーザーには、$from_id と UPDATE ステートメントを使用してエッジの $to_id 列を更新できません。 エッジを接続するノードを更新するには、ユーザーは、新しいノードを指す新しい edge の挿入および削除の前に必要があります。
* データベースをまたがるクエリ グラフのオブジェクトではサポートされていません。 


## <a name="next-steps"></a>次の手順
新しい構文で開始するを参照してください[SQL グラフ データベース - サンプル。](./sql-graph-sample.md)
 

