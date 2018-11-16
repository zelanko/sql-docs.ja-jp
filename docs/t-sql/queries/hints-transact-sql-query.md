---
title: クエリ ヒント (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Query_Hint_TSQL
- Query_TSQL
- Query
- Query Hint
- MAX_GRANT_PERCENT
- MAX_GRANT_PERCENT_TSQL
- MIN_GRANT_PERCENT
- MIN_GRANT_PERCENT_TSQL
- EXTERNALPUSHDOWN
- EXTERNALPUSHDOWN_TSQL
- NOLOCK_TSQL
- MAXDOP_TSQL
- USE_HINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REPORT PLAN query hint
- FORCE ORDER query hint
- HASH JOIN query hint
- query hints [SQL Server]
- OPTIMIZE FOR query hint
- FORCESCAN query hint
- RECOMPILE query hint
- MAXRECURSION query hint
- MERGE JOIN query hint
- HASH GROUP query hint
- KEEP PLAN query hint
- UNION query hint
- FORCESEEK query hint
- ORDER GROUP query hint
- LOOP JOIN query hint
- KEEPFIXED PLAN query hint
- FAST query hint
- MAXDOP query hint
- PARAMETERIZATION query hint
- hints [SQL Server], query
- JOIN query hint
- USE PLAN query hint
- EXPAND VIEWS query hint
- MAX_GRANT_PERCENT query hint
- MIN_GRANT_PERCENT query hint
- EXTERNALPUSHDOWN query hint
- USE HINT query hint
- QUERY_PLAN_PROFILE query hint
ms.assetid: 66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d0b16356be0c36f48f9e82b4a49e483c3eac529b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51704090"
---
# <a name="hints-transact-sql---query"></a>ヒント (Transact-SQL) - Query
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  クエリ ヒントは、指定されたヒントをクエリ全体で使用する必要があることを指定します。 クエリ ヒントは、ステートメント内のすべての演算子に影響を与えます。 メイン クエリで UNION を使用する場合、UNION 操作を含む最後のクエリだけに OPTION 句を指定できます。 クエリ ヒントは、[OPTION 句](../../t-sql/queries/option-clause-transact-sql.md)の一部として指定します。 複数のクエリ ヒントが原因でクエリ オプティマイザーが有効なプランを生成できない場合は、エラー 8622 が発生します。  
  
> [!CAUTION]  
> 通常、クエリにとって最適な実行プランが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーによって選択されるため、ヒントは、経験を積んだ開発者やデータベース管理者が最後の手段としてのみ使用することをお勧めします。  
  
 **適用対象:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [MERGE](../../t-sql/statements/merge-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
<query_hint > ::=   
{ { HASH | ORDER } GROUP   
  | { CONCAT | HASH | MERGE } UNION   
  | { LOOP | MERGE | HASH } JOIN   
  | EXPAND VIEWS   
  | FAST number_rows   
  | FORCE ORDER   
  | { FORCE | DISABLE } EXTERNALPUSHDOWN  
  | IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
  | KEEP PLAN   
  | KEEPFIXED PLAN  
  | MAX_GRANT_PERCENT = percent  
  | MIN_GRANT_PERCENT = percent  
  | MAXDOP number_of_processors   
  | MAXRECURSION number   
  | NO_PERFORMANCE_SPOOL   
  | OPTIMIZE FOR ( @variable_name { UNKNOWN | = literal_constant } [ , ...n ] )  
  | OPTIMIZE FOR UNKNOWN  
  | PARAMETERIZATION { SIMPLE | FORCED }   
  | RECOMPILE  
  | ROBUST PLAN   
  | USE HINT ( '<hint_name>' [ , ...n ] )
  | USE PLAN N'xml_plan'  | TABLE HINT ( exposed_object_name [ , <table_hint> [ [, ]...n ] ] )  
}  
  
<table_hint> ::=  
[ NOEXPAND ] {   
    INDEX ( index_value [ ,...n ] ) | INDEX = ( index_value )  
  | FORCESEEK [( index_value ( index_column_name [,... ] ) ) ]  
  | FORCESCAN  
  | HOLDLOCK   
  | NOLOCK   
  | NOWAIT  
  | PAGLOCK   
  | READCOMMITTED   
  | READCOMMITTEDLOCK   
  | READPAST   
  | READUNCOMMITTED   
  | REPEATABLEREAD   
  | ROWLOCK   
  | SERIALIZABLE   
  | SNAPSHOT  
  | SPATIAL_WINDOW_MAX_CELLS = integer  
  | TABLOCK   
  | TABLOCKX   
  | UPDLOCK   
  | XLOCK  
}  
```  
  
## <a name="arguments"></a>引数  
 { HASH | ORDER } GROUP  
 クエリの GROUP BY 句または DISTINCT 句に記述されている集計でハッシュまたは順序付けを使用することを指定します。  
  
 { MERGE | HASH | CONCAT } UNION  
 UNION セットをマージ、ハッシュ、または連結することによって、すべての UNION 操作を実行することを指定します。 複数の UNION ヒントを指定した場合、クエリ オプティマイザーは指定されたヒントの中から最も負荷の軽い方法を選択します。  
  
 { LOOP | MERGE | HASH } JOIN  
 LOOP JOIN、MERGE JOIN、または HASH JOIN によって、すべての結合操作がクエリ全体で実行されることを指定します。 結合ヒントを複数指定した場合は、可能なヒントの中から最も負荷の軽い方法がオプティマイザーによって選択されます。  
  
 同じクエリの中で、特定のテーブルのペアに対して FROM 句に結合ヒントが指定されている場合も、2 つのテーブルの結合ではこの結合ヒントが優先されますが、クエリ ヒントは引き続き有効です。 このため、テーブルのペアの結合ヒントは、クエリ ヒント内で許可される結合方法の選択を制限できるだけです。 詳細については、「[結合ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-join.md)」を参照してください。  
  
 EXPAND VIEWS  
 インデックス付きビューが展開されていることを指定します。これによって、クエリ オプティマイザーがインデックス付きビューをクエリの一部の代わりであると見なすことがなくなります。 ビューが展開されるのは、ビュー名がクエリ テキスト内のビュー定義に置換される場合です。  
  
 このクエリ ヒントは、インデックス付きビューを直接使用することを実質的に禁止し、クエリ プラン内のインデックス付きビューにインデックスを指定します。  
  
 クエリの SELECT 要素でビューが直接参照され、WITH (NOEXPAND) または WITH (NOEXPAND, INDEX( *index_value* [ **,**_...n_ ] ) ) が指定されている場合のみ、インデックス付きビューは展開されません。 クエリ ヒント WITH (NOEXPAND) の詳細については、「[FROM](../../t-sql/queries/from-transact-sql.md)」を参照してください。  
  
 INSERT、UPDATE、MERGE、DELETE ステートメントなど、ステートメントの SELECT 要素内のビューのみが、ヒントの影響を受けます。  
  
 FAST *number_rows*  
 最初の *number_rows* を高速検索するためにクエリの最適化を行うことを指定します。 これは、負以外の整数です。 最初の *number_rows* を返した後、クエリは実行を続け、完全な結果セットを作成します。  
  
 FORCE ORDER  
 クエリの構文に示されている結合順序が、クエリの最適化中、保持されることを指定します。 FORCE ORDER を使用しても、クエリ オプティマイザーのロールの逆引き動作に影響はありません。  
  
> [!NOTE]  
> MERGE ステートメント内で、WHEN SOURCE NOT MATCHED 句が指定されていない限り、既定の結合順序としてソース テーブルはターゲット テーブルよりも前にアクセスされます。 FORCE ORDER を指定すると、この既定の動作が維持されます。  
  
 {FORCE |無効にする EXTERNALPUSHDOWN}  
 強制または式を使用して hadoop の該当する計算のプッシュ ダウンを無効にします。 PolyBase を使用してクエリにのみ適用されます。 Azure ストレージに、下へプッシュされませんされます。  
  
 KEEP PLAN  
 クエリ オプティマイザーに対して、クエリに推定される再コンパイルしきい値を緩和することを指定します。 推定される再コンパイルしきい値とは、UPDATE、DELETE、MERGE、または INSERT ステートメントの実行により、予測した回数のインデックス列変更がテーブルに加えられた場合に、クエリを自動的に再コンパイルする時点のことです。 KEEP PLAN を指定することによって、テーブルに複数の更新が加えられても、クエリは頻繁に再コンパイルされません。  
  
 KEEPFIXED PLAN  
 統計情報の変更に応じてクエリを再コンパイルしないようにクエリ オプティマイザーを設定します。 KEEPFIXED PLAN を指定することによって、クエリの基になるテーブルのスキーマが変更された場合、またはそのテーブルに対して **sp_recompile** が実行された場合のみ、クエリが再コンパイルされます。  
  
 IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 クエリで非クラスター化メモリ最適化列ストア インデックスが使用されないようにします。 クエリに、列ストア インデックスの使用を回避するクエリ ヒントと、列ストア インデックスを使用するインデックス ヒントがある場合、ヒントが競合してクエリはエラーを返します。  
  
 MAX_GRANT_PERCENT = *percent*  
 最大メモリ サイズ (% 単位) を付与します。 クエリは、この制限を超えることはできないことが保証されます。 Resource Governor の設定がこのヒントで指定されている値より小さい場合、実際の制限はこれよりも小さくなる可能性があります。 有効な値では、0.0 ～ 100.0 します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 MIN_GRANT_PERCENT = *percent*  
 最低限のメモリ サイズ (% 単位) を付与する = 既定の制限の % です。 クエリは、少なくとも、クエリの開始に必要なメモリが必要となるために、(必要なメモリ、最小の許可) の最大値を取得することが保証します。 有効な値では、0.0 ～ 100.0 します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 MAXDOP *number*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 このオプションを指定しているクエリに対して、**sp_configure** およびリソース ガバナーの **max degree of parallelism** 構成オプションをオーバーライドします。 MAXDOP クエリ ヒントは、sp_configure で構成されている値を超えて指定できます。 MAXDOP の値がリソース ガバナーで構成されている値を超える場合は、「[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)」で説明されているように、[!INCLUDE[ssDE](../../includes/ssde-md.md)]でリソース ガバナーの MAXDOP 値が使用されます。 MAXDOP クエリ ヒントを使用している場合は、**max degree of parallelism** 構成オプションで使用されるすべての意味ルールを適用できます。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
  
> [!WARNING]     
> MAXDOP が 0 に設定されている場合、サーバーでは最大限の並列処理が実行されます。  
  
 MAXRECURSION *number*     
 このクエリで許可される最大再帰数を指定します。 *number* は、0 ～ 32,767 の負ではない整数です。 0 を指定した場合、制限は適用されません。 このオプションが指定されない場合、サーバーの既定の上限値である 100 が使用されます。  
  
 クエリの実行中に MAXRECURSION の指定した上限値または既定上限値に達した場合、クエリは終了し、エラーが返されます。  
  
 このエラーのため、ステートメントのすべての効果がロールバックされます。 ステートメントが SELECT ステートメントであった場合、結果の一部が返されるか、結果がまったく返されないかのいずれかになります。 結果の一部が返された場合でも、指定した最大再帰レベルを超える再帰レベルのすべての行は含まれていない可能性があります。  
  
 詳細については、「[WITH common_table_expression &#40;Transact-SQL&#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)」を参照してください。     
  
 NO_PERFORMANCE_SPOOL    
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 Spool 操作は、(を除く、計画、スプールが有効な更新のセマンティクスを保証するために必要な場合) のクエリ プランに追加されないようにします。 一部のシナリオでは、spool 操作にパフォーマンスが低下する可能性があります。 たとえば、spool のサイズは、tempdb を使用し、スプール操作を実行している多くの同時実行クエリがある場合に、tempdb の競合が発生することがあります。  
  
 OPTIMIZE FOR ( *@variable_name* { UNKNOWN | = *literal_constant }* [ **,** ...*n* ] )     
 クエリをコンパイルおよび最適化するときにローカル変数に対して特定の値を使用するように、クエリ オプティマイザーに指示します。 この値はクエリを最適化する過程でのみ使用され、クエリの実行時には使用されません。  
  
 *@variable_name*  
 クエリで使用されるローカル変数の名前です。このローカル変数に OPTIMIZE FOR クエリ ヒントで使用する値を割り当てます。  
  
 *UNKNOWN*  
 クエリ オプティマイザーでのクエリの最適化時に、初期値の代わりに統計データを使用してローカル変数の値を決定することを指定します。  
  
 *literal_constant*  
 OPTIMIZE FOR クエリ ヒントで使用する、*@variable_name* に割り当てるリテラル定数値です。 *literal_constant* は、クエリの最適化の過程でのみ使用され、クエリ実行時に *@variable_name* の値としては使用されません。 *literal_constant* には、リテラル定数として表現できる任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型を指定できます。 *literal_constant* のデータ型は、*@variable_name* がクエリ内で参照するデータ型に暗黙的に変換できる必要があります。  
  
 OPTIMIZE FOR はオプティマイザーの既定のパラメーター検出動作を無効にする場合や、プラン ガイドを作成する場合に使用できます。 詳細については、「[ストアド プロシージャの再コンパイル](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md)」を参照してください。  
  
 OPTIMIZE FOR UNKNOWN  
 クエリ オプティマイザーでクエリをコンパイルおよび最適化するときに、強制パラメーター化によって作成されたパラメーターも含め、すべてのローカル変数に対して初期値の代わりに統計データを使用することを指定します。  
  
 同一のクエリ ヒント内で OPTIMIZE FOR @variable_name = *literal_constant* と OPTIMIZE FOR UNKNOWN が使用されている場合、クエリ オプティマイザーでは、特定の値に対しては指定された *literal_constant* を使用し、残りの変数値には UNKNOWN を使用します。 これらの値はクエリを最適化する過程でのみ使用され、クエリの実行時には使用されません。  
  
 PARAMETERIZATION { SIMPLE | FORCED }     
 クエリのコンパイル時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーがそのクエリに適用するパラメーター化のルールを指定します。  
  
> [!IMPORTANT]  
> PARAMETERIZATION クエリ ヒントは、PARAMETERIZATION データベース SET オプションの現在の設定をオーバーライドするため、プラン ガイドの内部でのみ指定できます。 クエリの中で直接指定することはできません。    
> 詳細については、「[プラン ガイドを使用したクエリのパラメーター化動作の指定](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)」を参照してください。
  
 SIMPLE は、クエリ オプティマイザーに対して簡易パラメーター化を試行するように指示します。 FORCED は、クエリ オプティマイザーに対して強制パラメーター化を試行するように指示します。 詳細については、「クエリ処理アーキテクチャ ガイド」の「[強制パラメーター化](../../relational-databases/query-processing-architecture-guide.md#ForcedParam)」および「クエリ処理アーキテクチャ ガイド」の「[簡易パラメーター化](../../relational-databases/query-processing-architecture-guide.md#SimpleParam)」を参照してください。  

 RECOMPILE  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] に、クエリの新しい一時的なプランを生成し、クエリ実行完了直後にそのプランを破棄するよう指示します。 生成されたクエリ プランは、RECOMPILE ヒントを指定しないで同じクエリを実行したときにキャッシュに格納されるプランを置き換えません。 RECOMPILE を指定しない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]はクエリ プランをキャッシュして再利用します。 クエリ プランをコンパイルする場合、RECOMPILE クエリ ヒントは、クエリ内のローカル変数の現在値を使用し、クエリがストアド プロシージャ内にある場合は任意のパラメーターに渡された現在値を使用します。  
  
 RECOMPILE は、ストアド プロシージャ全体ではなくその中のクエリのサブセットだけを再コンパイルする必要がある場合に、WITH RECOMPILE 句を使用したストアド プロシージャを作成する代わりに使用すると便利です。 詳細については、「[ストアド プロシージャの再コンパイル](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md)」を参照してください。 RECOMPILE はプラン ガイドを作成するときにも利用できます。  
  
 ROBUST PLAN  
 クエリ オプティマイザーで、最大許容行サイズで動作するプランを試行するよう設定します。ただし、この場合は性能が低下する可能性があります。 クエリの処理の際、中間テーブルや演算子が入力行よりも大きな行を格納し、処理しなければならない可能性があります。 行があまりに大きいと、演算子によっては行を処理できない場合もあります。 このような状態が発生すると、クエリの実行中に[!INCLUDE[ssDE](../../includes/ssde-md.md)]からエラーが出力されます。 ROBUST PLAN を使用することで、クエリ オプティマイザーに対して、このような問題を発生するクエリ プランを考慮しないことを指示します。  
  
 このようなプランが可能でない場合は、クエリ実行の後でエラー検出を行うのではなく、クエリ オプティマイザーがエラーを返します。 行は可変長列で構成されている可能性があります。[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が処理できる範囲を超えた最大可能サイズを持つように、行を定義できます。 通常、可能な最大サイズに関係なく、アプリケーションは[!INCLUDE[ssDE](../../includes/ssde-md.md)]の処理能力で実際に対応できるサイズの行を格納します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]が長すぎる行を検出した場合は、実行エラーが返されます。  
 
<a name="use_hint"></a> USE HINT ( **'**_hint\_name_**'** )    
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降) および [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。
 
 ヒント名を**単一引用符で囲んで**指定し、1 つ以上の追加のヒントをクエリ プロセッサに指定します。   

 次のヒント名がサポートされています。    
 
*  'ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS' <a name="use_hint_join_containment"></a>       
   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降のクエリ オプティマイザーの[基数推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)モデルで、結合に対して、既定の基本含有の推定の代わりに、単純な含有の推定を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にクエリ プランを生成させます。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9476 を指定した場合と同じです。 
*  'ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES' <a name="use_hint_correlation"></a>      
   相関関係を考慮するフィルターの AND 述語を見積もるときに、最低限の選択度を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にプランを生成させます。 これは、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以前のバージョンのカーディナリティ推定モデルで[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4137 を使用した場合と同じで、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9471 を [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降のバージョンのカーディナリティ推定モデルで使用した場合と同じ効果があります。
*  'DISABLE_BATCH_MODE_ADAPTIVE_JOINS'       
   バッチ モード アダプティブ結合を無効にします。 詳細については、「[バッチ モード アダプティブ結合](../../relational-databases/performance/adaptive-query-processing.md#batch-mode-adaptive-joins)」を参照してください。
*  'DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK'       
   バッチ モード メモリ許可フィードバックを無効にします。 詳細については、「[バッチ モード メモリ許可フィードバック](../../relational-databases/performance/adaptive-query-processing.md#batch-mode-memory-grant-feedback)」を参照してください。
*  'DISABLE_INTERLEAVED_EXECUTION_TVF'      
   複数ステートメントのテーブル値関数のインターリーブ実行を無効にします。 詳細については、「[複数ステートメントのテーブル値関数のインターリーブ実行](../../relational-databases/performance/adaptive-query-processing.md#interleaved-execution-for-multi-statement-table-valued-functions)」を参照してください。
*  'DISABLE_OPTIMIZED_NESTED_LOOP'      
   クエリ プランを生成するときに、最適化された入れ子になったループ結合に対して並べ替え操作 (バッチ ソート) を使用しないように、クエリ プロセッサに指示します。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2340 を指定した場合と同じです。
*  'DISABLE_OPTIMIZER_ROWGOAL' <a name="use_hint_rowgoal"></a>      
   TOP、OPTION (FAST N)、IN、EXISTS のいずれかのキーワードを含むクエリで行の目標の調整を使用しないプランを SQL Server に生成させます。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4138 を指定した場合と同じです。
*  'DISABLE_PARAMETER_SNIFFING'      
   クエリをコンパイルするときに最初に使用されていたパラメーター値にクエリ プランが依存しないようにするため、1 つまたは複数のパラメーターを指定してクエリをコンパイルする際に、平均データ分布を使用するようにクエリ オプティマイザーに指示します。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4136 を指定した場合、または[データベース スコープ構成](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)を PARAMETER_SNIFFING=OFF に設定した場合と同じです。
*  'ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS'      
   カーディナリティ推定が必要なすべての先頭のインデックス列に対して、クイック統計情報 (ヒストグラム修正) を自動的に生成できるようにします。 カーディナリティを推定するために使用されるヒストグラムは、この列の実際の最大値または最小値を考慮するクエリのコンパイル時に調整されます。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4139 を指定した場合と同じです。 
*  'ENABLE_QUERY_OPTIMIZER_HOTFIXES'     
   クエリ オプティマイザー修正プログラム (SQL Server の累積的な更新プログラムとサービス パックでリリースされた変更) を有効にします。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 4199 を指定した場合、または[データベース スコープ構成](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)を QUERY_OPTIMIZER_HOTFIXES=ON に設定した場合と同じです。
*  'FORCE_DEFAULT_CARDINALITY_ESTIMATION'      
   現在のデータベース互換性レベルに対応する[カーディナリティ推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)モデルを使用するようにクエリ オプティマイザーを設定します。 このヒントを使用して、[データベース スコープ構成](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)の LEGACY_CARDINALITY_ESTIMATION=ON 設定または[トレース フラグ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 9481 をオーバーライドします。
*  'FORCE_LEGACY_CARDINALITY_ESTIMATION' <a name="use_hint_ce70"></a>      
   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以前のバージョンの [基数推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)モデルを使用するようにクエリ オプティマイザーを設定します。 これは、[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 9481 を指定した場合、または[データベース スコープ構成](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)を LEGACY_CARDINALITY_ESTIMATION=ON に設定した場合と同じです。
*  'QUERY_OPTIMIZER_COMPATIBILITY_LEVEL_n'          
 クエリがデータベース互換レベル *n* でコンパイルされている場合と同じように、クエリ レベルでのクエリ オプティマイザーの動作を設定します。*n* はサポートされているデータベース互換レベルです。 現在サポートされている *n* の値の一覧については、「[sys.dm_exec_valid_use_hints](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md)」をご覧ください。 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU10 以降)。    

   > [!NOTE]
   > 既定またはレガシのカーディナリティ推定の設定が、データベース スコープ構成、トレース フラグ、または QUERYTRACEON などの別のクエリ ヒントによって適用されている場合、QUERY_OPTIMIZER_COMPATIBILITY_LEVEL_n ヒントはそれをオーバーライドしません。   
   > このヒントは、クエリ オプティマイザーの動作にのみ影響します。 特定のデータベース機能の可用性など、[データベース互換レベル](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)に依存する可能性のある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の他の機能には影響しません。  
   > このヒントについて詳しくは、「[Developer’s Choice: Hinting Query Execution model](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-hinting-query-execution-model)」(開発者の選択: クエリ ヒント実行モデル) をご覧ください。
    
*  'QUERY_PLAN_PROFILE'      
 クエリの軽量プロファイリングを有効にします。 この新しいヒントを含むクエリが完了したら、新しい拡張イベントである query_plan_profile が起動されます。 この拡張イベントでは、実行の統計と query_post_execution_showplan 拡張イベントのような実際の実行プラン XML が公開されますが、新しいヒントを含むクエリのみが対象です。 **適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 CU3 および [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU11 以降)。 

  > [!NOTE]
  > query_post_execution_showplan 拡張イベントの収集を有効にした場合は、サーバー上で実行しているすべてのクエリに標準的なプロファイリング インフラストラクチャが追加されるので、全体的なサーバー パフォーマンスに影響する可能性があります。      
  > *query_thread_profile* 拡張イベントのコレクションを有効にして軽量プロファイリング インフラストラクチャを代わりに使用する場合、パフォーマンス オーバーヘッドがはるかに少なくなりますが、依然として全体的なサーバー パフォーマンスに影響します。       
  > query_plan_profile 拡張イベントを有効にした場合、軽量プロファイリング インフラストラクチャは QUERY_PLAN_PROFILE を使用して実行されるクエリに対してのみ有効になるので、サーバー上の他のワークロードには影響しません。 このヒントを使用して、サーバー ワークロードの他の部分に影響を与えずに特定のクエリをプロファイリングします。
  > 軽量プロファイリングについて詳しくは、「[Developers Choice: Query progress - anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/)」(開発者の選択: クエリの進行状況 - いつでも、どこでも) をご覧ください。
 
サポートされているすべての USE HINT 名の一覧は、動的管理ビューの [sys.dm_exec_valid_use_hints](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md) を使用して照会できます。    

> [!TIP]
> ヒント名では大文字と小文字が区別されません。   
  
> [!IMPORTANT] 
> 一部の USE HINT ヒントは、グローバルまたはセッション レベルで有効になっているトレース フラグや、データベース スコープ構成設定と競合する場合があります。 この場合、クエリ レベル ヒント (USE HINT) が常に優先されます。 USE HINT が別のクエリ ヒントまたはクエリ レベルで (QUERYTRACEON などによって) 有効になっているトレース フラグと競合する場合、クエリを実行しようとすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってエラーが生成されます。 

 USE PLAN N **'**_xml\_plan_**'**     
 **'**_xml\_plan_**'** で指定されているクエリの既存のクエリ プランを使用するように、クエリ オプティマイザーを設定します。 USE PLAN は、INSERT、UPDATE、MERGE、または DELETE の各ステートメントに指定することはできません。  
  
TABLE HINT **(**_exposed\_object\_name_ [ **,** \<table_hint>  **[,]**..._n_ ] ] **)** *exposed_object_name* に対応するテーブルまたはビューに、指定したテーブル ヒントを適用します。 [プラン ガイド](../../relational-databases/performance/plan-guides.md)のコンテキスト内でのみ、テーブル ヒントをクエリ ヒントとして使用することをお勧めします。  
  
 *exposed_object_name* には、次のいずれかの参照を指定できます。  
  
-   クエリの [FROM](../../t-sql/queries/from-transact-sql.md) 句内でテーブルまたはビューに対して別名を使用する場合、*exposed_object_name* は別名です。  
  
-   別名を使用しない場合、*exposed_object_name* は、FROM 句で参照されているテーブルまたはビューと完全に一致している必要があります。 たとえば、2 つの部分で構成される名前を使用してテーブルまたはビューが参照されている場合、*exposed_object_name* は、2 つの部分で構成される同じ名前です。  
  
 テーブル ヒントを指定しないで *exposed_object_name* を指定した場合、オブジェクトのテーブル ヒントの一部としてクエリに指定された任意のインデックスは無視され、インデックスの使用はクエリ オプティマイザーによって決定されます。 この手法を使用すると、元のクエリに変更を加えることができない場合に INDEX テーブル ヒントの効果を除去できます。 例 J を参照してください。  
  
**\<table_hint> ::=** { [ NOEXPAND ] { INDEX ( *index_value* [ ,...*n* ] ) | INDEX = ( *index_value* ) | FORCESEEK [**(**_index\_value_**(**_index\_column\_name_ [**,**... ] **))** ]| FORCESCAN | HOLDLOCK | NOLOCK | NOWAIT | PAGLOCK | READCOMMITTED | READCOMMITTEDLOCK | READPAST | READUNCOMMITTED | REPEATABLEREAD | ROWLOCK | SERIALIZABLE | SNAPSHOT | SPATIAL_WINDOW_MAX_CELLS | TABLOCK | TABLOCKX | UPDLOCK | XLOCK } *exposed_object_name* に対応するテーブルまたはビューにクエリ ヒントとして適用するテーブル ヒントを指定します。 これらのヒントの説明については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 INDEX、FORCESCAN、および FORCESEEK 以外のテーブル ヒントは、クエリで既に WITH 句を使用してテーブル ヒントが指定されていない限り、クエリ ヒントとして使用できません。 詳細については、「解説」を参照してください。  
  
> [!CAUTION] 
> パラメーターを使用して FORCESEEK を指定すると、オプティマイザーで考慮できるプラン数の制限は、パラメーターなしで FORCESEEK を指定した場合よりも多くなります。 これにより、"プランを生成できない" というエラーが生じる回数が増加する可能性があります。 将来のリリースでは、オプティマイザーに対して内部変更を行うため、より多くのプランを考慮できるようになります。  
  
## <a name="remarks"></a>Remarks  
 ステートメント内部で SELECT 句が使用されている場合を除き、クエリ ヒントは INSERT ステートメントでは指定できません。  
  
 クエリ ヒントはサブクエリではなく、最上位レベルのクエリでのみ指定できます。 テーブル ヒントをクエリ ヒントとして指定する場合、最上位レベルのクエリまたはサブクエリ内にヒントを指定できます。ただし、TABLE HINT 句の *exposed_object_name* に対して指定する値は、クエリまたはサブクエリ内で公開された名前と完全に一致する必要があります。  
  
## <a name="specifying-table-hints-as-query-hints"></a>クエリ ヒントとしてのテーブル ヒントの指定  
 [プラン ガイド](../../relational-databases/performance/plan-guides.md)のコンテキスト内でのみ、INDEX、FORCESCAN、または FORCESEEK テーブル ヒントをクエリ ヒントとして使用することをお勧めします。 プラン ガイドは、たとえばクエリがサードパーティ アプリケーションである場合のように、元のクエリに変更を加えることができない場合に便利です。 プラン ガイドに指定されたクエリ ヒントは、コンパイルおよび最適化される前にクエリに追加されます。 アドホック クエリの場合は、プラン ガイド ステートメントをテストするときだけ TABLE HINT 句を使用します。 その他のアドホック クエリに対しては、テーブル ヒント内でのみこれらのヒントを指定することをお勧めします。  
  
 クエリ ヒントとして指定した場合、INDEX、FORCESCAN、および FORCESEEK テーブル ヒントは次のオブジェクトに対して有効です。  
  
-   テーブル  
-   ビュー  
-   インデックス付きビュー  
-   共通テーブル式 (ヒントは、結果セットが共通テーブル式に入力される SELECT ステートメントに指定する必要があります)  
-   動的管理ビュー  
-   名前付きサブクエリ  
  
INDEX、FORCESCAN、および FORCESEEK テーブル ヒントは、既存のテーブル ヒントを持たないクエリのクエリ ヒントとして指定できます。また、それぞれ、クエリ内の既存の INDEX、FORCESCAN、または FORCESEEK ヒントの代わりに使用することもできます。 INDEX、FORCESCAN、および FORCESEEK 以外のテーブル ヒントは、クエリで既に WITH 句を使用してテーブル ヒントが指定されていない限り、クエリ ヒントとして使用できません。 この場合に、そのクエリのセマンティックを維持するには、OPTION 句で TABLE HINT を使用して、対応するヒントもクエリ ヒントとして指定する必要があります。 たとえば、クエリにテーブル ヒント NOLOCK が含まれている場合、プラン ガイドの **@hints** パラメーターの OPTION 句にも NOLOCK ヒントが含まれている必要があります。 K. の例を参照してください。せず、対応するクエリ ヒントでは、OPTION 句で TABLE HINT を使用して、INDEX、FORCESCAN、または FORCESEEK 以外のテーブル ヒントが指定されている場合またはその逆の場合(OPTION 句を変更するクエリのセマンティックになることを示す) にエラー 8702 が発生し、クエリが失敗します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-merge-join"></a>A. MERGE JOIN を使用する  
 次の例では、クエリの JOIN 操作を MERGE JOIN によって実行することを指定します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
SELECT *   
FROM Sales.Customer AS c  
INNER JOIN Sales.CustomerAddress AS ca ON c.CustomerID = ca.CustomerID  
WHERE TerritoryID = 5  
OPTION (MERGE JOIN);  
GO    
```  
  
### <a name="b-using-optimize-for"></a>B. OPTIMIZE FOR を使用する  
 次の例では、クエリ オプティマイザーでのクエリの最適化時に、ローカル変数 `'Seattle'` に値 `@city_name` を使用し、統計データを使用してローカル変数 `@postal_code` の値を決定するように指定しています。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
DECLARE @city_name nvarchar(30);  
DECLARE @postal_code nvarchar(15);  
SET @city_name = 'Ascheim';  
SET @postal_code = 86171;  
SELECT * FROM Person.Address  
WHERE City = @city_name AND PostalCode = @postal_code  
OPTION ( OPTIMIZE FOR (@city_name = 'Seattle', @postal_code UNKNOWN) );  
GO  
```  
  
### <a name="c-using-maxrecursion"></a>C. MAXRECURSION を使用する  
 MAXRECURSION を使用すると、不適切に作成された再帰共通テーブル式による無限ループの発生を防ぐことができます。 次の例では、無限ループを意図的に作成し、MAXRECURSION ヒントを使用して再帰レベルの数を 2 に制限しています。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
--Creates an infinite loop  
WITH cte (CustomerID, PersonID, StoreID) AS  
(  
    SELECT CustomerID, PersonID, StoreID  
    FROM Sales.Customer  
    WHERE PersonID IS NOT NULL  
  UNION ALL  
    SELECT cte.CustomerID, cte.PersonID, cte.StoreID  
    FROM cte   
    JOIN  Sales.Customer AS e   
        ON cte.PersonID = e.CustomerID  
)  
--Uses MAXRECURSION to limit the recursive levels to 2  
SELECT CustomerID, PersonID, StoreID  
FROM cte  
OPTION (MAXRECURSION 2);  
GO  
```  
  
 コードのエラーが訂正されると、MAXRECURSION は不要になります。  
  
### <a name="d-using-merge-union"></a>D. MERGE UNION を使用する  
 次の例では、MERGE UNION クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
SELECT *  
FROM HumanResources.Employee AS e1  
UNION  
SELECT *  
FROM HumanResources.Employee AS e2  
OPTION (MERGE UNION);  
GO  
```  
  
### <a name="e-using-hash-group-and-fast"></a>E. HASH GROUP および FAST を使用する  
 次の例では、HASH GROUP および FAST クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO    
```  
  
### <a name="f-using-maxdop"></a>F. MAXDOP を使用する  
 次の例では、MAXDOP クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```sql  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (MAXDOP 2);    
GO
```  
  
### <a name="g-using-index"></a>G. INDEX を使用する  
 次の例では、INDEX ヒントを使用します。 最初の例では、単一のインデックスを指定します。 2 番目の例では、1 つのテーブル参照に対して複数のインデックスを指定します。 INDEX ヒントはどちらの例においても別名が使用されているテーブルに適用されるので、公開されたオブジェクト名と同じ別名を TABLE HINT 句でも指定する必要があります。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX (IX_Employee_ManagerID)))';  
GO  
EXEC sp_create_plan_guide   
    @name = N'Guide2',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e, INDEX(PK_Employee_EmployeeID, IX_Employee_ManagerID)))';  
GO    
```  
  
### <a name="h-using-forceseek"></a>H. FORCESEEK を使用する  
 次の例では、FORCESEEK テーブル ヒントを使用します。 INDEX ヒントは 2 つの部分で構成される名前が使用されているテーブルに適用されるので、公開されたオブジェクト名と同じ 2 つの部分で構成される名前を TABLE HINT 句でも指定する必要があります。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide3',   
    @stmt = N'SELECT c.LastName, c.FirstName, HumanResources.Employee.Title  
              FROM HumanResources.Employee  
              JOIN Person.Contact AS c ON HumanResources.Employee.ContactID = c.ContactID  
              WHERE HumanResources.Employee.ManagerID = 3  
              ORDER BY c.LastName, c.FirstName;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT( HumanResources.Employee, FORCESEEK))';  
GO    
```  
  
### <a name="i-using-multiple-table-hints"></a>I. 複数のテーブル ヒントを使用する  
 次の例では、INDEX ヒントと FORCESEEK ヒントをそれぞれ別のテーブルに適用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide4',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX( IX_Employee_ManagerID))   
                       , TABLE HINT (c, FORCESEEK))';  
GO  
```  
  
### <a name="j-using-table-hint-to-override-an-existing-table-hint"></a>J. TABLE HINT を使用して既存のテーブル ヒントをオーバーライドする  
 次の例では、ヒントを指定しないで TABLE HINT ヒントを使用して、クエリの FROM 句に指定されている INDEX テーブル ヒントの動作をオーバーライドする方法を示します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide5',   
    @stmt = N'SELECT e.ManagerID, c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e WITH (INDEX (IX_Employee_ManagerID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT(e))';  
GO    
```  
  
### <a name="k-specifying-semantics-affecting-table-hints"></a>K. セマンティックに作用するテーブル ヒントを指定する  
 次の例では、クエリに 2 つのテーブル ヒントが含まれています。1 つは、セマンティックに作用する NOLOCK で、もう 1 つはセマンティックに作用しない INDEX です。 クエリのセマンティックを保持するために、プラン ガイドの OPTIONS 句に NOLOCK ヒントが指定されています。 NOLOCK ヒントに加えて、INDEX および FORCESEEK ヒントが指定されているので、ステートメントをコンパイルおよび最適化するときにクエリのセマンティックに作用しない INDEX ヒントが置き換えられます。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide6',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 3;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, INDEX(IX_Employee_ManagerID), NOLOCK, FORCESEEK))';  
GO    
```  
  
 次の例では、クエリのセマンティックを保持し、テーブル ヒントに指定されている以外のインデックスをオプティマイザーが選択できるようにする別の方法を示します。 これを実現するには、OPTIONS 句に (セマンティックに作用する) NOLOCK ヒントを指定する一方で、INDEX ヒントを持たないテーブル参照だけの TABLE HINT キーワードを指定します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide7',   
    @stmt = N'SELECT c.LastName, c.FirstName, e.Title  
              FROM HumanResources.Employee AS e   
                   WITH (NOLOCK, INDEX (PK_Employee_EmployeeID))  
              JOIN Person.Contact AS c ON e.ContactID = c.ContactID  
              WHERE e.ManagerID = 2;',  
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (TABLE HINT (e, NOLOCK))';  
GO  
```  
### <a name="l-using-use-hint"></a>L. USE HINT の使用  
 次の例では、RECOMPILE および USE HINT のクエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを使用します。  
  
**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]。  
  
```sql  
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (RECOMPILE, USE HINT ('ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES', 'DISABLE_PARAMETER_SNIFFING')); 
GO  
```  
    
## <a name="see-also"></a>参照  
 [Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
 [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)       
 [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)      
  
