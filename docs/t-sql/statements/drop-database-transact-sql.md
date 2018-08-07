---
title: DROP DATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/15/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP DATABASE
- DROP_DATABASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], deleting
- removing databases
- database snapshots [SQL Server], removing
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- DROP DATABASE statement
- database removal [SQL Server], DROP DATABASE statement
ms.assetid: 477396a9-92dc-43c9-9b97-42c8728ede8e
caps.latest.revision: 83
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: d744de4921f4cd3c77bffa98c5b07be6fce8d160
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39455786"
---
# <a name="drop-database-transact-sql"></a>DROP DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  1 つ以上のユーザー データベースまたはデータベース スナップショットを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
DROP DATABASE [ IF EXISTS ] { database_name | database_snapshot_name } [ ,...n ] [;]  
```  
  
```  
-- Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse Syntax   
DROP DATABASE database_name [;]  
```  
  
## <a name="arguments"></a>引数  
 *IF EXISTS*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、データベースを削除します。  
  
 *database_name*  
 削除するデータベースの名前を指定します。 データベースの一覧を表示するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューを使用します。  
  
 *database_snapshot_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 削除するデータベース スナップショットの名前を指定します。  
  
## <a name="general-remarks"></a>全般的な解説  
 データベースは、オフライン、読み取り専用、未確認などの状態に関係なくドロップすることができます。 データベースの現在の状態を表示するには、**sys.databases** カタログ ビューを使用します。  
  
 削除されたデータベースは、バックアップを復元することによってのみ、再作成できます。 データベース スナップショットはバックアップできません。したがって復元もできません。  
  
 データベースを削除する場合は、[master データベース](../../relational-databases/databases/master-database.md)をバックアップする必要があります。  
  
 データベースを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからそのデータベースが削除され、そのデータベースで使用されている物理ディスク ファイルも削除されます。 削除の際にデータベースまたはディスク ファイルのいずれかがオフラインの場合、ディスク ファイルは削除されません。 これらのファイルは Windows エクスプローラーを使用して手動で削除できます。 ファイルをファイル システムから削除せずにデータベースを現在のサーバーから削除するには、[sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) を使用します。  
  
> [!WARNING]  
>  FILE_SNAPSHOT を持つデータベースを削除すると、関連付けられているバックアップは成功しますが、スナップショットが関連付けられているデータベース ファイルは、これらのデータベース ファイルを参照するバックアップを無効化を回避するのには削除されません。 ファイルでは、切り捨てられますが、FILE_SNAPSHOT のバックアップをそのままの状態に保つために物理的に削除されません。 詳細については、「 [Microsoft Azure Blob Storage サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで。  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 データベース スナップショットを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータベース スナップショットが削除され、スナップショットで使用されている物理的な NTFS ファイル システムのスパース ファイルが削除されます。 データベース スナップショットによるスパース ファイルの使用の詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。 データベース スナップショットを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュが消去されます。 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、一部のデータベース メンテナンス操作または再構成操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに含まれます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
## <a name="interoperability"></a>相互運用性  
  
### <a name="sql-server"></a>SQL Server  
 トランザクション レプリケーションに対してパブリッシュされたデータベース、あるいは、マージ レプリケーションに対してパブリッシュまたはサブスクライブされたデータベースを削除するには、まず、データベースからレプリケーションを削除する必要があります。 データベースが損傷しているか、レプリケーションを最初に削除できない場合、またはその両方の場合でも、ALTER DATABASE を使用してデータベースをオフラインに設定してから削除すると、ほとんどの場合、データベースを削除できます。  
  
 データベースがログ配布に関与している場合は、データベースを削除する前にログ配布を削除します。 詳細については、「[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 [システム データベース](../../relational-databases/databases/system-databases.md)は削除できません。  
  
 DROP DATABASE ステートメントは、自動コミット モードで実行する必要があり、明示的または暗黙的なトランザクションでは許可されません。 自動コミット モードは、既定のトランザクション管理モードです。  
  
 使用中のデータベースは削除できません。 使用中のデータベースとは、1 人以上のユーザーが読み込みまたは書き込みのため開いているデータベースです。 データベースからユーザーを削除するには、ALTER DATABASE を使用して、データベースを SINGLE_USER に設定する方法があります。 
 
 >[!Warning] 
 > これは、任意のスレッドによる最初の連続する接続で SINGLE_USER スレッドを受け取り、接続できなくなるため、失敗しない方法です。 SQL Server では、負荷時にデータベースを削除する組み込みの方法は提供されていません。
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 データベースを削除する前に、そのデータベース上のすべてのデータベース スナップショットを削除する必要があります。  
  
 Stretch データベースのデータベースの有効化を削除しても、リモートのデータは削除されません。 リモートのデータを削除する場合は、手動で削除する必要があります。  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 データベースを削除するには、master データベースに接続する必要があります。
  
 DROP DATABASE ステートメントは SQL バッチ内の唯一のステートメントである必要があります。また、一度に削除できるデータベースは 1 つだけです。
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 データベースを削除するには、master データベースに接続する必要があります。
  
 DROP DATABASE ステートメントは SQL バッチ内の唯一のステートメントである必要があります。また、一度に削除できるデータベースは 1 つだけです。

## <a name="permissions"></a>アクセス許可  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 データベースの **CONTROL** 権限、**ALTER ANY DATABASE** 権限、または **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 データベースを削除できるのは、(プロビジョニング プロセスによって作成される) サーバーレベル プリンシパルのログイン、または **dbmanager** データベース ロールのメンバーだけです。  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 データベースの **CONTROL** 権限、**ALTER ANY DATABASE** 権限、または **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-single-database"></a>A. 1 つのデータベースを削除する  
 次の例では、`Sales` データベースを削除します。  
  
```  
DROP DATABASE Sales;  
```  
  
### <a name="b-dropping-multiple-databases"></a>B. 複数のデータベースを削除する  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例では、一覧表示された各データベースを削除します。  
  
```  
DROP DATABASE Sales, NewSales;  
```  
  
### <a name="c-dropping-a-database-snapshot"></a>C. データベース スナップショットを削除する  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例では、`sales_snapshot0600` というデータベース スナップショットを、ソース データベースには影響を与えずに削除します。  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
