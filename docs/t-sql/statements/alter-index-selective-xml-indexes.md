---
title: "ALTER INDEX (選択的 XML インデックス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: cca96a8f-7737-42d2-bbcc-03d5f858dcc1
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f875f7d34c568bc1156c5f8bce60d893fce8039
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="alter-index-selective-xml-indexes"></a>ALTER INDEX (選択的 XML インデックス)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  既存の選択的 XML インデックスを変更します。 ALTER INDEX ステートメントは次のアイテムの 1 つ以上を変更します。  
  
-   インデックス パスの一覧 (FOR 句)。  
  
-   名前空間の一覧 (WITH XMLNAMESPACES 句)。  
  
-   インデックス オプション (WITH 句)。  
  
 選択的セカンダリ XML インデックスを変更することはできません。 詳細については、次を参照してください。 [Create、Alter、およびセカンダリ選択的 XML インデックスのドロップ](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER INDEX index_name  
    ON <table_object>   
    [WITH XMLNAMESPACES ( <xmlnamespace_list> )]  
    FOR ( <promoted_node_path_action_list> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
<promoted_node_path_action_list> ::=   
<promoted_node_path_action_item> [, <promoted_node_path_action_list>]  
  
<promoted_node_path_action_item>::=   
<add_node_path_item_action> | <remove_node_path_item_action>  
  
<add_node_path_item_action> ::=  
ADD <path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<remove_node_path_item_action> ::= REMOVE <path_name>   
  
<path_name_or_typed_node_path>::=   
<path_name> | <typed_node_path>  
  
<typed_node_path> ::=   
<node_path> [[AS XQUERY <xsd_type_ext>] | [AS SQL <sql_type>]]  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | 'node()'  
  
<sql_values_node_path_item> ::=   
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type_ext> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::= character_string_literal  
<xml_namespace_prefix> ::= identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY =OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE =OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> 引数  
 *index_name*  
 変更する既存のインデックスの名前です。  
  
 *\<table_object >*  
 インデックスを作成する XML 列が含まれるテーブルを指定します。 次のどちらかの形式を使用します。  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 [WITH XMLNAMESPACES **(** \<xmlnamespace_list > **)**]  
 インデックスを作成するパスで使用される名前空間の一覧を指定します。 WITH XMLNAMESPACES 句の構文の詳細については、次を参照してください。 [WITH XMLNAMESPACES &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/xml/with-xmlnamespaces.md).  
  
 **(** \<Promoted_node_path_action_list > **)**  
 追加または削除するインデックス付きパスの一覧です。  
  
-   **パスを追加します。** パスを追加 (ADD) するときは、CREATE SELECTIVE XML INDEX ステートメントを使用してパスを作成するときと同じ構文を使用します。 CREATE または ALTER ステートメントで指定できるパスについては、次を参照してください。[パスを指定し、選択的 XML インデックスの最適化ヒント](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)です。  
  
-   **パスを削除します。** パスを削除 (REMOVE) するときは、作成時にパスに付けた名前を指定します。  
  
 [で**(** \<index_options > **)**]  
 指定できますのみ\<index_options > FOR 句なし ALTER INDEX を使用するとします。 ALTER INDEX を使用してインデックスのパスを追加または削除する場合、インデックス オプションは引数として無効です。 インデックス オプションについては、次を参照してください。 [CREATE XML INDEX &#40;です。選択的 XML インデックス &#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  ALTER INDEX ステートメントを実行すると、選択的 XML インデックスが常に再構築されます。 サーバーのリソースに対するこの処理の影響を考慮してください。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 ALTER INDEX を実行するには、少なくともテーブルまたはビューに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 ALTER INDEX ステートメントの例を次に示します。 このステートメントは、インデックスの XQuery の部分にパス `'/a/b/m'` を追加し、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md)」のトピックの例で作成したインデックスの SQL の部分からパス `'/a/b/e'` を削除します。 削除するパスは、作成時に指定された名前によって識別されます。  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
);  
```  
  
 次の例では、インデックス オプションを指定する ALTER INDEX ステートメントを示しています。 このステートメントは FOR 句を使用してパスを追加または削除していないため、インデックス オプションを指定できます。  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
PAD_INDEX = ON;  
```  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [作成、変更、および選択的 XML インデックスを削除します。](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [選択的 XML インデックスのパスと最適化ヒントの指定](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  
