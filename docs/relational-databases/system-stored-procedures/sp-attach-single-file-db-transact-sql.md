---
title: sp_attach_single_file_db (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_attach_single_file_db
- sp_attach_single_file_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_single_file_db
ms.assetid: 13bd1044-9497-4293-8390-1f12e6b8e952
caps.latest.revision: 68
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6bc8e6d5f9e6e281a970ba42cd604d9f817ab5b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spattachsinglefiledb-transact-sql"></a>sp_attach_single_file_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ ファイルが 1 つだけ格納されているデータベースを現在のサーバーにアタッチします。 **sp_attach_single_file_db**複数のデータ ファイルでは使用できません。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] CREATE DATABASE を使用することをお勧め*database_name* FOR ATTACH 代わりにします。 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。 レプリケートされたデータベースには、このプロシージャを使用しないでください。  
  
> [!IMPORTANT]  
>  不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースのデータベースを使用する前に、実稼働用ではないサーバーでそのデータベースに対し [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_attach_single_file_db [ @dbname= ] 'dbname'  
    , [ @physname= ] 'physical_name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=** ] **'***dbname***'**  
 サーバーにアタッチされるデータベースの名前を指定します。 名前は一意である必要があります。 *dbname*は**sysname**、既定値は NULL です。  
  
 [ **@physname=** ] **'***physical_name***'**  
 物理名、データベース ファイルのパスを含むです。 *physical_name*は**nvarchar (260)**、既定値は NULL です。  
  
> [!NOTE]  
>  この引数は、CREATE DATABASE ステートメントの FILENAME パラメーターにマップされます。 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
 フルテキスト カタログ ファイルを含む [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバー インスタンスにアタッチする場合、カタログ ファイルは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と同様に他のデータベース ファイルと一緒に以前の場所からアタッチされます。 詳細については、「 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 使用して**sp_attach_single_file_db**明示的に使用して、サーバーからデタッチされたデータベースに対してのみ**sp_detach_db**オペレーション データベース、またはコピーします。  
  
 **sp_attach_single_file_db**は単一のログ ファイルのあるデータベースに対してのみ機能します。 ときに**sp_attach_single_file_db**データベースをアタッチ、サーバーに、新しいログ ファイルを作成します。 データベースが読み取り専用の場合、ログ ファイルは、アタッチされる前の場所に作成されます。  
  
> [!NOTE]  
>  データベース スナップショットのデタッチおよびアタッチは行うことができません。  
  
 レプリケートされたデータベースには、このプロシージャを使用しないでください。  
  
## <a name="permissions"></a>権限  
 データベースをアタッチするときにアクセス許可を処理する方法については、次を参照してください。 [CREATE DATABASE &#40;SQL Server TRANSACT-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)です。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] をデタッチした後、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] から現在のサーバーに 1 つのファイルをアタッチします。  
  
```  
USE master;  
GO  
EXEC sp_detach_db @dbname = 'AdventureWorks2012';  
EXEC sp_attach_single_file_db @dbname = 'AdventureWorks2012',   
    @physname =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf';  
```  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
