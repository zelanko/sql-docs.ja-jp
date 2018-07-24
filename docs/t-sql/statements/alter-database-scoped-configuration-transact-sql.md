---
title: ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/142018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 811376d76608af8d75ab68649f0eea61bfb8a5c3
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041940"
---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このステートメントでは、複数のデータベース構成を**個別データベース** レベルで設定できます。 このステートメントは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降の [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で利用できます。 次のような設定があります。  
  
- プロシージャ キャッシュをクリアします。  
- プライマリ データベースに対して、MAXDOP パラメーターを特定のデータベースに最適な内容に基づいて任意の値 (1、2、...) に設定し、(クエリ レポートなどに) 使用されるすべてのセカンダリ データベースに対して別の値 (0 など) を設定します。  
- データベースに依存しないクエリ オプティマイザーのカーディナリティ推定モデルを互換性レベルに設定します。  
- データベース レベルでパラメーター スニッフィングを有効または無効にします。
- データベース レベルでのクエリ最適化の修正プログラムを有効または無効にします。
- データベース レベルで ID キャッシュを有効または無効にします。
- バッチが初めてコンパイルされるとき、コンパイルしたプラン スタブのキャッシュ保存を有効または無効にします。  
- ネイティブ コンパイル T-SQL モジュールの実行統計コレクションを有効または無効にします。
- ONLINE= 構文に対応している DDL ステートメントの既定のオプションでオンラインの有効/無効を変更します。
- RESUMABLE= 構文に対応している DDL ステートメントの既定のオプションで再開可能性の有効/無効を変更します。 

 ![リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET < set_options >
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}
    | IDENTITY_CACHE = { ON | OFF }
    | OPTIMIZE_FOR_AD_HOC_WORKLOADS = { ON | OFF }
    | XTP_PROCEDURE_EXECUTION_STATISTICS = { ON | OFF } 
    | XTP_QUERY_EXECUTION_STATISTICS = { ON | OFF }    
    | ELEVATE_ONLINE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED } 
    | ELEVATE_RESUMABLE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }  
}  
```  
  
## <a name="arguments"></a>引数  
 
セカンダリの場合  
 
セカンダリ データベースの設定を指定します (すべてのセカンダリ データベースに同じ値を与える必要があります)。  
  
MAXDOP **=** {\<value> | PRIMARY }  
**\<value>**  
  
ステートメントで使用される MAXDOP 設定の既定値を指定します。 0 が初期設定値であり、サーバー構成が代わりに使用されることを示します。 データベース スコープの MAXDOP は、サーバー レベルで設定されている**並列処理の最大限度**を p_configure によってオーバーライドします (0 に設定されていない限り)。 別の設定を必要とする特定のクエリを調整する目的で、クエリ ヒントは引き続き、DB スコープの MAXDOP をオーバーライドできます。 これらすべての設定の上限は、ワークロード グループに設定されている MAXDOP によって決定されます。   

max degree of parallelism オプションを使用すると、並列プラン実行で使用するプロセッサの数を制限できます。 SQL Server は、クエリ、インデックス データ定義言語 (DDL) の操作、並列挿入、オンライン列変更、並行統計コレクション、静的およびキーセット ドリブン カーソルの作成の場合に並列実行プランを検討します。
 
インスタンス レベルでこのオプションを設定する方法については、「[max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。 

> [!TIP] 
> これをクエリ レベルで行うには、**MAXDOP** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)を追加してください。  
  
PRIMARY  
  
データベースがプライマリにあるとき、セカンダリに対してのみ設定できます。構成はプライマリに設定されている構成になることを示します。 プライマリの構成が変更されると、セカンダリの値も適宜変更されます。セカンダリの値を明示的に設定する必要はありません。 **PRIMARY** はセカンダリの初期設定です。  
  
LEGACY_CARDINALITY_ESTIMATION **=** { ON | **OFF** | PRIMARY }  

データベースの互換性レベルに関係なく、クエリ オプティマイザーのカーディナリティ推定モデルを SQL Server 2012 以前のバージョンに設定できます。 既定値は **OFF** であり、クエリ オプティマイザーのカーディナリティ推定モデルがデータベースの互換性レベルに基づいて設定されます。 これを **ON** に設定することは、[トレース フラグ 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) を有効にすることと同じです。 

> [!TIP] 
> これをクエリ レベルで行うには、**QUERYTRACEON** [クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)を追加してください。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降、クエリ レベルでこれを行うには、トレース フラグの代わりに、**USE HINT** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)を追加してください。 
  
PRIMARY  
  
データベースがプライマリにあるとき、この値はセカンダリでのみ有効になります。すべてのセカンダリのクエリ オプティマイザーのカーディナリティ推定モデル設定がプライマリに設定されている値になることを示します。 クエリ オプティマイザーのカーディナリティ推定モデルの構成がプライマリで変更された場合、セカンダリの値も適宜変更されます。 **PRIMARY** はセカンダリの初期設定です。  
  
PARAMETER_SNIFFING **=** { **ON** | OFF | PRIMARY}  

[パラメーター スニッフィング](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)を有効にするか無効にします。 既定値は ON です。 これは、 [トレース フラグ 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)を指定した場合と同じです。   

> [!TIP] 
> クエリ レベルでこれを行う方法については、「**OPTIMIZE FOR UNKNOWN** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降、クエリ レベルでこれを行うには、**USE HINT** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)も利用できます。 
  
PRIMARY  
  
データベースがプライマリにあるとき、この値はセカンダリでのみ有効になります。すべてのセカンダリでこの設定の値がプライマリに設定されている値になることを示します。 [パラメーター スニッフィング](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)の使用に関するプライマリの構成が変更されると、セカンダリの値も適宜変更されます。セカンダリの値を明示的に設定する必要はありません。 これはセカンダリの初期設定です。  
  
QUERY_OPTIMIZER_HOTFIXES **=** { ON | **OFF** | PRIMARY }  

データベースの互換性レベルに関係なく、クエリ最適化修正プログラムを有効または無効にします。 既定値は **OFF** です。特定のバージョンで利用できる最高の互換性レベルが導入された後に公開されたクエリ最適化修正プログラムが無効になります (RTM 後)。 これを **ON** に設定することは、[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) を有効にすることと同じです。   

> [!TIP] 
> これをクエリ レベルで行うには、**QUERYTRACEON** [クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)を追加してください。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降、クエリ レベルでこれを行うには、トレース フラグの代わりに、USE HINT [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)を追加してください。  
  
PRIMARY  
  
データベースがプライマリにあるとき、この値はセカンダリでのみ有効になります。すべてのセカンダリでこの設定の値がプライマリに設定されている値になることを示します。 プライマリの構成が変更されると、セカンダリの値も適宜変更されます。セカンダリの値を明示的に設定する必要はありません。 これはセカンダリの初期設定です。  
  
CLEAR PROCEDURE_CACHE  

データベースのプロシージャ (プラン) キャッシュを消去します。 これはプライマリとセカンダリの両方で実行されます。  

IDENTITY_CACHE **=** { **ON** | OFF }  

**適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] と [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 

データベース レベルで ID キャッシュを有効または無効にします。 既定値は **ON** です。 ID キャッシュは、ID 列が含まれるテーブルでの INSERT パフォーマンスを改善するために使用されます。 サーバーが突然再起動したか、セカンダリ サーバーにフェールオーバーしたときに ID 列の値に隔たりができることを回避するには、IDENTITY_CACHE オプションを無効にします。 このオプションは、サーバー レベルのみならずデータベース レベルで設定可能という点を除き、既存の[トレース フラグ 272](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) と似ています。   

> [!NOTE] 
> このオプションはプライマリにのみ設定できます。 詳細については、「[ID 列](create-table-transact-sql-identity-property.md)」を参照してください。  

OPTIMIZE_FOR_AD_HOC_WORKLOADS **=** { ON | **OFF** }  

**適用対象**: [!INCLUDE[sssdsfull](../../includes/sssdsfull-md.md)] 

バッチが初めてコンパイルされるとき、コンパイルしたプラン スタブのキャッシュ保存を有効または無効にします。 既定値は OFF です。 あるデータベースに対してデータベース スコープ構成 OPTIMIZE_FOR_AD_HOC_WORKLOADS を有効にすると、バッチを初めてコンパイルしたとき、コンパイル済みのプラン スタブがキャッシュに保存されます。 プラン スタブのメモリ領域は、完全なコンパイル済みプランのサイズに比べて小さくなります。  バッチが再度コンパイルまたは実行されると、コンパイル済みプラン スタブは削除され、完全なコンパイル済みプランと置換されます。

XTP_PROCEDURE_EXECUTION_STATISTICS  **=** { ON | **OFF** }  

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] 

現在のデータベース内のすべてのネイティブ コンパイル T-SQL モジュールに対し、モジュール レベルで実行統計コレクションを有効また無効にします。 既定値は OFF です。 実行統計は [sys.dm_exec_procedure_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) に反映されます。

このオプションが ON の場合、または統計コレクションが [sp_xtp_control_proc_exec_stats](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md) によって有効化されている場合は、ネイティブ コンパイル T-SQL モジュールのモジュール レベルの実行統計が収集されます。

XTP_QUERY_EXECUTION_STATISTICS  **=** { ON | **OFF** }  

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]

現在のデータベース内のすべてのネイティブ コンパイル T-SQL モジュールに対し、ステートメント レベルで実行統計コレクションを有効また無効にします。 既定値は OFF です。 実行統計は、[sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) および[クエリ ストア](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)に反映されます。

このオプションが ON の場合、または統計コレクションが [sp_xtp_control_query_exec_stats](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md) によって有効化されている場合は、ネイティブ コンパイル T-SQL モジュールのステートメント レベルの実行統計が収集されます。

ネイティブ コンパイル T-SQL モジュールのパフォーマンスの監視の詳細については、「[ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視](../../relational-databases/in-memory-oltp/monitoring-performance-of-natively-compiled-stored-procedures.md)」を参照してください。

ELEVATE_ONLINE = { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (機能はパブリック プレビュー段階)

サポートされている操作からオンラインにエンジンを自動的に昇格させるオプションを選択できます。 既定は OFF であり、ステートメントで指定されない限り、操作はオンラインに昇格されません。 [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) は ELEVATE_ONLINE の現在の値を反映します。 これらのオプションは、オンラインで一般的にサポートされている操作にのみ適用されます。  

FAIL_UNSUPPORTED

この値のとき、サポートされているすべての DDL 操作が ONLINE に昇格されます。 オンライン実行に対応していない操作は失敗し、警告が出ます。

WHEN_SUPPORTED  

この値のとき、ONLINE 対応の操作が昇格されます。 オンライン対応ではない操作はオフラインで実行されます。

> [!NOTE]
> ONLINE オプションが指定されたステートメントを送信することで、既定の設定をオーバーライドできます。 
 
ELEVATE_RESUMABLE= { OFF | WHEN_SUPPORTED | FAIL_UNSUPPORTED }

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (機能はパブリック プレビュー段階)

サポートされている操作から再開可能にエンジンを自動的に昇格させるオプションを選択できます。 既定は OFF であり、ステートメントで指定されない限り、操作は再開可能に昇格されません。 [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) は ELEVATE_RESUMABLE の現在の値を反映します。 これらのオプションは、再開可能実行で一般的にサポートされている操作にのみ適用されます。 

FAIL_UNSUPPORTED

この値のとき、サポートされているすべての DDL 操作が RESUMABLE に昇格されます。 再開可能実行に対応していない操作は失敗し、警告が出ます。

WHEN_SUPPORTED  

この値のとき、RESUMABLE 対応の操作が昇格されます。 再開可能対応ではない操作は再開不可能として実行されます。  

> [!NOTE]
> RESUMABLE オプションが指定されたステートメントを送信することで、既定の設定をオーバーライドできます。 

##  <a name="Permissions"></a> Permissions  
 データベースで ALTER ANY DATABASE SCOPE CONFIGURATION を   
必要とします。 この権限は、データベース上で CONTROL 権限を持つユーザーが付与できます。  
  
## <a name="general-remarks"></a>全般的な解説  
 セカンダリ データベースにはプライマリとは異なるスコープ構成を設定できますが、すべてのセカンダリ データベースで同じ構成が使用されます。 個々のセカンダリに異なる設定を構成することはできません。  
  
 このステートメントを実行すると、現在のデータベースのプロシージャ キャッシュが消去されます。つまり、すべてのクエリを再コンパイルする必要があります。  
  
 3 部構成の名前のクエリの場合、現在のデータベース コンテキストでコンパイルされる SQL モジュール (プロシージャ、関数、トリガーなど) ではなく、クエリに対する現在のデータベース接続の設定が適用されます。そのため、そのような設定が置かれているデータベースのオプションが使用されます。  
  
 ALTER_DATABASE_SCOPED_CONFIGURATION イベントは、DDL トリガーの始動に利用できる DDL イベントとして追加されます。 これは ALTER_DATABASE_EVENTS トリガー グループの子になります。  
 
 データベース スコープ構成設定はデータベースで継承されます。 つまり、特定のデータベースが復元されたり、アタッチされたりしたとき、既存の構成設定が残ります。
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
**MAXDOP**  
  
 詳細設定はグローバル設定をオーバーライドします。その Resource Governor が他のすべての MAXDOP 設定の上限となります。  MAXDOP 設定のロジックは次のようになります。  
  
-   クエリ ヒントは sp_configure とデータベース スコープ設定の両方をオーバーライドします。 ワークロード グループにリソース グループ MAXDOP が設定されている場合:  
  
    -   クエリ ヒントが 0 に設定されている場合、Resource Governor 設定でオーバーライドされます。  
  
    -   クエリ ヒントが 0 ではない場合、Resource Governor 設定が上限となります。  
  
-   DB スコープ設定 (0 ではない限り) は、クエリ ヒントがある場合を除き、sp_configure をオーバーライドし、Resource Governor 設定が上限となります。  
  
-   sp_configure 設定は、Resource Governor 設定でオーバーライドされます。  
  
**QUERY_OPTIMIZER_HOTFIXES**  
  
 QUERYTRACEON ヒントを使用して旧来のクエリ オプティマイザーまたはクエリ オプティマイザー修正プログラムを有効にするとき、クエリ ヒントとデータベース スコープ構成設定の OR 条件になります。つまり、いずれかが有効になっている場合、オプションが適用されます。  
  
**GeoDR**  
  
 AlwaysOn 可用性グループや GeoReplication など、読み取り可能なセカンダリ データベースは、データベースの状態を確認し、セカンダリ値を使用します。 フェールオーバーで再コンパイルが行われず、技術的に、セカンダリ設定を使用しているクエリが新しいプライマリに与えられる場合でも、プライマリとセカンダリの間の設定はワークロードが異なるときにのみ変わるというのがその考えです。そのため、キャッシュされたクエリでは最適設定が使用されるが、新しいクエリはそれに適した新しい設定を選択します。  
  
**DacFx**  
  
 ALTER DATABASE SCOPED CONFIGURATION は Azure SQL Database と SQL Server 2016 以降の SQL Server の新しい機能であり、データベース スキーマに影響を与えます。スキーマのエクスポートは (データがあってもなくても)、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] や [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] など、以前のバージョンの SQL Server にはインポートできません。 たとえば、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] または [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] データベースから [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) または [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) にエクスポートしたものは、下位レベルのサーバーにインポートできません。  

**ELEVATE_ONLINE** 

このオプションは、WITH(ONLINE= 構文) 対応の DDL ステートメントにのみ適用されます。 XML インデックスは影響を受けません。 

**ELEVATE_RESUMABLE**

このオプションは、WITH(ONLINE= 構文) 対応の DDL ステートメントにのみ適用されます。 XML インデックスは影響を受けません。 

  
## <a name="metadata"></a>メタデータ  

[sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) システム ビューには、データベース内のスコープ構成に関する情報が表示されます。 データベース スコープ構成オプションはサーバー全体の初期設定にオーバーライドするため、sys.database_scoped_configurations にのみ表示されます。 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) システム ビューは、サーバー全体の設定にのみ表示されます。  
  
## <a name="examples"></a>使用例  
以下は ALTER DATABASE SCOPED CONFIGURATION の使用例です  
  
### <a name="a-grant-permission"></a>A. 権限の付与  

この例では、ALTER DATABASE SCOPED CONFIGURATION の実行に必要な権限を     
ユーザー [Joe] に与えています。  
  
```sql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. MAXDOP の設定  

この例では、geo レプリケーション シナリオでプライマリ データベースに MAXDOP = 1 を、セカンダリ データベースに MAXDOP = 4 を設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
この例では、geo レプリケーション シナリオで、セカンダリ データベースの MAXDOP をそのプライマリ データベースと同じ値に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. LEGACY_CARDINALITY_ESTIMATION の設定  

この例では、geo レプリケーション シナリオで、セカンダリ データベースの LEGACY_CARDINALITY_ESTIMATION を ON に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
この例では、geo レプリケーション シナリオで、セカンダリ データベースの LEGACY_CARDINALITY_ESTIMATION をそのプライマリ データベースと同じ値に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. PARAMETER_SNIFFING の設定  

この例では、geo レプリケーション シナリオで、プライマリ データベースの PARAMETER_SNIFFING を OFF に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
この例では、geo レプリケーション シナリオで、プライマリ データベースの PARAMETER_SNIFFING を OFF に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
この例では、geo レプリケーション シナリオで、セカンダリ データベースの PARAMETER_SNIFFING をプライマリ データベースと同じ値に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. QUERY_OPTIMIZER_HOTFIXES の設定  

geo レプリケーション シナリオで、プライマリ データベースの QUERY_OPTIMIZER_HOTFIXES を ON に設定します。  

```sql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. プロシージャ キャッシュの消去  

この例では、プロシージャ キャッシュを消去します (プライマリ データベースのみ可能)。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. IDENTITY_CACHE の設定

**適用対象**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] と [!INCLUDE[ssSDS](../../includes/sssds-md.md)] (機能はパブリック プレビュー段階) 

この例では、ID キャッシュを無効にします。

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

### <a name="h-set-optimizeforadhocworkloads"></a>H. OPTIMIZE_FOR_AD_HOC_WORKLOADS の設定

**適用対象**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

この例では、バッチが初めてコンパイルされるとき、コンパイルしたプラン スタブのキャッシュ保存を有効にします。

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET OPTIMIZE_FOR_AD_HOC_WORKLOADS = ON;
```

### <a name="i--set-elevateonline"></a>I.  ELEVATE_ONLINE を設定する 

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (機能はパブリック プレビュー段階)
 
この例では、ELEVATE_ONLINE が FAIL_UNSUPPORTED に設定されます。  tsqlCopy 

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ELEVATE_ONLINE=FAIL_UNSUPPORTED ;
```  

### <a name="j-set-elevateresumable"></a>J. ELEVATE_RESUMABLE を設定する 

**適用対象**: [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] (機能はパブリック プレビュー段階)

この例では、ELEVEATE_RESUMABLE が WHEN_SUPPORTED に設定されます。  tsqlCopy 

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ELEVATE_RESUMABLE=WHEN_SUPPORTED ;  
``` 

## <a name="additional-resources"></a>その他のリソース

### <a name="maxdop-resources"></a>MAXDOP リソース 
* [並列処理の次数](../../relational-databases/query-processing-architecture-guide.md#DOP)
* [SQL Server の "max degree of parallelism" 構成オプションの推奨事項とガイドライン](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>LEGACY_CARDINALITY_ESTIMATION リソース    
* 
  [カーディナリティ推定 (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* 
  [SQL Server 2014 のカーディナリティ推定機能によるクエリプランの最適化](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>PARAMETER_SNIFFING リソース    
* [パラメーター スニッフィング](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)
* ["I smell a parameter!"](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/) (パラメーターのにおいがする!)

### <a name="queryoptimizerhotfixes-resources"></a>QUERY_OPTIMIZER_HOTFIXES リソース    
* [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
* [SQL Server クエリ オプティマイザー修正プログラム トレース フラグ 4199 サービス モデル](https://support.microsoft.com/en-us/kb/974006)

### <a name="elevateonline-resources"></a>ELEVATE_ONLINE リソース 

- [オンライン インデックス操作のガイドライン](../../relational-databases/indexes/guidelines-for-online-index-operations.md) 

### <a name="elevateresumable-resources"></a>ELEVATE_RESUMABLE リソース 

- [オンライン インデックス操作のガイドライン](../../relational-databases/indexes/guidelines-for-online-index-operations.md) 
 
## <a name="more-information"></a>詳細情報  
 [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [データベースとファイルのカタログ ビュー](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [サーバー構成オプション](../../database-engine/configure-windows/server-configuration-options-sql-server.md) [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
 
