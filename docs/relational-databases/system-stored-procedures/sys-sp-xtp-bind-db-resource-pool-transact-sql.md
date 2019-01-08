---
title: sys.sp_xtp_bind_db_resource_pool (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xtp_bind_db_resource_pool_TSQL
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool_TSQL
- sys.sp_xtp_bind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool
ms.assetid: c2a78073-626b-4159-996e-1808f6bfb6d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2e8182a0fca11105541f8dd435f352ba0d393731
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391655"
---
# <a name="sysspxtpbinddbresourcepool-transact-sql"></a>sys.sp_xtp_bind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  指定されたリソース プールに指定された[!INCLUDE[hek_2](../../includes/hek-2-md.md)] データベースをバインドします。 データベースおよびリソース プールはどちらも `sys.sp_xtp_bind_db_resource_pool` を実行する前に存在している必要があります。  
  
 このシステム ストアド プロシージャは、resource_pool_name で識別されるリソース ガバナー プールと database_name によって識別されるデータベースのバインドを作成します。 データベースは、バインド時にメモリ最適化オブジェクトを持つ必要はありません。 メモリ最適化オブジェクトが存在しない場合、リソース プールからメモリは取得されません。 このバインドは、以下で説明するように[!INCLUDE[hek_2](../../includes/hek-2-md.md)] アロケーターで割り当てられたメモリを管理するためにリソース ガバナーで使用されます。  
  
 所定のデータベースに既にバインドが存在する場合、このプロシージャはエラーを返します。  どのような場合でも、データベースがアクティブなバインドを複数持つことはできません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  
## <a name="syntax"></a>構文  
  
```sql  
sys.sp_xtp_bind_db_resource_pool 'database_name', 'resource_pool_name'  
```  
  
## <a name="arguments"></a>引数  
 database_name  
 既存の[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 対応データベースの名前。  
  
 resource_pool_name  
 既存のリソース プールの名前。  
  
## <a name="messages"></a>メッセージ  
 エラーが発生すると、`sp_xtp_bind_db_resource_pool` は以下のメッセージのいずれかを返します。  
  
 **データベースは存在しません**  
 Database_name は既存のデータベースを参照する必要があります。 指定した ID のデータベースが存在しない場合、次のメッセージが返されます。   
*データベース ID %d は存在しません。このバインディングの有効なデータベース ID を使用してください。*  
  
```  
Msg 911, Level 16, State 18, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB213' does not exist. Make sure that the name is entered correctly.  
```  
  
**データベースは、システム データベースは、**  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] テーブルをシステム データベースに作成することはできません。  そのため、そのようなデータベースに[!INCLUDE[hek_2](../../includes/hek-2-md.md)] メモリのバインドを作成するのは無効です。  次のエラーが返されます。  
*Database_name %s は、システム データベースを参照します。リソース プールは、ユーザー データベースにのみバインド可能性があります。*  
  
```  
Msg 41371, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Binding to a resource pool is not supported for system database 'master'. This operation can only be performed on a user database.  
```  
  
**リソース プールが存在しません**  
 resource_pool_name で識別されるリソース プールは、`sp_xtp_bind_db_resource_pool` を実行する前に存在している必要があります。  指定した ID のプールが存在しない場合、次のエラーが返されます。  
*リソース プール %s は存在しません。有効なリソース プールの名前を入力してください。*  
  
```  
Msg 41370, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Resource pool 'Pool_Hekaton' does not exist or resource governor has not been reconfigured.  
```  
  
**Pool_name が予約されたシステム プールには**  
 プール名"INTERNAL"および"DEFAULT"はシステム プール用に予約されています。  明示的にデータベースをこれらにバインドするのは無効です。  システム プール名を入力した場合、次のエラーが返されます。  
*リソース プール %s は、システム リソース プールです。この手順を使用してデータベースにシステム リソース プールは明示的にバインドしないことがあります。*  
  
```  
Msg 41373, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB' cannot be explicitly bound to the resource pool 'internal'. A database can only be bound only to a user resource pool.  
```  
  
**データベースは既に別のリソース プールにバインドされています**  
 データベースにバインドできるのは、1 度に 1 つのリソース プールだけです。 データベースを別のリソース プールにバインドする前に、リソース プールに対するデータベースのバインドを明示的に削除する必要があります。 参照してください[sys.sp_xtp_unbind_db_resource_pool &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)します。  
*データベース %s は、既にをリソース プール %s にバインドされています。新しいバインドを作成する前にバインドを解除する必要があります。*  
  
```  
Msg 41372, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 54  
Database 'Hekaton_DB' is currently bound to a resource pool. A database must be unbound before creating a new binding.  
```  
  
 成功すると、`sp_xtp_bind_db_resource_pool` は次のメッセージを返します。  
  
**バインドに成功**  
 成功すると、次の成功メッセージを返します。このメッセージは SQL ERRORLOG に記録されます。  
*ID %d のデータベースと ID %d のリソース プール間でリソースのバインドが正常に作成されました。*  
  
## <a name="examples"></a>使用例  
A.  次のコード例は、リソース プール Pool_Hekaton にデータベース Hekaton_DB をバインドします。  
  
```sql  
sys.sp_xtp_bind_db_resource_pool N'Hekaton_DB', N'Pool_Hekaton'  
```  
 
 バインドは、データベースが次にオンラインになったときに有効になります。  
 
 B. 上記の例をいくつかの基本的なチェックを含むの展開の例です。  次の実行[!INCLUDE[tsql](../../includes/tsql-md.md)]で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]\:
 
```sql
DECLARE @resourcePool sysname = N'Pool_Hekaton';
DECLARE @database sysname = N'Hekaton_DB';

-- Check whether resource pool exists
IF NOT EXISTS (
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = @resourcePool
    )
BEGIN
    SELECT N'Resource pool "' + @resourcePool + N'" does not exist or resource governor has not been reconfigured.';
END
-- Check whether database is already bound to a resource pool
ELSE IF EXISTS (
    SELECT p.name
    FROM sys.databases d
    JOIN sys.resource_governor_resource_pools p
    ON d.resource_pool_id = p.pool_id
    WHERE d.name = @database
    )
BEGIN
    SELECT N'Database "' + @database + N'" is currently bound to resource pool "' + @resourcePool  + N'". A database must be unbound before creating a new binding.';
END
-- Bind resource pool to database.
ELSE BEGIN
    EXEC sp_xtp_bind_db_resource_pool @database, @resourcePool; 
END 
``` 
  
## <a name="requirements"></a>必要条件  
  
-   `database_name` で指定するデータベースと `resource_pool_name` で指定するリソース プールはどちらも、バインドする前に存在している必要があります。  
  
-   CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データベースを作成してリソース プールにバインドする方法については、「](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_unbind_db_resource_pool &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  
