---
title: "データベースを削除 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6e1a96bb64c8cb6a81311f422d370e36d9489ca4
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

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
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、データベースを削除します。  
  
 *database_name*  
 削除するデータベースの名前を指定します。 データベースの一覧を表示する、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 *database_snapshot_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 削除するデータベース スナップショットの名前を指定します。  
  
## <a name="general-remarks"></a>全般的な解説  
 データベースは、オフライン、読み取り専用、未確認などの状態に関係なくドロップすることができます。 表示するには、データベースの現在の状態を使用して、 **sys.databases**カタログ ビューです。  
  
 削除されたデータベースは、バックアップを復元することによってのみ、再作成できます。 データベース スナップショットはバックアップできません。したがって復元もできません。  
  
 データベースが削除されるとき、 [master データベース](../../relational-databases/databases/master-database.md)をバックアップする必要があります。  
  
 データベースを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからそのデータベースが削除され、そのデータベースで使用されている物理ディスク ファイルも削除されます。 削除の際にデータベースまたはディスク ファイルのいずれかがオフラインの場合、ディスク ファイルは削除されません。 これらのファイルは Windows エクスプローラーを使用して手動で削除できます。 ファイル システムからファイルを削除することがなく、現在のサーバーからデータベースを削除するには使用[sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)です。  
  
> [!WARNING]  
>  FILE_SNAPSHOT を持つデータベースを削除すると、関連付けられているバックアップは成功しますが、スナップショットが関連付けられているデータベース ファイルは、これらのデータベース ファイルを参照するバックアップを無効化を回避するのには削除されません。 ファイルでは、切り捨てられますが、FILE_SNAPSHOT のバックアップをそのままの状態に保つために物理的に削除されません。 詳細については、「 [Microsoft Azure Blob Storage サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)します。  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 データベース スナップショットを削除すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータベース スナップショットが削除され、スナップショットで使用されている物理的な NTFS ファイル システムのスパース ファイルが削除されます。 データベース スナップショットによるスパース ファイルの使用方法の詳細については、次を参照してください。[データベース スナップショット & #40 です。SQL Server &#41;](../../relational-databases/databases/database-snapshots-sql-server.md). インスタンスのプラン キャッシュが消去、データベース スナップショットを削除する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 各キャッシュ ストアが消去、プラン キャッシュ内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログには、次の情報メッセージが含まれています:"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ ストア フラッシュをいくつかのデータベースのため '%s' キャッシュ ストア (プラン キャッシュの一部) を %d 個検出が発生しましたメンテナンス操作または再構成操作"です。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
## <a name="interoperability"></a>相互運用性  
  
### <a name="sql-server"></a>SQL Server  
 トランザクション レプリケーションに対してパブリッシュされたデータベース、あるいは、マージ レプリケーションに対してパブリッシュまたはサブスクライブされたデータベースを削除するには、まず、データベースからレプリケーションを削除する必要があります。 データベースが損傷しているか、レプリケーションを最初に削除できない場合、またはその両方の場合でも、ALTER DATABASE を使用してデータベースをオフラインに設定してから削除すると、ほとんどの場合、データベースを削除できます。  
  
 データベースがログ配布に関与している場合は、データベースを削除する前にログ配布を削除します。 詳細については、「[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 [システム データベース](../../relational-databases/databases/system-databases.md)は削除できません。  
  
 DROP DATABASE ステートメントは、自動コミット モードで実行する必要があり、明示的または暗黙的なトランザクションでは許可されません。 自動コミット モードは、既定のトランザクション管理モードです。  
  
 使用中のデータベースは削除できません。 使用中のデータベースとは、1 人以上のユーザーが読み込みまたは書き込みのため開いているデータベースです。 データベースからそのユーザーを削除するには、ALTER DATABASE を使用して、データベースを SINGLE_USER に設定します。  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 データベースを削除する前に、そのデータベース上のすべてのデータベース スナップショットを削除する必要があります。  
  
 Stretch データベースのデータベースの有効化を削除しても、リモートのデータは削除されません。 リモートのデータを削除する場合は、手動で削除する必要があります。  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 データベースを削除するには、master データベースに接続する必要があります。
  
 DROP DATABASE ステートメントは SQL バッチ内の唯一のステートメントである必要があります。また、一度に削除できるデータベースは 1 つだけです。
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 データベースを削除するには、master データベースに接続する必要があります。
  
 DROP DATABASE ステートメントは SQL バッチ内の唯一のステートメントである必要があります。また、一度に削除できるデータベースは 1 つだけです。

## <a name="permissions"></a>Permissions  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 必要があります、**コントロール**、データベースに対する権限または**ALTER ANY DATABASE**権限、またはメンバーシップ、 **db_owner**固定データベース ロール。  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 サーバー レベル プリンシパル ログイン (プロビジョニング処理で作成される) またはのメンバーのみ、 **dbmanager**データベース ロールは、データベースを削除できます。  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 必要があります、**コントロール**、データベースに対する権限または**ALTER ANY DATABASE**権限、またはメンバーシップ、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-single-database"></a>A. 1 つのデータベースを削除する  
 次の例では、削除、`Sales`データベース。  
  
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
  
 次の例では、削除、データベース スナップショットをという名前`sales_snapshot0600`、ソース データベースには影響しません。  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  

