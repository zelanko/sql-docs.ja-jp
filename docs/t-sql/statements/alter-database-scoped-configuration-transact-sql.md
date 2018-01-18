---
title: ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9638d94c2bd6f461650b15f96c7a75c95eaeb861
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このステートメントで複数のデータベース構成設定を使用する、**個々 のデータベース**レベル。 このステートメントで使用できる[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で始まる[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 これらの設定は次のとおりです。  
  
- プロシージャ キャッシュをクリアします。  
- プライマリ データベースが特定のデータベースに最適に基づいており、別の値の設定の任意の値 (1、2、...) に、MAXDOP パラメーターを設定 (0 など) すべてのセカンダリ データベースを使用 (レポート クエリなど)。  
- データベースに依存しないクエリ オプティマイザーの基数推定モデルを互換性レベルに設定します。  
- データベース レベルでパラメーター スニッフィングを有効または無効にします。
- データベース レベルでのクエリ最適化の修正プログラムを有効または無効にします。
- 有効にするにまたはデータベース レベルで id キャッシュを無効にします。
- 有効にするにまたは、バッチが初めてコンパイルされるときに、キャッシュに格納されるコンパイル済みプランのスタブを無効にします。    
  
 ![リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "リンク アイコン") [TRANSACT-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
}  
```  
  
## <a name="arguments"></a>引数  
 
セカンダリの  
 
(すべてのセカンダリ データベースは同一の値が必要) のセカンダリ データベースの設定を指定します。  
  
MAXDOP **=** {\<value> | PRIMARY }  
**\<value>**  
  
ステートメントの MAXDOP 設定を使用する既定値を指定します。 0 では、既定値をサーバーの構成が代わりに使用されることを示します。 データベース スコープで MAXDOP オーバーライド (場合を除く 0 に設定されています)、**並列処理の次数の最大**sp_configure でサーバー レベルで設定します。 クエリ ヒントでは、DB をオーバーライドできますもを別の設定を必要とする特定のクエリをチューニングするために MAXDOP をスコープします。 これらすべての設定は、MAXDOP、ワークロード グループの設定によって制限されます。   

max degree of parallelism オプションを使用すると、並列プラン実行で使用するプロセッサの数を制限できます。 SQL Server で並列実行プランをクエリ、インデックス データ定義言語 (DDL) 操作、並列挿入、オンライン alter 列、並行統計コレクション、および静的およびキーセット ドリブン カーソルの作成。
 
インスタンス レベルでは、このオプションを設定するを参照してください。 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)です。 

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **MAXDOP** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)です。  
  
PRIMARY  
  
プライマリ上のデータベース中に、セカンダリに対してのみ設定して、構成が 1 つのセットをプライマリになることを示します。 構成変更については、プライマリ、セカンダリ上の値が変更される場合それに応じて、セカンダリを設定する必要はありません値に明示的にです。 **プライマリ**セカンダリの既定の設定です。  
  
LEGACY_CARDINALITY_ESTIMATION **=** { ON | **OFF** | PRIMARY }  

データベースの互換性レベルに依存しない SQL Server 2012 および以前のバージョンにクエリ オプティマイザーの基数の推定モデルを設定できます。 既定値は**OFF**、クエリ オプティマイザーの基数の推定モデルは、データベースの互換性レベルに基づく設定します。 これを設定する**ON**を有効にすると等価[トレース フラグ 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **querytraceon です**[クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルでは、追加、 **USE ヒント**[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)トレース フラグを使用する代わりにします。 
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効です、クエリ オプティマイザー基数推定モデルの設定ですべてのセカンダリがプライマリに設定値であることを指定します。 クエリ オプティマイザーの基数の推定モデルのプライマリで構成が変更された場合、セカンダリ上の値を変更します。 **プライマリ**セカンダリの既定の設定です。  
  
PARAMETER_SNIFFING **=** { **ON** | OFF | PRIMARY}  

有効または無効に[パラメーターを見つけ出す](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)です。 既定値は ON です。 これは、 [トレース フラグ 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)を指定した場合と同じです。   

> [!TIP] 
> これを実現するクエリ レベルで、次を参照してください。、 **OPTIMIZE FOR UNKNOWN** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルで、 **USE ヒント**[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)も利用できます。 
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効です、すべてのセカンダリでは、この設定に値が、プライマリの設定値であることを指定します。 場合、構成を使用するため、プライマリ上[パラメーターを見つけ出す](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)変更、セカンダリ上の値が変更されますそれに応じて設定する必要がないセカンダリ値に明示的にします。 これは、セカンダリの既定の設定です。  
  
QUERY_OPTIMIZER_HOTFIXES **=** { ON | **OFF** | PRIMARY }  

有効またはデータベースの互換性レベルに関係なく、クエリ オプティマイザーの修正プログラムを無効にします。 既定値は**OFF**、無効にクエリ オプティマイザーの修正プログラム、最高の使用可能な互換性レベルは、特定のバージョンの導入された後にリリースされていた (RTM)。 これを設定する**ON**を有効にすると等価[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。   

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **querytraceon です**[クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルで使用するヒントの追加[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)トレース フラグを使用する代わりにします。  
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効ですし、すべてのセカンダリでは、この設定に値が、プライマリに設定された値を指定します。 構成変更については、プライマリ、セカンダリ上の値が変更された場合はそれに応じてを設定する必要がないセカンダリ値明示的にです。 これは、セカンダリの既定の設定です。  
  
CLEAR PROCEDURE_CACHE  

データベースのプロシージャ (プラン) キャッシュをクリアします。 これは、プライマリとセカンダリの両方で実行できます。  

IDENTITY_CACHE  **=**  { **ON** |オフ}  

**適用されます**:[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

有効またはデータベース レベルで id キャッシュを無効にします。 既定値は**ON**です。 Identity キャッシュは、id 列を持つテーブルの挿入のパフォーマンスを向上させるために使用されます。 サーバーが予期せず再起動やセカンダリ サーバーにフェールオーバーした場合、id 列の値のギャップを回避するのには、IDENTITY_CACHE オプションを無効にします。 このオプションは、既存のような[トレース フラグ 272](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md), サーバー レベルでのみではなく、データベース レベルで設定できる点が異なります。   

> [!NOTE] 
> このオプションは、プライマリの場合にのみ設定できます。 詳細については、次を参照してください。 [id 列](create-table-transact-sql-identity-property.md)です。  

OPTIMIZE_FOR_AD_HOC_WORKLOADS **=** { ON | **OFF** }  

**適用対象**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

有効またはバッチが初めてコンパイルされるときに、キャッシュに格納されるコンパイル済みプランのスタブを無効にします。 既定値は OFF です。 データベース スコープの構成データベースは、コンパイル済みプランのスタブ OPTIMIZE_FOR_AD_HOC_WORKLOADS が有効になっている場合、バッチのキャッシュに保存されますが、最初にコンパイルされます。 プランのスタブは、完全なコンパイル済みプランのサイズと比較して、小さいメモリ使用量があります。  バッチがコンパイルまたは再実行された場合、コンパイル済みプランのスタブは削除され、コンパイル済みプランの完全に置き換えられます。

##  <a name="Permissions"></a> アクセス許可  
 必要と任意のデータベース スコープ構成を変更します   
上のデータベースです。 データベースに対する CONTROL 権限を持つユーザーは、この権限を付与することができます。  
  
## <a name="general-remarks"></a>全般的な解説  
 セカンダリ データベースがプライマリからのさまざまなスコープを持つ構成設定を構成するときに、すべてのセカンダリ データベースは、同じ構成を使用します。 個々 のセカンダリには、さまざまな設定を構成することはできません。  
  
 このステートメントを実行するすべてのクエリが再コンパイルする必要が、現在のデータベースでプロシージャ キャッシュをクリアします。  
  
 3 部構成の名前のクエリでクエリの現在のデータベース接続の設定が SQL モジュール (プロシージャ、関数、トリガーなど) では、現在のデータベース コンテキストでコンパイルされた以外の受け入れられ、およびそのためのオプションを使用して、データベースが存在します。  
  
 ALTER_DATABASE_SCOPED_CONFIGURATION イベントは、DDL トリガーを起動するために使用できる DDL イベントとして追加されます。 これは、ALTER_DATABASE_EVENTS トリガー グループの子です。  
 
 データベース スコープの設定が引き継がれます、データベースを構成します。 これは、特定のデータベースが復元またはアタッチされたときに、既存の構成設定が残ることを意味します。
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
**MAXDOP**  
  
 詳細な設定はグローバル ルールを上書きでき、そのリソース ガバナーは、他のすべての MAXDOP 設定に上限を設定します。  MAXDOP 設定ロジック次に示します。  
  
-   クエリ ヒントは、sp_configure と、データベース スコープの設定の両方をオーバーライドします。 リソース グループ MAXDOP 設定されている場合、ワークロード グループの。  
  
    -   クエリ ヒントが 0 に設定されている場合は、リソース ガバナーの設定によってオーバーライドされます。  
  
    -   クエリ ヒントが 0 の場合、it ではない場合は、リソース ガバナーの設定によって制限されます。  
  
-   クエリ ヒントがある場合を除き、(0 でない限り) を設定するスコープ DB が sp_configure の設定をオーバーライドし、リソース ガバナーの設定によって制限されます。  
  
-   Sp_configure の設定は、リソース ガバナーの設定によってオーバーライドされます。  
  
**QUERY_OPTIMIZER_HOTFIXES**  
  
 Querytraceon ですヒントを使用して、従来のクエリ オプティマイザーまたはクエリ オプティマイザー修正プログラムを有効にする、クエリ ヒントとデータベース スコープの構成設定であり、オプションを適用するかが有効な場合、OR 条件があります。  
  
**GeoDR**  
  
 Always On 可用性グループや GeoReplication などの読み取り可能なセカンダリ データベースは、データベースの状態をチェックして、セカンダリの値を使用します。 場合でも、フェールオーバーで再コンパイルは発生しないと、技術的には新しいプライマリがセカンダリの設定を使用しているクエリ、つまり、ワークロードが異なると、キャッシュされたクエリは、そのために、プライマリとセカンダリの間で設定をのみ変化します。最適な設定を使用して、一方、新しいクエリがそれらに対応する新しい設定を選択します。  
  
**DacFx**  
  
 ALTER データベース スコープのため構成は、ことへの影響、データベースのスキーマ (またはデータなし)、スキーマのエクスポートはできません、古いバージョンの SQL Server にインポートする SQL Server 2016 以降の Azure SQL Database と SQL Server の新機能例:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]または[!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)]です。 エクスポートなど、 [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3)または[BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4)から、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]または[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]この新しい機能を使用するデータベースが下位レベルのサーバーにインポートすることはありません。  
  
## <a name="metadata"></a>メタデータ  

[Sys.database_scoped_configurations &#40;です。TRANSACT-SQL と&#41; です。](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)システム ビューは、データベース内でのスコープの構成に関する情報を提供します。 データベース スコープ構成オプションに表示するだけ sys.database_scoped_configurations はサーバー全体の既定の設定を上書きします。 [Sys.configurations &#40;です。TRANSACT-SQL と&#41;です。](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)システム ビューでは、サーバー全体の設定のみ示しています。  
  
## <a name="examples"></a>使用例  
これらの例は、ALTER DATABASE SCOPED CONFIGURATION の使用法を示します  
  
### <a name="a-grant-permission"></a>A. アクセス許可を付与します。  

この例は、ALTER DATABASE SCOPED CONFIGURATION を実行するために必要なアクセス許可を付与します。     
ユーザー [Joe] です。  
  
```sql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. MAXDOP を設定します。  

この例の MAXDOP 設定プライマリ データベースと MAXDOP 1 = セカンダリ データベースの地理的レプリケーションのシナリオ 4 を = です。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
この例では、同じ値に設定されている地理的レプリケーション シナリオでは、プライマリ データベースをセカンダリ データベースの MAXDOP を設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. LEGACY_CARDINALITY_ESTIMATION を設定します。  

この例は、セカンダリ データベースの地理的レプリケーションのシナリオで LEGACY_CARDINALITY_ESTIMATION を ON に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
この例は、geo レプリケーションのシナリオでは、プライマリ データベースは、セカンダリ データベースの LEGACY_CARDINALITY_ESTIMATION を設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. PARAMETER_SNIFFING を設定します。  

この例は、プライマリ データベースの地理的レプリケーションのシナリオで PARAMETER_SNIFFING を OFF に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
この例は、プライマリ データベースの地理的レプリケーションのシナリオで PARAMETER_SNIFFING を OFF に設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
この例では、geo レプリケーションのシナリオではプライマリ データベース上にあるように、セカンダリ データベースの PARAMETER_SNIFFING を設定します。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. QUERY_OPTIMIZER_HOTFIXES を設定します。  

プライマリ データベースの地理的レプリケーション シナリオでは、QUERY_OPTIMIZER_HOTFIXES を ON に設定します。  

```sql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. プロシージャ キャッシュをクリア  

この例では、(プライマリ データベースに対してのみ可能)、プロシージャ キャッシュをクリアします。  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. IDENTITY_CACHE を設定します。

**適用されます**:[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)](機能は、パブリック プレビューで) 

この例では、id キャッシュが無効にします。

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

### <a name="h-set-optimizeforadhocworkloads"></a>H. OPTIMIZE_FOR_AD_HOC_WORKLOADS を設定します。

**適用対象**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

この例では、バッチが初めてコンパイルされるときに、キャッシュに格納されるコンパイル済みプランのスタブが有効にします。

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET OPTIMIZE_FOR_AD_HOC_WORKLOADS = ON;
```

## <a name="additional-resources"></a>その他のリソース

### <a name="maxdop-resources"></a>MAXDOP リソース 
* [並列処理の次数](../../relational-databases/query-processing-architecture-guide.md#DOP)
* [推奨事項と SQL Server の"max degree of parallelism"構成オプションのガイドライン](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>LEGACY_CARDINALITY_ESTIMATION リソース    
* [基数推定 (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* [SQL Server 2014 の基数推定機能によるクエリプランの最適化](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>PARAMETER_SNIFFING リソース    
* [パラメーター スニッフィング](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)
* [「パラメーターが僕されます」です。](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>QUERY_OPTIMIZER_HOTFIXES リソース    
* [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
* [SQL Server クエリ オプティマイザーの修正プログラム トレース フラグ 4199 サービス モデル](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>詳細情報  
 [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [データベースとファイルのカタログ ビュー](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [サーバー構成オプション](../../database-engine/configure-windows/server-configuration-options-sql-server.md) [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
 
