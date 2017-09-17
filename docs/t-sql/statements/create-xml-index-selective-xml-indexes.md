---
title: "CREATE XML INDEX (選択的 XML インデックス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1f510151-41d5-45c2-9cd0-b1ca0246fffe
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 02b6c4b19007ecce500046ce6f3824abf9956309
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-xml-index-selective-xml-indexes"></a>CREATE XML INDEX (選択的 XML インデックス)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  既存の選択的 XML インデックスによってインデックスが既に作成されている単一のパスに、新しい選択的セカンダリ XML インデックスを作成します。 選択的プライマリ XML インデックスを作成することもできます。 詳細については、次を参照してください。 [Create、Alter、および選択的 XML インデックスのドロップ](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE XML INDEX index_name  
    ON <table_object> ( xml_column_name )  
    USING XML INDEX sxi_index_name  
    FOR ( <xquery_or_sql_values_path> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<xquery_or_sql_values_path>::=   
<path_name>   
  
<path_name> ::=   
character string literal  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
xmlnamespace_uri AS xmlnamespace_prefix  
  
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
  
 ON  *\<table_object >*インデックスに XML 列を含むテーブルです。 次の形式を使用できます。  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
 *xml_column_name*  
 インデックスを作成するパスが含まれる XML 列の名前を指定します。  
  
 USING XML INDEX *sxi_index_name*  
 選択的 XML インデックスの名前を指定します。  
  
 **(** \<Xquery_or_sql_values_path > **)**セカンダリ選択的 XML インデックスを作成する対象のインデックス付きパスの名前を指定します。 インデックスを作成するパスは、CREATE SELECTIVE XML INDEX ステートメントで割り当てられた名前です。 詳細については、「[CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md)」を参照してください。  
  
 \<Index_options > インデックス オプションについては、次を参照してください。 [CREATE XML INDEX](../../t-sql/statements/create-xml-index-selective-xml-indexes.md)です。  
  
## <a name="remarks"></a>解説  
 ベース テーブルの各 XML 列に複数の選択的セカンダリ XML インデックスを作成できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 XML 列に選択的セカンダリ XML インデックスを作成するには、その列に選択的 XML インデックスが存在している必要があります。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 テーブルまたはビューに対する ALTER 権限が必要です。 実行するには、 **sysadmin** 固定サーバー ロール、または **db_ddladmin** 固定データベース ロールおよび **db_owner** 固定データベース ロールのメンバーである必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、パス `pathabc`に選択的セカンダリ XML インデックスを作成します。 インデックスへのパスは、割り当てられた名前、 [CREATE SELECTIVE XML INDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR ( pathabc );  
```  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [選択的セカンダリ XML インデックスの作成、変更、および削除](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)  
  
  


