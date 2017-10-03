---
title: "ALTER データベース スコープ ベースの構成 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
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
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 19d2d42ff513020b5d4bb9492f0714893101bdcb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER データベース スコープ ベースの構成 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このステートメントで複数のデータベース構成設定を使用する、**個々 のデータベース**レベル。 このステートメントは、両方で使用できる[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]し、[[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 これらの設定は次のとおりです。  
  
- プロシージャ キャッシュをクリアします。  
  
- プライマリ データベースに対して、MAXDOP パラメーターを特定のデータベースに最適な内容に基づいて任意の値 (1、2、...) に設定し、(クエリ レポートなどに) 使用されるすべてのセカンダリ データベースに対して別の値 (0 など) を設定します。  
  
- データベースに依存しないクエリ オプティマイザーの基数推定モデルを互換性レベルに設定します。  
  
- データベース レベルでパラメーター スニッフィングを有効または無効にします。
  
- データベース レベルでのクエリ最適化の修正プログラムを有効または無効にします。

- 有効にするにまたはデータベース レベルで id キャッシュを無効にします。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET IDENTITY_CACHE = { ON | OFF }
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}    
}  
  
```  
  
## <a name="arguments"></a>引数  
 
セカンダリの  
 
(すべてのセカンダリ データベースは同一の値が必要) のセカンダリ データベースの設定を指定します。  
  
MAXDOP ** = ** {\<値 > |プライマリ}  
**\<値 >**  
  
ステートメントの MAXDOP 設定を使用する既定値を指定します。 0 では、既定値をサーバーの構成が代わりに使用されることを示します。 データベース スコープで MAXDOP オーバーライド (場合を除く 0 に設定されています)、**並列処理の次数の最大**sp_configure でサーバー レベルで設定します。 クエリ ヒントでは、DB をオーバーライドできますもを別の設定を必要とする特定のクエリをチューニングするために MAXDOP をスコープします。 これらすべての設定は、MAXDOP、ワークロード グループの設定によって制限されます。   

max degree of parallelism オプションを使用すると、並列プラン実行で使用するプロセッサの数を制限できます。 SQL Server で並列実行プランをクエリ、インデックス データ定義言語 (DDL) 操作、並列挿入、オンライン alter 列、並行統計 collectiion および静的およびキーセット ドリブン カーソルの作成。
 
インスタンス レベルでは、このオプションを設定するを参照してください。 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)です。 

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **MAXDOP** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)です。  
  
PRIMARY  
  
プライマリ上のデータベース中に、セカンダリに対してのみ設定して、構成が 1 つのセットをプライマリになることを示します。 構成のプライマリの変更では、セカンダリ上の値が変更される場合それに応じてを設定する必要がないセカンダリ値明示的に必要です。 **プライマリ**セカンダリの既定の設定です。  
  
LEGACY_CARDINALITY_ESTIMATION ** = ** {ON |**OFF** |プライマリ}  

データベースの互換性レベルに依存しない SQL Server 2012 および以前のバージョンにクエリ オプティマイザーの基数の推定モデルを設定できます。 既定値は**OFF**、クエリ オプティマイザーの基数の推定モデルは、データベースの互換性レベルに基づく設定します。 これを設定する**ON**を有効にすると等価[トレース フラグ 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **querytraceon です**[クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルでは、追加、 **USE ヒント**[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)トレース フラグを使用する代わりにします。 
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効です、クエリ オプティマイザー基数推定モデルの設定ですべてのセカンダリがプライマリに設定値であることを指定します。 クエリ オプティマイザーの基数の推定モデルのプライマリで構成が変更された場合、セカンダリ上の値を変更します。 **プライマリ**セカンダリの既定の設定です。  
  
PARAMETER_SNIFFING ** = ** { **ON** |OFF |プライマリ}  

有効または無効に[パラメーターを見つけ出す](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)です。 既定値は ON です。 これは、 [トレース フラグ 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)を指定した場合と同じです。   

> [!TIP] 
> これを実現するクエリ レベルで、次を参照してください。、 **OPTIMIZE FOR UNKNOWN** [クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルで、 **USE ヒント**[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)も利用できます。 
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効です、すべてのセカンダリでは、この設定に値が、プライマリの設定値であることを指定します。 場合を使用するため、プライマリ上の構成[パラメーターを見つけ出す](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)変更、セカンダリ上の値が変更されます適宜を設定する必要がないセカンダリ値、明示的に必要です。 これは、セカンダリの既定の設定です。  
  
QUERY_OPTIMIZER_HOTFIXES ** = ** {ON |**OFF** |プライマリ}  

有効またはデータベースの互換性レベルに関係なく、クエリ オプティマイザーの修正プログラムを無効にします。 既定値は**OFF**です。 これは有効にすると同じ[トレース フラグ 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。   

> [!TIP] 
> これを行うにはクエリ レベルで、追加、 **querytraceon です**[クエリ ヒント](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)です。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、これを実現するクエリ レベルで使用するヒントの追加[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)トレース フラグを使用する代わりにします。  
  
PRIMARY  
  
この値は、プライマリ上でデータベース中にセカンダリでのみ有効です、すべてのセカンダリでは、この設定に値が、プライマリの設定値であることを指定します。 構成のプライマリの変更では、セカンダリ上の値が変更される場合それに応じてを設定する必要がないセカンダリ値明示的に必要です。 これは、セカンダリの既定の設定です。  
  
クリア PROCEDURE_CACHE  

データベースのプロシージャ キャッシュをクリアします。 これは、プライマリとセカンダリの両方で実行できます。  

IDENTITY_CACHE = { **ON** |オフ}  

**適用されます**: SQL Server 2017、および Azure SQL データベース (機能は、パブリック プレビューで) 

有効またはデータベース レベルで id キャッシュを無効にします。 既定値は**ON**です。 Identity キャッシュは、Id 列を持つテーブルの挿入のパフォーマンスを向上させるために使用されます。 サーバーが予期せず再起動やセカンダリ サーバーにフェールオーバーした場合、Id 列の値のギャップを回避するのには、IDENTITY_CACHE オプションを無効にします。 このオプションは、データベース レベルではなく、サーバー レベルでのみ設定できますが、既存 SQL Server トレース フラグ 272 に似ています。   

> [!NOTE] 
> このオプションは、プライマリの場合にのみ設定できます。 詳細については、次を参照してください。 [Id 列](create-table-transact-sql-identity-property.md)です。  
>

##  <a name="Permissions"></a> アクセス許可  
 必要と任意のデータベース スコープ構成を変更します   
上のデータベースです。 データベースに対する CONTROL 権限を持つユーザーがこのアクセス許可を付与することができます。  
  
## <a name="general-remarks"></a>全般的な解説  
 セカンダリ データベースがプライマリからのさまざまなスコープを持つ構成設定を構成するときに、すべてのセカンダリ データベースは、同じ構成を使用します。 個々 のセカンダリには、さまざまな設定を構成することはできません。  
  
 このステートメントを実行すると、すべてのクエリを再コンパイルする必要があることを意味、現在のデータベースでプロシージャ キャッシュがクリアされます。  
  
 3 部構成の名前のクエリでクエリの現在のデータベース接続の設定が受け入れられない場合以外は、現在のデータベース コンテキストでコンパイルしている SQL モジュール (プロシージャ、関数、およびトリガーなど) とそのためのオプションを使用して、データベースが存在します。  
  
 ALTER_DATABASE_SCOPED_CONFIGURATION イベントは、DDL トリガーを起動するために使用できる DDL イベントとして追加されます。 これは、ALTER_DATABASE_EVENTS トリガー グループの子です。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 **MAXDOP**  
  
 詳細な設定はグローバル ルールを上書きでき、そのリソース ガバナーは、他のすべての MAXDOP 設定に上限を設定します。  MAXDOP 設定ロジック次に示します。  
  
-   クエリ ヒントは、sp_configure と、データベース スコープの設定の両方をオーバーライドします。 リソース グループ MAXDOP 設定されている場合、ワークロード グループの。  
  
    -   クエリ ヒントが 0 に設定されている場合は、リソース ガバナーの設定によってオーバーライドされます。  
  
    -   クエリ ヒントが 0 の場合、it ではない場合は、リソース ガバナーの設定によって制限されます。  
  
-   クエリ ヒントがある場合を除き、(0 でない限り) を設定するスコープ DB が sp_configure の設定をオーバーライドし、リソース ガバナーの設定によって制限されます。  
  
-   Sp_configure の設定は、リソース ガバナーの設定によってオーバーライドされます。  
  
 **QUERY_OPTIMIZER_HOTFIXES**  
  
 Querytraceon ですヒントを使用して、従来のクエリ オプティマイザーまたはクエリ オプティマイザー修正プログラムを有効にする、クエリ ヒントとデータベース スコープの構成設定であり、いずれかが有効な場合、オプションが適用されます、OR 条件があります。  
  
 **GeoDR**  
  
 Always On 可用性グループや GeoReplication などの読み取り可能なセカンダリ データベースは、データベースの状態をチェックして、セカンダリの値を使用します。 場合でも、フェールオーバーでは再コンパイルしないし、技術的には新しいプライマリがセカンダリの設定を使用しているクエリ、つまり、ワークロードが異なると、キャッシュされたクエリは、そのために、プライマリとセカンダリの間で設定が異なるだけこと新しいクエリでは、それらの適切な新しい設定を取得します。 一方、最適な設定を使用します。  
  
 **DacFx**  
  
 ALTER DATABASE SCOPED CONFIGURATION が Azure SQL データベースおよびデータベース スキーマに影響する SQL Server 2016 の新機能であるため (またはデータなし)、スキーマのエクスポートことはできません古いバージョンの SQL Server にインポートする[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]または <。c2 > [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] です。 エクスポートなど、 [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3)または[BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4)から、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]または[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]この新しい機能を使用するデータベースが下位レベルのサーバーにインポートすることはありません。  
  
## <a name="metadata"></a>メタデータ  

[Sys.database_scoped_configurations & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)システム ビューは、データベース内でのスコープの構成に関する情報を提供します。 データベース スコープ構成オプションに表示するだけ sys.database_scoped_configurations はサーバー全体の既定の設定を上書きします。 [Sys.configurations & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)システム ビューでは、サーバー全体の設定のみ示しています。  
  
## <a name="examples"></a>使用例  
これらの例は、ALTER DATABASE SCOPED CONFIGURATION の使用法を示します  
  
### <a name="a-grant-permission"></a>A. アクセス許可を付与します。  

この例は、ALTER DATABASE SCOPED CONFIGURATION を実行するために必要なアクセス許可を付与します。     
ユーザー [Joe] です。  
  
```tsql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. MAXDOP を設定します。  

この例の MAXDOP 設定プライマリ データベースと MAXDOP 1 = セカンダリ データベースの地理的レプリケーションのシナリオ 4 を = です。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
この例では、同じ値に設定されている地理的レプリケーション シナリオでは、プライマリ データベースをセカンダリ データベースの MAXDOP を設定します。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. LEGACY_CARDINALITY_ESTIMATION を設定します。  

この例は、セカンダリ データベースの地理的レプリケーションのシナリオで LEGACY_CARDINALITY_ESTIMATION を ON に設定します。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
この例は、geo レプリケーションのシナリオでは、プライマリ データベースは、セカンダリ データベースの LEGACY_CARDINALITY_ESTIMATION を設定します。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. PARAMETER_SNIFFING を設定します。  

この例は、プライマリ データベースの地理的レプリケーションのシナリオで PARAMETER_SNIFFING を OFF に設定します。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
この例は、プライマリ データベースの地理的レプリケーションのシナリオで PARAMETER_SNIFFING を OFF に設定します。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
この例ではプライマリ データベースでは、セカンダリ データベースの PARAMETER_SNIFFING を設定します。   
geo レプリケーションのシナリオです。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING =PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. QUERY_OPTIMIZER_HOTFIXES を設定します。  

プライマリ データベースの QUERY_OPTIMIZER_HOTFIXES を ON に設定します。   
geo レプリケーションのシナリオです。  

```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. プロシージャ キャッシュをクリア  

この例では、(プライマリ データベースに対してのみ可能)、プロシージャ キャッシュをクリアします。  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. IDENTITY_CACHE を設定します。

**適用されます**: SQL Server 2017、および Azure SQL データベース (機能は、パブリック プレビューで) 

この例では、id キャッシュが無効にします。

```tsql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

## <a name="additional-resources"></a>その他のリソース

### <a name="maxdop-resources"></a>MAXDOP リソース 
* [推奨事項と SQL Server の"max degree of parallelism"構成オプションのガイドライン](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>LEGACY_CARDINALITY_ESTIMATION リソース    
* [基数推定 (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* [SQL Server 2014 の基数推定機能によるクエリプランの最適化](https://msdn.microsoft.com/library/dn673537.aspx)

### <a name="parametersniffing-resources"></a>PARAMETER_SNIFFING リソース    
* [「パラメーターが僕されます」です。](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>QUERY_OPTIMIZER_HOTFIXES リソース    
* [SQL Server クエリ オプティマイザーの修正プログラム トレース フラグ 4199 サービス モデル](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>詳細情報  
 [sys.database_scoped_configurations & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [トレース フラグ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   
 [sys.configurations & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
  
  

