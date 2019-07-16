---
title: sp_detach_db (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/30/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_detach_db
- sp_detach_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_db
- detaching databases [SQL Server]
ms.assetid: abcb1407-ff78-4c76-b02e-509c86574462
author: stevestein
ms.author: sstein
ms.openlocfilehash: eec8b91bbb7d90483b627aebddb7088bc80cb1ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912892"
---
# <a name="spdetachdb-transact-sql"></a>sp_detach_db (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンスから現在使用されていないデータベースを切り離します。必要に応じて、切り離す前に、すべてのテーブルに対して UPDATE STATISTICS を実行します。  
  
> [!IMPORTANT]  
>  レプリケートしたデータベースをデタッチする場合、パブリッシュを解除する必要があります。 詳細については、このトピックの後半の「解説」セクションを参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_detach_db [ @dbname= ] 'database_name'   
    [ , [ @skipchecks= ] 'skipchecks' ]   
    [ , [ @keepfulltextindexfile = ] 'KeepFulltextIndexFile' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @dbname = ] 'database_name'` デタッチするデータベースの名前です。 *database_name*は、 **sysname**値、既定値は NULL です。  
  
`[ @skipchecks = ] 'skipchecks'` スキップまたは統計の更新プログラムを実行するかどうかを指定します。 *skipchecks*は、 **nvarchar (10)** 値、既定値は NULL です。 UPDATE STATISTICS をスキップするには、指定**true**します。 UPDATE STATISTICS を明示的に実行する指定**false**します。  
  
 既定では、テーブルおよびインデックス内のデータに関する情報を更新する UPDATE STATISTICS を実行します。 UPDATE STATISTICS の実行は、データベースを読み取り専用メディアに移動する場合に使用すると便利です。  
  
`[ @keepfulltextindexfile = ] 'KeepFulltextIndexFile'` デタッチされているデータベースに関連付けられているフルテキスト インデックス ファイルをデータベースの中に削除しないを指定します。 操作をデタッチします。 *KeepFulltextIndexFile*は、 **nvarchar (10)** 値、既定値は**true**します。 場合*KeepFulltextIndexFile*は**false**データベースに関連付けられているフルテキスト インデックスのすべてのファイルおよびデータベースが読み取り専用でない限り、フルテキスト インデックスのメタデータを削除します。 NULL の場合、または**true**、フルテキスト関連するメタデータが保持されます。  
  
> [!IMPORTANT]
>  **@keepfulltextindexfile** パラメーターは将来のバージョンで削除される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 新しい開発作業でこのパラメーターを使用しないようにし、できるだけ早くこのパラメーターを使用されているアプリケーションを変更します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 データベースがデタッチされると、そのすべてのメタデータが削除されます。 データベースが、任意のログイン アカウントの既定のデータベースであった場合**マスター**既定のデータベースになります。  
  
> [!NOTE]  
>  すべてのログイン アカウントの既定のデータベースを表示する方法については、次を参照してください。 [sp_helplogins &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)します。 使用することが必要なアクセス許可があれば、 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)に新しい既定のデータベースをログインに割り当てます。  
  
## <a name="restrictions"></a>制限  
 次のいずれかに該当する場合、データベースをデタッチできません。  
  
-   データベースは現在使用中です。 詳細については、このトピックの「「排他アクセスを取得する」を参照してください。  
  
-   レプリケートされる場合、データベースはパブリッシュされます。  
  
     実行してパブリッシングを無効にする必要があります、データベースをデタッチする前に[sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)します。  
  
    > [!NOTE]  
    >  **sp_replicationdboption**を使用できない場合、 [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)を実行してレプリケーションを削除できます。  
  
-   データベースに、データベース スナップショットが存在する。  
  
     データベースをデタッチするには、すべてのデータベース スナップショットを削除する必要があります。 詳細については、「 [データベース スナップショットの削除 &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)の同一または別のインスタンスに再度アタッチすることができます。  
  
    > [!NOTE]  
    >  データベース スナップショットのデタッチおよびアタッチは行うことができません。  
  
-   データベースがミラー化されている。  
  
     データベース ミラーリング セッションが終了するまで、データベースをデタッチできません。 詳細については、「 [データベース ミラーリングの削除 &#40;SQL Server&#41;](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md)」を参照してください。  
  
-   データベースに問題がある。  
  
     データベースをデタッチする前に、問題のあるデータベースを緊急モードに設定する必要があります。 データベースを緊急モードに設定する方法の詳細については、「 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
  
-   データベースがシステム データベースである。  
  
## <a name="obtaining-exclusive-access"></a>排他アクセスの取得  
 データベースをデタッチするには、データベースへの排他アクセスが必要です。 デタッチするデータベースが使用しての場合、デタッチする前に、データベースを排他アクセスを取得する SINGLE_USER モードに設定します。  
  
 たとえば、次`ALTER DATABASE`ステートメントへの排他アクセスの取得、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースの現在のすべてのユーザーがデータベースから切断した後。  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012  
SET SINGLE_USER;  
GO  
```  
  
> [!NOTE]  
>  現在ユーザー データベースから直ちに、または指定された数 (秒単位) の使用しても、ROLLBACK オプション。ALTER DATABASE *database_name* SET SINGLE_USER WITH ROLLBACK *rollback_option*します。 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
  
## <a name="reattaching-a-database"></a>データベースの再アタッチ  
 デタッチされたファイルのままし、データベースの作成 (FOR ATTACH または FOR ATTACH_REBUILD_LOG オプション) を使用して再アタッチできます。 ファイルを別のサーバーに移動し、そこにアタッチすることもできます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **sysadmin**固定サーバー ロールのメンバーシップまたは、 **db_owner**データベースの役割。  
  
## <a name="examples"></a>使用例  
 次の例のデタッチ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]のデータベースが*skipchecks*を true に設定します。  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
 次の例のデタッチ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースし、フルテキスト インデックス ファイルおよびフルテキスト インデックスのメタデータが保持されます。 このコマンドでは、UPDATE STATISTICS が実行されます。これは既定の動作です。  
  
```  
exec sp_detach_db @dbname='AdventureWorks2012'  
    , @keepfulltextindexfile='true';  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースのデタッチ](../../relational-databases/databases/detach-a-database.md)  
  
  
