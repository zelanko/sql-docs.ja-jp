---
title: "パーティション構成 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION SCHEME
- SCHEME
- PARTITION SCHEME
- CREATE_PARTITION_SCHEME_TSQL
- SCHEME_TSQL
- PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- partitioned indexes [SQL Server], schemes
- partitioned tables [SQL Server], schemes
- CREATE PARTITION SCHEME statement
- partition schemes [SQL Server], creating
- filegroups [SQL Server], partitions
- partitioned indexes [SQL Server], filegroups
- partitioned tables [SQL Server], filegroups
- mapping partitions [SQL Server]
ms.assetid: 5b21c53a-b4f4-4988-89a2-801f512126e4
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 13bd8b623604f8bfe93dcf4483c65be14f43f003
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-partition-scheme-transact-sql"></a>CREATE PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  パーティション テーブルまたはパーティション インデックスのパーティションをファイル グループにマップする構成を、現在のデータベース内に作成します。 パーティション テーブルまたはパーティション インデックスのパーティションの数とドメインは、パーティション関数で決まります。 パーティション関数で最初に作成する必要があります、 [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md)パーティション構成を作成する前にステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE PARTITION SCHEME partition_scheme_name  
AS PARTITION partition_function_name  
[ ALL ] TO ( { file_group_name | [ PRIMARY ] } [ ,...n ] )  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_scheme_name*  
 パーティション構成の名前です。 パーティション構成の名前のデータベース内で一意であるし、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *partition_function_name*  
 パーティション構成を使用するパーティション関数の名前です。 パーティション関数によって作成されたパーティションは、パーティション構成で指定されたファイル グループにマップされます。 *partition_function_name*データベースに既に存在する必要があります。 1 つのパーティションに FILESTREAM ファイル グループと非 FILESTREAM ファイル グループの両方を含めることはできません。  
  
 ALL  
 すべてのパーティションがで提供されるファイル グループにマップすることを示す*file_group_name*、またはプライマリ ファイル グループに場合**[**プライマリ**]**が指定されています。 ALL を指定した場合は、1 つだけ*file_group_name*を指定できます。  
  
 *file_group_name* | **[**プライマリ**]** [ **、***...n*]  
 によって指定されたパーティションを保持するファイル グループの名前を指定*partition_function_name*です。 *file_group_name*データベースに既に存在する必要があります。  
  
 場合**[**プライマリ**]**を指定すると、プライマリ ファイル グループにパーティションを格納します。 ALL を指定した場合は、1 つだけ*file_group_name*を指定できます。 以降では、パーティション 1 でのファイル グループが表示される順序でのファイル グループに割り当てられているパーティション [**、***...n*] です。 同じ*file_group_name*で 1 つ以上の時間を指定することができます [**、***...n*] です。 場合 *n* で指定されたパーティションの数を保持するのに十分ではない*partition_function_name*、CREATE PARTITION SCHEME がエラーで失敗します。  
  
 場合*partition_function_name*生成ファイル グループよりも少ないパーティション、割り当てられていない最初のファイル グループが NEXT USED の場合、マークされているし、情報メッセージは、NEXT USED ファイル グループの名前が表示されます。 ALL を指定した場合、唯一*file_group_name*これの NEXT USED プロパティを保持*partition_function_name*です。 ALTER PARTITION FUNCTION ステートメントで追加のパーティションを作成した場合は、NEXT USED ファイル グループがそのパーティションを受け取ります。 割り当てられていないファイル グループを追加作成して新しいパーティションを保持するには、ALTER PARTITION SCHEME を使用します。  
  
 プライマリ ファイル グループを指定すると*file_group_name* [1**、***...n*]、プライマリように区切る必要があります**[**プライマリ**]**キーワードであるため、します。  
  
 唯一のプライマリがサポートされている[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。 例 E 以下を参照してください。 
  
## <a name="permissions"></a>Permissions  
 CREATE PARTITION SCHEME を実行する場合、下記の権限を使用することができます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   データベースの CONTROL 権限または ALTER 権限 (パーティション構成はこのデータベース内で作成)。  
  
-   データベースのサーバーの CONTROL SERVER 権限または ALTER ANY DATABASE 権限 (パーティション構成はこのデータベースで作成)。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-partition-scheme-that-maps-each-partition-to-a-different-filegroup"></a>A. 各パーティションを異なるファイル グループにマップするパーティション構成を作成する  
 次の例では、テーブルまたはインデックスを 4 つのパーティションに分割するパーティション関数を作成します。 その後、4 つのパーティションそれぞれを保持するファイル グループを指定するパーティション構成を作成します。 この例では、ファイル グループが既にデータベースに存在していると仮定しています。  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
TO (test1fg, test2fg, test3fg, test4fg);  
```  
  
 パーティション関数を使用するテーブルのパーティション`myRangePF1`パーティション分割列**col1**次の表に示すように割り当てられます。  
  
||||||  
|-|-|-|-|-|  
|**ファイル グループ**|`test1fg`|`test2fg`|`test3fg`|`test4fg`|  
|**パーティション**|1|2|3|4|  
|**値**|**col1** <= `1`|**col1**  >  `1` AND **col1** <= `100`|**col1**  >  `100` AND **col1** <= `1000`|**col1** > `1000`|  
  
### <a name="b-creating-a-partition-scheme-that-maps-multiple-partitions-to-the-same-filegroup"></a>B. 複数のパーティションを同じファイル グループにマップするパーティション構成を作成する  
 すべてのパーティションを同じファイル グループにマップする場合は、ALL キーワードを使用します。 ただし、複数の (すべてではない) パーティションを同じファイル グループにマップする場合は、次の例に示すように、ファイル グループ名を繰り返し記述する必要があります。  
  
```  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS2  
AS PARTITION myRangePF2  
TO ( test1fg, test1fg, test1fg, test2fg );  
```  
  
 パーティション関数を使用するテーブルのパーティション`myRangePF2`パーティション分割列**col1**次の表に示すように割り当てられます。  
  
||||||  
|-|-|-|-|-|  
|**ファイル グループ**|`test1fg`|`test1fg`|`test1fg`|`test2fg`|  
|**パーティション**|1|2|3|4|  
|**値**|**col1** <= `1`|**col1** > 1 AND **col1** <= `100`|**col1**  >  `100` AND **col1** <= `1000`|**col1** > `1000`|  
  
### <a name="c-creating-a-partition-scheme-that-maps-all-partitions-to-the-same-filegroup"></a>C. すべてのパーティションを同じファイル グループにマップするパーティション構成を作成する  
 次の例では、これまでの例と同じパーティション関数を作成し、すべてのパーティションを同じファイル グループにマップするパーティション構成を作成します。  
  
```  
CREATE PARTITION FUNCTION myRangePF3 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS3  
AS PARTITION myRangePF3  
ALL TO ( test1fg );  
```  
  
### <a name="d-creating-a-partition-scheme-that-specifies-a-next-used-filegroup"></a>D. 'NEXT USED' ファイル グループを指定するパーティション構成を作成する  
 次の例では、これまでの例と同じパーティション関数を作成し、関連するパーティション関数によって作成されるパーティションよりも多くのファイル グループを一覧するパーティション構成を作成します。  
  
```  
CREATE PARTITION FUNCTION myRangePF4 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS4  
AS PARTITION myRangePF4  
TO (test1fg, test2fg, test3fg, test4fg, test5fg)  
```  
  
 このステートメントを実行すると、次のメッセージが返されます。  
  
パーティション構成 'myRangePS4' が正常に作成されました。 'test5fg' は、パーティション構成 'myRangePS4' で使用するファイル グループの [次へ] としてマークされます。  
  
  
 場合はパーティション関数`myRangePF4`パーティション、ファイル グループを追加する変更は`test5fg`新しく作成されたパーティションを受信します。  

### <a name="e-creating-a-partition-schema-only-on-primary---only-primary-is-supported-for-includesqldbesaincludessqldbesa-mdmd"></a>E. パーティション スキーマを作成するだけでプライマリ - プライマリのみでサポートされて[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]

 次の例では、テーブルまたはインデックスを 4 つのパーティションに分割するパーティション関数を作成します。 パーティション構成のプライマリ ファイル グループにすべてのパーティションが作成されたことを指定するが、作成されます。  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
ALL TO ( [PRIMARY] );  
```
   
## <a name="see-also"></a>参照  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION SCHEME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [パーティション テーブルとインデックスを作成します。](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md)   
 [sys.partition_schemes と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [sys.data_spaces と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

