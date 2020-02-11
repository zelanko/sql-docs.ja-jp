---
title: sp_tables (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables
- sp_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables
ms.assetid: 787a2fa5-87a1-49bd-938b-6043c245f46b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71aaa9e52cfca8435501695a4ebf60b2a6aa6ee4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096052"
---
# <a name="sp_tables-transact-sql"></a>sp_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境でクエリを実行できるオブジェクトの一覧を返します。 これは、シノニムオブジェクトを除くすべてのテーブルまたはビューを意味します。  
  
> [!NOTE]  
>  シノニムのベースオブジェクトの名前を確認するには、クエリを実行[します。](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_tables [ [ @table_name = ] 'name' ]   
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @table_type = ] "type" ]   
     [ , [@fUsePattern = ] 'fUsePattern'];  
```  
  
## <a name="arguments"></a>引数  
`[ @table_name = ] 'name'`カタログ情報を返すために使用するテーブルです。 *名前*は**nvarchar (384)**,、既定値は NULL です。 ワイルドカードパターンマッチングがサポートされています。  
  
`[ @table_owner = ] 'owner'`カタログ情報を返すために使用するテーブルのテーブル所有者を示します。 *owner*は**nvarchar (384)**,、既定値は NULL です。 ワイルドカードパターンマッチングがサポートされています。 所有者が指定されていない場合は、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、指定された名前のテーブルが現在のユーザーによって所有されている場合、そのテーブルの列が返されます。 所有者が指定されておらず、現在のユーザーが指定された名前のテーブルを所有していない場合、このプロシージャは、データベース所有者が所有する、指定された名前のテーブルを検索します。 そのテーブルが存在する場合、そのテーブルの列が返されます。  
  
`[ @table_qualifier = ] 'qualifier'`テーブル修飾子の名前を指定します。 *修飾子*は**sysname**,、既定値は NULL です。 さまざまな DBMS 製品では、3つの要素で構成するテーブル (_修飾子_) がサポート**しています。**_所有者_**。**_名前_)。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列はデータベース名を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
``[ , [ @table_type = ] "'type', 'type'" ]``指定されているテーブル型のすべてのテーブルに関する情報を提供する、コンマで区切られた値の一覧です。 これには、**テーブル**、**システムテーブル**、および**ビュー**が含まれます。 *型*は**varchar (100)**,、既定値は NULL です。  
  
> [!NOTE]  
>  単一引用符は各テーブル型を囲む必要があり、二重引用符はパラメーター全体を囲む必要があります。 テーブル型は大文字にする必要があります。 SET QUOTED_IDENTIFIER が ON の場合は、各単一引用符を2倍にし、パラメーター全体を単一引用符で囲む必要があります。  
  
`[ @fUsePattern = ] 'fUsePattern'`アンダースコア (_)、パーセント (%)、および角かっこ ([または]) の各文字がワイルドカード文字として解釈されるかどうかを決定します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *Fusepattern*は**ビット**,、既定値は1です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|テーブル修飾子の名前。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列はデータベース名を表します。 このフィールドは NULL にすることができます。|  
|**TABLE_OWNER**|**sysname**|テーブル所有者の名前。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列は、テーブルを作成したデータベースユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名。 このフィールドは常に値を返します。|  
|**TABLE_TYPE**|**varchar(32)**|テーブル、システムテーブル、またはビュー。|  
|**」**|**varchar (254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はこの列の値を返しません。|  
  
## <a name="remarks"></a>解説  
 相互運用性を最大にするために、ゲートウェイクライアントは SQL-92-標準の SQL パターン照合 (% と _ ワイルドカード文字) のみを想定する必要があります。  
  
 現在のユーザーの特定のテーブルに対する読み取りまたは書き込みアクセスに関する特権情報は、常にチェックされません。 そのため、アクセスは保証されません。 この結果セットには、テーブルとビューだけでなく、これらの型をサポートする DBMS 製品へのゲートウェイのシノニムと別名も含まれています。 **Sp_server_info**の結果セットで server 属性**ACCESSIBLE_TABLES**が Y の場合は、現在のユーザーがアクセスできるテーブルだけが返されます。  
  
 **sp_tables**は、ODBC の**sqltables**に相当します。 返される結果は、 **TABLE_TYPE**、 **TABLE_QUALIFIER**、 **TABLE_OWNER**、および**TABLE_NAME**順に並べ替えられます。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>A. 現在の環境でクエリされるオブジェクトの一覧を返す  
 次の例では、現在の環境でクエリを実行できるオブジェクトの一覧を返します。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="b-returning-information-about-the-tables-in-a-specified-schema"></a>B. 指定されたスキーマ内のテーブルに関する情報を返す  
 次の例では、`Person` データベース内の [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] スキーマに属するテーブルに関する情報が返されます。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_tables   
   @table_name = '%',  
   @table_owner = 'Person',  
   @table_qualifier = 'AdventureWorks2012';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-a-list-of-objects-that-can-be-queried-in-the-current-environment"></a>C. 現在の環境でクエリされるオブジェクトの一覧を返す  
 次の例では、現在の環境でクエリを実行できるオブジェクトの一覧を返します。  
  
```  
EXEC sp_tables ;  
```  
  
### <a name="d-returning-information-about-the-tables-in-a-specified-schema"></a>D. 指定されたスキーマ内のテーブルに関する情報を返す  
 次の例では、 `AdventureWorksPDW201`データベース内のディメンションテーブルに関する情報を返します。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_tables   
   @table_name = 'Dim%',  
   @table_owner = 'dbo',  
   @table_qualifier = 'AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-synonyms-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

