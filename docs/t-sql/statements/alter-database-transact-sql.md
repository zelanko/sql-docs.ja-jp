---
title: "ALTER DATABASE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 6c498acedd2821127137ec6be1bd2e04e6b3da09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース、またはそのデータベースに関連付けられているファイルおよびファイル グループを変更します。 データベースに対するファイルやファイル グループの追加と削除、データベースおよびデータベースのファイルやファイル グループの属性の変更、データベースの照合順序の変更、データベース オプションの設定を行えます。 データベース スナップショットは変更できません。 レプリケーションに関連付けられたデータベース オプションを変更するには、使用[sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)です。  
   
 解説が長くなるため、ALTER DATABASE の構文は次の各トピックに分けて説明しています。  
  
 ALTER DATABASE  
 このトピックでは、データベースの名前と照合順序を変更するための構文について説明します。  
  
 [ALTER DATABASE の File および Filegroup オプション](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
 データベースのファイルおよびファイル グループを追加したり削除したりするための構文のほか、ファイルおよびファイル グループの属性を変更するための構文について説明します。  
  
 [ALTER DATABASE SET オプション](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
 ALTER DATABASE の SET オプションを使ってデータベースの属性を変更するための構文について説明します。  
  
 [ALTER DATABASE データベース ミラーリング](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
 ALTER DATABASE のデータベース ミラーリングに関連した SET オプションの構文について説明します。  
  
 [ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
 構文について説明、 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] Always On 可用性グループのセカンダリ レプリカでセカンダリ データベースを構成するための ALTER DATABASE のオプションです。  
  
 [ALTER DATABASE 互換性レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
 ALTER DATABASE のデータベース互換性レベルに関連した SET オプションの構文について説明します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 
Azure SQL データベースでは、次を参照してください。 [ALTER DATABASE &#40;です。Azure SQL データベース &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
Azure SQL Data Warehouse では、次を参照してください。 [ALTER DATABASE &#40;です。Azure SQL Data Warehouse &#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
並列データ ウェアハウスでは、次を参照してください。 [ALTER DATABASE &#40;です。並列データ ウェアハウス"&"#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).
  
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
>  このオプションでは、包含データベースで使用できません。  
  
 CURRENT  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 使用中の現在のデータベースを変更することを指定します。  
  
 MODIFY NAME  **=**  *new_database_name*  
 として指定された名前のデータベースの名前を変更*new_database_name*です。  
  
 COLLATE *collation_name*  
 データベースの照合順序を指定します。 *collation_name* Windows 照合順序名または SQL 照合順序名のいずれかを指定できます。 指定しない場合は、データベースに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの照合順序が割り当てられます。  
  
 既定の照合順序以外でデータベースを作成する場合、データベース内のデータは常に、指定された照合順序を優先します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して内部のカタログ情報を保持する、包含データベースを作成するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定の照合順序、 **Latin1_General_100_CI_AS_WS_KS_SC**です。  
  
 Windows と SQL 照合順序名の詳細については、次を参照してください。 [COLLATE &#40;です。TRANSACT-SQL と #41 です。](~/t-sql/statements/collations.md).  
  
 **\<delayed_durability_option >:: =**  
 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 詳細については、次を参照してください。 [ALTER DATABASE SET Options &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md)と[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)です。  
  
 **\<file_and_filegroup_options >:: =**  
 詳細については、次を参照してください[ALTER DATABASE の File および Filegroup オプション &#40;。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="remarks"></a>解説  
 データベースを削除するには使用[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)です。  
  
 データベースのサイズを小さくを使用して[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)です。  
  
 ALTER DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
 データベース ファイルの状態 (オンラインかオフラインかなど) は、データベースの状態とは別に保持されます。 詳細については、次を参照してください。[ファイルの状態](../../relational-databases/databases/file-states.md)です。 ファイル グループ内のファイルの状態は、ファイル グループ全体の可用性を決定します。 ファイル グループを使用可能にするには、ファイル グループ内のすべてのファイルがオンラインである必要があります。 ファイル グループがオフラインの場合、SQL ステートメントでそのファイル グループにアクセスを試行するとエラーが発生します。 SELECT ステートメントのクエリ プランを作成する場合、クエリ オプティマイザーは、オフラインのファイル グループにある非クラスター化インデックスやインデックス付きビューを回避します。 これにより、これらのステートメントは正常に実行できます。 ただし、オフラインのファイル グループに、対象テーブルのヒープやクラスター化インデックスが含まれている場合には、SELECT ステートメントは失敗します。 また、オフラインのファイル グループ内にあるインデックス付きのテーブルを変更する INSERT、UPDATE、または DELETE ステートメントは失敗します。  
  
 データベースが RESTORING 状態にある場合、大半の ALTER DATABASE ステートメントは失敗します。 ただし、データベース ミラーリング オプションの設定は例外です。 データベースが RESTORING 状態になるのは、アクティブな復元操作中や、バックアップ ファイルの破損によりデータベースまたはログ ファイルの復元操作が失敗した場合などです。  
  
 インスタンスのプラン キャッシュ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のオプションのいずれかの設定ではオフにします。  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 各キャッシュ ストアが消去、プラン キャッシュ内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログには、次の情報メッセージが含まれています:"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ ストア フラッシュをいくつかのデータベースのため '%s' キャッシュ ストア (プラン キャッシュの一部) を %d 個検出が発生しましたメンテナンス操作または再構成操作"です。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。  
  
 次のシナリオでは、プロシージャ キャッシュがフラッシュも。  
  
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
  
     データベース、ALTER DATABASE のかどうか、データベースの照合順序に依存する次のオブジェクトが存在*database_name*COLLATE ステートメントは失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ALTER アクションをブロックしている各オブジェクトのエラー メッセージを返します。  
  
    -   SCHEMABINDING を指定して作成されたユーザー定義関数およびビュー  
  
    -   計算列。  
  
    -   CHECK 制約  
  
    -   既定のデータベース照合順序から継承した照合順序を持つ文字型列がテーブルにある場合に、そのテーブルを返すテーブル値関数  
  
     非スキーマ バインド エンティティの依存関係情報は、データベースの照合順序が変更されると自動的に更新されます。  
  
 データベースの照合順序を変更しても、データベース オブジェクトのシステム名に重複は発生しません。 照合順序の変更によって名前が重複する場合、次の名前空間が原因でデータベースの照合順序の変更が失敗することがあります。  
  
-   プロシージャ、テーブル、トリガー、ビューなどのオブジェクト名  
  
-   スキーマの名前。  
  
-   グループ、ロール、ユーザーなどのプリンシパル  
  
-   システム データ型、ユーザー定義データ型などのスカラー データ型の名前  
  
-   フルテキスト カタログ名  
  
-   オブジェクト内の列名またはパラメーター名  
  
-   テーブル内のインデックス名  
  
新しい照合順序の名前が重複すると、変更操作が失敗すると、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]重複が見つかった名前空間を示すエラー メッセージを返します。  
  
## <a name="viewing-database-information"></a>データベース情報の表示  
 カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用して、データベース、ファイルおよびファイル グループについての情報を返すことができます。  
  
## <a name="permissions"></a>Permissions  
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
- [ALTER DATABASE &#40;です。Azure SQL データベース &#41;](alter-database-azure-sql-database.md)  
- [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
- [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [sys.database_mirroring_witnesses &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [sys.data_spaces と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [sys.filegroups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [システム データベース](../../relational-databases/databases/system-databases.md)  
  

