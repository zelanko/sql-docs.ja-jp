---
title: ALTER DATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_TSQL
- ALTER DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- databases [SQL Server], modifying
- ALTER DATABASE statement
- databases [SQL Server], renaming
- renaming databases
- database modifications [SQL Server]
- ALTER DATABASE statement, syntax described
- database names [SQL Server], ALTER DATABASE
- modifying databases
- collations [SQL Server], modifying
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 15f8affd-8f39-4021-b092-0379fc6983da
caps.latest.revision: 282
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5e0e79fb6a74373268e6077971662b323623cc54
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース、またはそのデータベースに関連付けられているファイルおよびファイル グループを変更します。 データベースに対するファイルやファイル グループの追加と削除、データベースおよびデータベースのファイルやファイル グループの属性の変更、データベースの照合順序の変更、データベース オプションの設定を行えます。 データベース スナップショットは変更できません。 レプリケーションに関連するデータベース オプションを変更するには、[sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) を使用してください。  
   
 解説が長くなるため、ALTER DATABASE の構文は次の各トピックに分けて説明しています。  
  
 ALTER DATABASE  
 このトピックでは、データベースの名前と照合順序を変更するための構文について説明します。  
  
 [ALTER DATABASE の File および Filegroup オプション](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
 データベースのファイルおよびファイル グループを追加したり削除したりするための構文のほか、ファイルおよびファイル グループの属性を変更するための構文について説明します。  
  
 [ALTER DATABASE の SET オプション](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
 ALTER DATABASE の SET オプションを使ってデータベースの属性を変更するための構文について説明します。  
  
 [ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
 ALTER DATABASE のデータベース ミラーリングに関連した SET オプションの構文について説明します。  
  
 [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
 Always On 可用性グループのセカンダリ レプリカ上のセカンダリ データベースを構成するための、ALTER DATABASE の [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] オプションの構文について説明します。  
  
 [ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
 ALTER DATABASE のデータベース互換性レベルに関連した SET オプションの構文について説明します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
Azure SQL Database については、「[ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)」をご覧ください  
Azure SQL Data Warehouse については、「[ALTER DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)」をご覧ください。  
Parallel Data Warehouse については、「[ALTER DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)」をご覧ください。
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
ALTER DATABASE { database_name  | CURRENT }  
{  
    MODIFY NAME = new_database_name   
  | COLLATE collation_name  
  | <file_and_filegroup_options>  
  | <set_database_options>  
}  
[;]  
  
<file_and_filegroup_options >::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  
  
<set_database_options>::=  
  <optionspec>::=   
  <auto_option> ::=   
  <change_tracking_option> ::=  
  <cursor_option> ::=   
  <database_mirroring_option> ::=   
  <date_correlation_optimization_option> ::=  
  <db_encryption_option> ::=  
  <db_state_option> ::=  
  <db_update_option> ::=  
  <db_user_access_option> ::=  <delayed_durability_option> ::=  <external_access_option> ::=  
  <FILESTREAM_options> ::=  
  <HADR_options> ::=    
  <parameterization_option> ::=  
  <query_store_options> ::=  
  <recovery_option> ::=   
  <service_broker_option> ::=  
  <snapshot_option> ::=  
  <sql_option> ::=   
  <termination> ::=  
  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 CURRENT  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 使用中の現在のデータベースを変更することを指定します。  
  
 MODIFY NAME **=***new_database_name*  
 データベースの名前を、*new_database_name* で指定した名前に変更します。  
  
 COLLATE *collation_name*  
 データベースの照合順序を指定します。 *collation_name* には、Windows 照合順序名または SQL 照合順序名を指定できます。 指定しない場合は、データベースに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの照合順序が割り当てられます。  
  
 既定の照合順序以外でデータベースを作成する場合、データベース内のデータは常に、指定された照合順序を優先します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、包含データベースを作成する場合、内部カタログの情報は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の照合順序、**Latin1_General_100_CI_AS_WS_KS_SC** を使用して維持されます。  
  
 Windows と SQL の照合順序名については、「[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)」を参照してください。  
  
 **\<delayed_durability_option> ::=**  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 詳しくは、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」および「[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)」をご覧ください。  
  
 **\<file_and_filegroup_options>::=**  
 詳細については、「[ALTER DATABASE の File および Filegroup オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 データベースを削除するには、[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) を使用します。  
  
 データベースのサイズを縮小するには、[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md) を使用します。  
  
 ALTER DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
 データベース ファイルの状態 (オンラインかオフラインかなど) は、データベースの状態とは別に保持されます。 詳しくは、「[ファイルの状態](../../relational-databases/databases/file-states.md)」をご覧ください。 ファイル グループ内のファイルの状態は、ファイル グループ全体の可用性を決定します。 ファイル グループを使用可能にするには、ファイル グループ内のすべてのファイルがオンラインである必要があります。 ファイル グループがオフラインの場合、SQL ステートメントでそのファイル グループにアクセスを試行するとエラーが発生します。 SELECT ステートメントのクエリ プランを作成する場合、クエリ オプティマイザーは、オフラインのファイル グループにある非クラスター化インデックスやインデックス付きビューを回避します。 これにより、これらのステートメントは正常に実行できます。 ただし、オフラインのファイル グループに、対象テーブルのヒープやクラスター化インデックスが含まれている場合には、SELECT ステートメントは失敗します。 また、オフラインのファイル グループ内にあるインデックス付きのテーブルを変更する INSERT、UPDATE、または DELETE ステートメントは失敗します。  
  
 データベースが RESTORING 状態にある場合、大半の ALTER DATABASE ステートメントは失敗します。 ただし、データベース ミラーリング オプションの設定は例外です。 データベースが RESTORING 状態になるのは、アクティブな復元操作中や、バックアップ ファイルの破損によりデータベースまたはログ ファイルの復元操作が失敗した場合などです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュは、次のいずれかのオプションを設定することにより消去されます。  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、一部のデータベース メンテナンス操作または再構成操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに含まれます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
 プロシージャ キャッシュは、次のシナリオでもフラッシュされます。  
  
-   AUTO_CLOSE データベース オプションが ON に設定されている。 データベースを参照 (または使用) するユーザー接続が 1 つも存在しない場合、バックグラウンド タスクがデータベースを自動的に閉じてシャットダウンすることを試みます。  
  
-   既定のオプションが設定されているデータベースに対して複数のクエリを実行した。 データベースはその後削除されます。  
  
-   ソース データベースのデータベース スナップショットが削除された。  
  
-   データベースのトランザクション ログを正常に再構築した。  
  
-   データベースのバックアップを復元した。  
  
-   データベースをデタッチした。  
  
## <a name="changing-the-database-collation"></a>データベースの照合順序の変更  
 データベースに別の照合順序を適用する前に、次の条件が満たされているかどうかを確認してください。  
  
-   現在データベースを使用しているのは、1 人だけである。  
  
-   データベースの照合順序に依存するスキーマ バインド オブジェクトがない。  
  
     データベースの照合順序に依存する次のオブジェクトがデータベース内に存在する場合、ALTER DATABASE*database_name*COLLATE ステートメントは失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ALTER アクションをブロックしているオブジェクトごとにエラー メッセージを返します。  
  
    -   SCHEMABINDING を指定して作成されたユーザー定義関数およびビュー  
  
    -   計算列。  
  
    -   CHECK 制約  
  
    -   既定のデータベース照合順序から継承した照合順序を持つ文字型列がテーブルにある場合に、そのテーブルを返すテーブル値関数  
  
     非スキーマ バインド エンティティの依存関係情報は、データベースの照合順序が変更されると自動的に更新されます。  
  
 データベースの照合順序を変更しても、データベース オブジェクトのシステム名に重複は発生しません。 照合順序の変更によって名前が重複する場合、次の名前空間が原因でデータベースの照合順序の変更が失敗することがあります。  
  
-   プロシージャ、テーブル、トリガー、ビューなどのオブジェクト名  
  
-   スキーマ名。  
  
-   グループ、ロール、ユーザーなどのプリンシパル  
  
-   システム データ型、ユーザー定義データ型などのスカラー データ型の名前  
  
-   フルテキスト カタログ名  
  
-   オブジェクト内の列名またはパラメーター名  
  
-   テーブル内のインデックス名  
  
新しい照合順序によって名前が重複すると、変更操作が失敗し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は重複が見つかった名前空間を示すエラー メッセージを返します。  
  
## <a name="viewing-database-information"></a>データベース情報の表示  
 カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用して、データベース、ファイルおよびファイル グループについての情報を返すことができます。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-name-of-a-database"></a>A. データベースの名前を変更する  
 次の例では、`AdventureWorks2012` データベースの名前を `Northwind` に変更します。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
### <a name="b-changing-the-collation-of-a-database"></a>B. データベースの照合順序を変更する  
 次の例では、`testdb`S 照合順序で `SQL_Latin1_General_CP1_CI_A` という名前のデータベースを作成した後、`testdb` データベースの照合順序を `COLLATE French_CI_AI` に変更します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE master;  
GO  
  
CREATE DATABASE testdb  
COLLATE SQL_Latin1_General_CP1_CI_AS ;  
GO  
  
ALTER DATABASE testDB  
COLLATE French_CI_AI ;  
GO  
```  
  
## <a name="see-also"></a>参照  
- [ALTER DATABASE &#40;Azure SQL Database&#41;](alter-database-azure-sql-database.md)  
- [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
- [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [sys.data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [システム データベース](../../relational-databases/databases/system-databases.md)  
  
