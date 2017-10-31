---
title: "OBJECT_SCHEMA_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 621a58fcc00b95626f3e4eb7d34d79af608436fe
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="objectschemaname-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  スキーマ スコープ オブジェクトのデータベース スキーマ名を返します。 スキーマ スコープ オブジェクトの一覧は、次を参照してください。 [sys.objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>引数  
 *object_id*  
 使用するオブジェクトの ID を指定します。 *object_id*は**int**または現在のデータベース コンテキストで指定されたデータベースでは、スキーマ スコープ オブジェクトであると見なされます。  
  
 *database_id*  
 オブジェクトを検索するデータベースの ID を指定します。 *database_id*は**int**です。  
  
## <a name="return-types"></a>戻り値の型  
 **sysname**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。 呼び出し先データベースの AUTO_CLOSE オプションが ON に設定されている場合、データベースが開きます。  
  
 ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (OBJECT_SCHEMA_NAME など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する ANY 権限が必要です。 データベース ID を指定するには、そのデータベースの CONNECT 権限を持っているか、ゲスト アカウントが有効である必要があります。  
  
## <a name="remarks"></a>解説  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 詳細については、次を参照してください。[式](../../t-sql/language-elements/expressions-transact-sql.md)と[場所](../../t-sql/queries/where-transact-sql.md)です。  
  
 このシステム関数が返す結果セットには、現在のデータベースの照合順序が使用されます。  
  
 場合*database_id*が指定されていない、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]であると推定*object_id*は、現在のデータベースのコンテキストでします。 参照するクエリ、 *object_id*別のデータベースでは、NULL または不適切な結果を返します。 たとえば、次のクエリでは、現在のデータベースのコンテキストは[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]は、クエリの FROM 句に指定されたデータベースではなく、このデータベースの指定されたオブジェクト ID のオブジェクト スキーマ名を返します。 したがって、正しくない情報が返されます。  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 次の例では、`master` 関数で `OBJECT_SCHEMA_NAME` データベースのデータベース ID を指定し、正確な結果を返します。  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. オブジェクト スキーマ名とオブジェクト名を取得する  
 この例では、アドホック ステートメントでも準備されたステートメントでもない、キャッシュされたすべてのクエリ プランについて、オブジェクト スキーマ名、オブジェクト名、SQL テキストを返します。  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>B. 3 つの要素で構成されたオブジェクト名を取得する  
 この例では、データベース名、スキーマ名、およびオブジェクト名と共に、すべてのデータベースのすべてのオブジェクトの統計を示す `sys.dm_db_index_operational_stats` 動的管理ビューの残りのすべての列を返します。  
  
```  
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-id-transact-sql.md)   
 [OBJECT_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-name-transact-sql.md)   
 [セキュリティ保護可能](../../relational-databases/security/securables.md)  
  
  

