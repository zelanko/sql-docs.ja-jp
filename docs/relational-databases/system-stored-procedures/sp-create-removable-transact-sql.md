---
title: sp_create_removable (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_create_removable
- sp_create_removable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_removable
ms.assetid: 06e36ae5-f70d-4a26-9a7f-ee4b9360b355
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c74f780b4e981fad39e7b6da6a531305000910cc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spcreateremovable-transact-sql"></a>sp_create_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リムーバブル メディア データベースを作成します。 3 つ以上のファイル (システム カタログ テーブルとトランザクション ログに 1 つずつ、データ テーブルに 1 つ以上) を作成し、それらのファイルにデータベースを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用することをお勧め[CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_create_removable   
   [ @dbname = ] 'dbname',   
   [ @syslogical= ] 'syslogical',   
   [ @sysphysical = ] 'sysphysical',   
   [ @syssize = ] syssize,   
   [ @loglogical = ] 'loglogical',   
   [ @logphysical = ] 'logphysical',   
   [ @logsize = ] logsize,   
   [ @datalogical1 = ] 'datalogical1',   
   [ @dataphysical1 = ] 'dataphysical1',   
   [ @datasize1 = ] datasize1 ,   
   [ @datalogical16 = ] 'datalogical16',   
   [ @dataphysical16 = ] 'dataphysical16',   
   [ @datasize16 = ] datasize16 ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=** ] **'***dbname***'**  
 リムーバブル メディアに作成するデータベースの名前を指定します。 *dbname*は**sysname**です。  
  
 [ **@syslogical=** ] **'***syslogical***'**  
 システム カタログ テーブルを格納するファイルの論理名を指定します。 *syslogical*は**sysname**です。  
  
 [  **@sysphysical=** ] **'***sysphysical***'**  
 物理名です。 システム カタログ テーブルを格納するファイルの名前をフル パスと共に指定します。 *sysphysical*は**nvarchar (260)**です。  
  
 [ **@syssize=** ] *syssize*  
 システム カタログ テーブルを格納するファイルのサイズ (MB) を指定します。 *syssize*は**int**です。最小*syssize*は 1 です。  
  
 [ **@loglogical=** ] **'***loglogical***'**  
 トランザクション ログを格納するファイルの論理名を指定します。 *loglogical*は**sysname**です。  
  
 [  **@logphysical=** ] **'***logphysical***'**  
 物理名です。 トランザクション ログを格納するファイルの名前をフル パスと共に指定します。 *logphysical*は**nvarchar (260)**です。  
  
 [ **@logsize=** ] *logsize*  
 トランザクション ログを格納するファイルのサイズ (MB) を指定します。 *logsize*は**int**です。最小*logsize*は 1 です。  
  
 [  **@datalogical1=** ] **'***datalogical***'**  
 データ テーブルを格納するファイルの論理名を指定します。 *datalogical*は**sysname**です。  
  
 データ ファイルの数は 1 ～ 16 です。 データベースが大きくなり複数のディスクに分散する必要が生じた場合に備えて、通常、複数のデータ ファイルを作成します。  
  
 [  **@dataphysical1=** ] **'***dataphysical***'**  
 物理名です。 データ テーブルを格納するファイルの名前をフル パスと共に指定します。 *dataphysical*は**nvarchar (260)**です。  
  
 [  **@datasize1=** ] **'***datasize***'**  
 データ テーブルを格納するファイルのサイズ (MB) を指定します。 *datasize*は**int**です。最小*datasize*は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 データベースのコピーをコンパクト ディスクなどのリムーバブル メディアに作成し、他のユーザーにデータベースを配布する場合は、このストアド プロシージャを使用します。  
  
## <a name="permissions"></a>権限  
 CREATE DATABASE、CREATE ANY DATABASE、または ALTER ANY DATABASE の各権限が必要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス上のディスク使用量を管理するため、通常、データベースを作成する権限をいくつかのログイン アカウントに制限します。  
  
### <a name="permissions-on-data-and-log-files"></a>データおよびログ ファイルに対する権限  
 特定の操作がデータベースに対して実行されるときは必ず、そのデータおよびログ ファイルに対して必要な権限が設定されます。 この権限は、開く権限のあるディレクトリにファイルが存在する場合に、そのファイルが誤って書き換えられるのを防ぎます。  
  
|データベースに対する操作|ファイルに対して設定される権限|  
|---------------------------|------------------------------|  
|変更して新しいファイルを追加|Created|  
|バックアップ|アタッチ|  
|復元|デタッチ|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セット データではなくファイルとログ ファイルのアクセス許可。  
  
## <a name="examples"></a>使用例  
 次の例は、データベースを作成`inventory`というリムーバブルなデータベースです。  
  
```  
EXEC sp_create_removable 'inventory',   
   'invsys',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invsys.mdf'  
, 2,   
   'invlog',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invlog.ldf', 4,  
   'invdata',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invdata.ndf',   
10;  
```  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_certify_removable &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-certify-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
