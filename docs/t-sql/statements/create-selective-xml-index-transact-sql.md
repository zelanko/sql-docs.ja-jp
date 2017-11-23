---
title: "選択的 XML インデックス (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
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
ms.assetid: 1d769f62-f646-4057-b93a-bf5f90e935ed
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 411d0242510752d82e85425634f057cc3ac2cbb3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-selective-xml-index-transact-sql"></a>CREATE SELECTIVE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  指定したテーブルと XML 列に新しい選択的 XML インデックスを作成します。 選択的 XML インデックスは、クエリを通常行うノードのサブセットにのみインデックスを作成します。そのため、XML インデックス作成とクエリのパフォーマンスが向上します。 選択的セカンダリ XML インデックスを作成することもできます。 詳細については、次を参照してください。 [Create、Alter、およびセカンダリ選択的 XML インデックスのドロップ](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE SELECTIVE XML INDEX index_name  
    ON <table_object> (xml_column_name)  
    [WITH XMLNAMESPACES (<xmlnamespace_list>)]  
    FOR (<promoted_node_path_list>)  
    [WITH (<index_options>)]  
  
<table_object> ::=  
 { [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<promoted_node_path_list> ::=   
<named_promoted_node_path_item> [, <promoted_node_path_list>]  
  
<named_promoted_node_path_item> ::=   
<path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | node()  
  
<sql_values_node_path_item> ::=  
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::=   
character_string_literal  
  
<xml_namespace_prefix> ::=   
identifier  
  
<index_options> ::=   
(   
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> 引数  
 *index_name*  
 作成する新しいインデックスの名前を指定します。 インデックス名は、テーブル内で一意である必要がありますが、データベース内で一意にする必要はありません。 インデックス名の規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *\<table_object >*インデックスに XML 列を含むテーブルです。 次のどちらかの形式を使用します。  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *xml_column_name*  
 インデックスへのパスを含む XML 列の名前です。  
  
 [WITH XMLNAMESPACES **(**\<xmlnamespace_list >**)**] インデックスを作成するパスで使用される名前空間の一覧を示します。 WITH XMLNAMESPACES 句の構文の詳細については、次を参照してください。 [WITH XMLNAMESPACES &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/xml/with-xmlnamespaces.md).  
  
 **(**\<Promoted_node_path_list >**)**省略可能な最適化ヒントを使用してインデックスへのパスの一覧を示します。 パスと、CREATE または ALTER ステートメントで指定できる最適化のヒントについては、次を参照してください。[パスを指定し、選択的 XML インデックスの最適化ヒント](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)です。  
  
 *\<Index_options >*インデックス オプションについては、次を参照してください。 [CREATE XML INDEX &#40;です。選択的 XML インデックス &#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="best-practices"></a>ベスト プラクティス  
 ほとんどの場合、通常の XML インデックスではなく選択的 XML インデックスを作成すると、パフォーマンスが向上し、効率的な保管が可能になります。 ただし、選択的 XML インデックスは、次の条件のいずれかに該当する場合はお勧めしません。  
  
-   多数のノード パスをマップする必要がある場合。  
  
-   不明な要素または不明な位置にある要素のクエリをサポートする必要がある場合。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 制限事項と制約については、次を参照してください。[選択的 XML インデックス &#40;です。SXI &#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 テーブルまたはビューに対する ALTER 権限が必要です。 実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、選択的 XML インデックスを作成するための構文を示しています。 また、インデックスを作成するパスと省略可能な最適化ヒントを指定する構文のいくつかのバリエーションを示します。  
  
```  
CREATE TABLE Tbl ( id INT PRIMARY KEY, xmlcol XML );  
GO  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()',  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON,  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
);  
```  
  
 次の例では、WITH XMLNAMESPACES 句を使用しています。  
  
```  
CREATE SELECTIVE XML INDEX on T1(C1)  
WITH XMLNAMESPACES ('http://www.tempuri.org/' as myns)  
FOR ( path1 = '/myns:book/myns:author/text()' );  
```  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [作成、変更、および選択的 XML インデックスを削除します。](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [選択的 XML インデックスのパスと最適化ヒントの指定](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  

