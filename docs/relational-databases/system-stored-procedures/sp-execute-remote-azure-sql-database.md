---
title: sp_execute_remote (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/01/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ffa47c5238053d7f94998dfef6a3a62df38f183a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spexecuteremote-azure-sql-database"></a>sp_execute_remote (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  実行、[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントで、単一のリモートの Azure SQL Database または水平方向のパーティション分割構成のシャードとして機能しているデータベースのセット。  
  
 ストアド プロシージャは、柔軟なクエリ機能の一部です。  参照してください[Azure SQL Database の柔軟なデータベース クエリの概要](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)と[分割 (水平パーティション分割) の柔軟なデータベース クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_execute_remote [ @data_source_name = ] datasourcename  
[ , @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>引数  
 [ @data_source_name =] *datasourcename*  
 ステートメントが実行された外部データ ソースを識別します。 参照してください[外部データ ソースの作成 & #40 です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-external-data-source-transact-sql.md)。 外部データ ソースは、"RDBMS"または"SHARD_MAP_MANAGER"の型指定できます。  
  
 [ @stmt= ] *ステートメント*  
 Unicode 文字列が含まれて、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチです。 @stmt Unicode 定数または Unicode 変数のいずれかにする必要があります。 + 演算子で 2 つの文字列を連結するなどの複雑な Unicode 式は使用できません。 文字定数も使用できません。 Unicode 定数が指定されている場合に付ける必要があります、 **N**です。たとえば、Unicode 定数**N 'sp_who'** 有効ですが、文字定数 **'sp_who'** はありません。 文字列のサイズは、データベース サーバーで利用可能なメモリにより制限されます。 64 ビット サーバーに、文字列のサイズは 2 GB の最大サイズに制限**nvarchar (max)** です。  
  
> [!NOTE]  
>  @stmt たとえば、名前の変数と同じ形式を持つパラメーターを含めることができます。 `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 @stmt に含める各パラメーターには、@params パラメーター定義リストとパラメーター値リストの両方に、対応するエントリが存在する必要があります。  
  
 [ @params= ] N'@*parameter_name**data_type* [ ,... *n* ] '  
 @stmt に埋め込まれたすべてのパラメーターの定義が含まれている 1 つの文字列を指定します。この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 *n*追加のパラメーター定義を示すプレース ホルダーです。 すべてのパラメーターで指定された@stmtmustで定義されている@paramsです。 場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに@stmtパラメーターを含まない@paramsは必要ありません。 このパラメーターの既定値は NULL です。  
  
 [ @param1=] '*value1*'  
 パラメーター文字列に定義する最初のパラメーターの値を指定します。 Unicode 定数または Unicode 変数を指定できます。 @stmt に含まれる各パラメーターに対して、パラメーター値を指定する必要があります。値が必要なときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに@stmtパラメーターを持たない。  
  
 *n*  
 追加するパラメーター値のプレースホルダーです。 定数または変数のみを指定できます。 関数などの複雑な式や演算子を使用した式は指定できません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 最初の SQL ステートメントからの結果セットを返します。  
  
## <a name="permissions"></a>権限  
 `ALTER ANY EXTERNAL DATA SOURCE` 権限が必要です。  
  
## <a name="remarks"></a>解説  
 `sp_execute_remote` 上記の「構文」の説明に従って、特定の順序でパラメーターを入力する必要があります。 パラメーターを不適切な順序で入力した場合、エラー メッセージが表示されます。  
  
 `sp_execute_remote`として動作は同じ[EXECUTE &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/execute-transact-sql.md)に関してバッチおよび名前のスコープです。 TRANSACT-SQL ステートメントまたはバッチ、sp_execute_remote に*@stmt*パラメーターは、sp_execute_remote ステートメントが実行されるまでコンパイルされません。  
  
 `sp_execute_remote` 行を生成するリモートのデータベースの名前を含む ' $ShardName' という名前が結果セットに追加の列を追加します。  
  
 `sp_execute_remote`同様に使用できる[sp_executesql & #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md)。  
  
## <a name="examples"></a>使用例  
### <a name="simple-example"></a>簡単な例  
 次の例では、作成し、リモート データベースで単純な SELECT ステートメントを実行します。  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>複数のパラメーターの例  
ユーザー データベース、master データベースの管理者の資格情報を指定するには、データベース スコープ資格情報を作成します。 Master データベースをポイントし、データベース スコープ資格情報を指定する外部データ ソースを作成します。 次のように、ユーザー データベースでの使用例を実行し、 `sp_set_firewall_rule` master データベース内のプロシージャです。 `sp_set_firewall_rule`手順 3 つのパラメーターとが必要です、`@name`パラメーターを Unicode になります。

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>参照:

[データベース スコープを作成する資格情報](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[外部データ ソース (TRANSACT-SQL) を作成します。](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
