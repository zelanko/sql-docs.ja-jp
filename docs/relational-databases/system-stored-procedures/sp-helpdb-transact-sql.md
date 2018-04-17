---
title: sp_helpdb (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 231e911d1438a16d4b1a2db234e895f8652ea375
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースまたはすべてのデータベースに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=** ] **'***name***'**  
 情報を報告するデータベースの名前を指定します。 *名前*は**sysname**、既定値はありません。 場合*名前*が指定されていない**sp_helpdb**のすべてのデータベース上のレポート、 **sys.databases**カタログ ビューです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|データベース名。|  
|**db_size**|**nvarchar (13)**|データベースの総サイズです。|  
|**所有者**|**sysname**|データベースの所有者は、のように**sa**です。|  
|**dbid**|**smallint**|データベース ID。|  
|**created**|**nvarchar (11)**|データベースの作成日です。|  
|**ステータス**|**nvarchar (600)**|データベースで現在設定されているデータベース オプションの、コンマで区切られたリストです。<br /><br /> ブール値を持つオプションは、有効になっている場合にのみリストに追加されます。 形式でそれらの値がブール型以外のオプションが表示されている*option_name*=*値*です。<br /><br /> 詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。|  
|**compatibility_level**|**tinyint**|データベースの互換性レベル (60、65、70、80、および 90) です。|  
  
 場合*名前*を指定すると、指定されたデータベースのファイルの割り当てを示す追加の結果セットが存在します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nchar(128)**|論理ファイル名です。|  
|**fileid**|**smallint**|ファイル ID。|  
|**filename**|**nchar(260)**|オペレーティング システム ファイル名 (物理ファイル名) です。|  
|**filegroup**|**nvarchar(128)**|ファイルが属するファイル グループです。<br /><br /> NULL = ファイルはログ ファイルです。 ログ ファイルはファイル グループのメンバーにはなりません。|  
|**size**|**nvarchar(18)**|ファイル サイズ (MB 単位) です。|  
|**maxsize**|**nvarchar(18)**|ファイルの最大拡張サイズです。 このフィールドの値が UNLIMITED である場合、ディスクがいっぱいになるまでファイルを拡張できることを示します。|  
|**growth**|**nvarchar(18)**|ファイルを拡張するときの増分です。 これは、新たに領域が必要になるたびにファイルに追加する容量を示します。|  
|**使用状況**|**varchar (9)**|ファイルの使い方を示します。 データ ファイルの場合は、値は**'data only'**と、値は、ログ ファイルの**'ログのみ'**です。|  
  
## <a name="remarks"></a>解説  
 **ステータス**結果内の列がどのオプションは、データベースで ON に設定されているレポートを設定します。 すべてのデータベース オプションがによって報告されていない、**ステータス**列です。 現在のデータベース オプションの設定の完全な一覧を表示する、 **sys.databases**カタログ ビューです。  
  
## <a name="permissions"></a>権限  
 1 つのデータベースが指定されている場合、メンバーシップ、**パブリック**データベース内のロールが必要です。 データベースが指定されていない場合のメンバーシップ、**パブリック**における役割、**マスター**データベースが必要です。  
  
 データベースにアクセスすることはできない場合、 **sp_helpdb**可能な限り、データベースに関するエラー メッセージ 15622 と情報が表示されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-information-about-a-single-database"></a>A. 特定のデータベースに関する情報を返す  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに関する情報を表示します。  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>B. すべてのデータベースに関する情報を返す  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行するサーバー上のすべてのデータベースに関する情報を表示します。  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
