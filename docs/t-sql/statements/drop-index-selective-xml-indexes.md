---
title: "DROP INDEX (選択的 XML インデックス) |Microsoft ドキュメント"
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
f1_keywords: DROP XML INDEX statement
dev_langs: TSQL
ms.assetid: 4779ae84-e5f4-4d04-8fc1-e24a6631b428
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 573003dda4029b73bc9cf7a59a496738adbe14d1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="drop-index-selective-xml-indexes"></a>DROP INDEX (選択的 XML インデックス)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  既存の選択的 XML インデックスまたは内のセカンダリ選択的 XML インデックスを削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、「[選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP INDEX index_name ON <object>  
    [ WITH ( <drop_index_option> [ ,...n ] ) ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]   
        table_or_view_name  
}  
  
<drop_index_option> ::=  
{  
    MAXDOP = max_degree_of_parallelism  
    | ONLINE = { ON | OFF }  
}  
```  
  
##  <a name="Arguments"></a> 引数  
 *index_name*  
 削除する既存のインデックスの名前です。  
  
 *\<オブジェクト >*インデックス付き XML 列を含むテーブルです。 次のどちらかの形式を使用します。  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *\<drop_index_option >*ドロップ インデックス オプションについては、次を参照してください。 [DROP INDEX &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-index-transact-sql.md).  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 DROP INDEX を実行するには、少なくともテーブルまたはビューに対する ALTER 権限が必要です。 この権限は、固定サーバー ロール sysadmin と、固定データベース ロール db_ddladmin および db_owner に既定で許可されています。  
  
## <a name="example"></a>例  
 DROP INDEX ステートメントの例を次に示します。  
  
```  
DROP INDEX sxi_index ON tbl;  
```  
  
## <a name="see-also"></a>参照  
 [選択的 XML インデックス &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [選択的 XML インデックスの作成、変更、および削除](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  

