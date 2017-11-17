---
title: "クエリ ヒント (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
ms.assetid: 66fb1520-dcdf-4aab-9ff1-7de8f79e5b2d
caps.latest.revision: 136
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b866e3ab0ee44c8b65a7b5064f0feb1e4f52aff9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hints-transact-sql---query"></a>ヒント (TRANSACT-SQL) のクエリ
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  クエリ ヒントは、指定されたヒントをクエリ全体で使用する必要があることを指定します。 クエリ ヒントは、ステートメント内のすべての演算子に影響を与えます。 メイン クエリで UNION を使用する場合、UNION 操作を含む最後のクエリだけに OPTION 句を指定できます。 クエリ ヒントがの一部として指定されて、 [OPTION 句](../../t-sql/queries/option-clause-transact-sql.md)です。 複数のクエリ ヒントが原因でクエリ オプティマイザーが有効なプランを生成できない場合は、エラー 8622 が発生します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通常、クエリ オプティマイザーがクエリの最適な実行プランを選択、お勧めのみ、最後の手段としてのヒントを使用して、経験を積んだ開発者やデータベース管理者です。  
  
 **適用対象:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [INSERT](../../t-sql/statements/insert-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 [マージ](../../t-sql/statements/merge-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
 同じクエリの中で、特定のテーブルのペアに対して FROM 句に結合ヒントが指定されている場合も、2 つのテーブルの結合ではこの結合ヒントが優先されますが、クエリ ヒントは引き続き有効です。 このため、テーブルのペアの結合ヒントは、クエリ ヒント内で許可される結合方法の選択を制限できるだけです。 詳細については、次を参照してください。[結合ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-join.md).  
  
 EXPAND VIEWS  
 インデックス付きビューが展開されていることを指定します。これによって、クエリ オプティマイザーがインデックス付きビューをクエリの一部の代わりであると見なすことがなくなります。 ビューが展開されるのは、ビュー名がクエリ テキスト内のビュー定義に置換される場合です。  
  
 このクエリ ヒントは、インデックス付きビューを直接使用することを実質的に禁止し、クエリ プラン内のインデックス付きビューにインデックスを指定します。  
  
 ビューがクエリおよび WITH (NOEXPAND) または WITH の SELECT 部分で直接参照されている場合にのみ、インデックス付きビューが展開されていない (NOEXPAND, INDEX ( *index_value* [ **、***...n*])) を指定します。 クエリ ヒント WITH (NOEXPAND) の詳細については、次を参照してください。 [FROM](../../t-sql/queries/from-transact-sql.md)です。  
  
 INSERT、UPDATE、MERGE、DELETE ステートメントなど、ステートメントの SELECT 要素内のビューのみが、ヒントの影響を受けます。  
  
 高速*number_rows*  
 最初の高速検索のクエリを最適化することを示す*number_rows です。* これは、負以外の整数です。 1 つ目後*number_rows*が返されます。 クエリの実行が続けられ、完全な結果セットを生成します。  
  
 FORCE ORDER  
 クエリの構文に示されている結合順序が、クエリの最適化中、保持されることを指定します。 FORCE ORDER を使用しても、クエリ オプティマイザーのロールの逆引き動作に影響はありません。  
  
> [!NOTE]  
>  MERGE ステートメント内で、WHEN SOURCE NOT MATCHED 句が指定されていない限り、既定の結合順序としてソース テーブルはターゲット テーブルよりも前にアクセスされます。 FORCE ORDER を指定すると、この既定の動作が維持されます。  
  
 {FORCE |無効にする EXTERNALPUSHDOWN}  
 強制または式を使用して hadoop の該当する計算のプッシュ ダウンを無効にします。 PolyBase を使用してクエリにのみ適用されます。 Azure ストレージに、下へプッシュされませんされます。  
  
 KEEP PLAN  
 クエリ オプティマイザーに対して、クエリに推定される再コンパイルしきい値を緩和することを指定します。 推定される再コンパイルしきい値とは、UPDATE、DELETE、MERGE、または INSERT ステートメントの実行により、予測した回数のインデックス列変更がテーブルに加えられた場合に、クエリを自動的に再コンパイルする時点のことです。 KEEP PLAN を指定することによって、テーブルに複数の更新が加えられても、クエリは頻繁に再コンパイルされません。  
  
 KEEPFIXED PLAN  
 統計情報の変更に応じてクエリを再コンパイルしないようにクエリ オプティマイザーを設定します。 KEEPFIXED PLAN を指定すると、または基になるテーブルのスキーマが変更された場合にのみ、クエリを再コンパイルにすることを確認**sp_recompile**それらのテーブルに対してを実行します。  
  
 IGNORE_NONCLUSTERED_COLUMNSTORE_INDEX  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 クエリが非クラスター化メモリ最適化列ストア インデックスを使用するを防ぎます。 クエリに、列ストア インデックスの使用を回避するクエリ ヒントと、列ストア インデックスを使用するためのインデックス ヒントがある場合、ヒントが競合してクエリはエラーを返します。  
  
 MAX_GRANT_PERCENT = *%*  
 最大メモリ サイズ (% 単位) を付与します。 クエリは、この制限を超えることはできないことが保証されます。 実際の制限は、リソース ガバナーの設定がこの値より小さい場合に下限にすることはできます。 有効な値では、0.0 ～ 100.0 します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 MIN_GRANT_PERCENT = *%*  
 最低限のメモリ サイズ (% 単位) を付与する = 既定の制限の % です。 クエリは、少なくとも、クエリの開始に必要なメモリが必要となるために、(必要なメモリ、最小の許可) の最大値を取得することが保証します。 有効な値では、0.0 ～ 100.0 します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 MAXDOP*数*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 上書き、**並列処理の次数の最大**構成オプションの**sp_configure**とは、このオプションを指定して、クエリのリソース ガバナーです。 MAXDOP クエリ ヒントは、sp_configure で構成されている値を超えて指定できます。 MAXDOP 値を超える場合、リソース ガバナーで構成されている、[!INCLUDE[ssDE](../../includes/ssde-md.md)]で説明されている、リソース ガバナーの MAXDOP 値を使用して[ALTER WORKLOAD GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-workload-group-transact-sql.md). 使用されるすべての意味ルール、**並列処理の次数の最大**MAXDOP クエリ ヒントを使用する場合に、構成オプションが適用されます。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。  
  
> [!WARNING]  
>  MAXDOP が 0 に設定されている場合、サーバーでは最大限の並列処理が実行されます。  
  
 MAXRECURSION*数*  
 このクエリで許可される最大再帰数を指定します。 *数*は 0 ~ 32,767 の負でない整数。 0 を指定した場合、制限は適用されません。 このオプションが指定されない場合、サーバーの既定の上限値である 100 が使用されます。  
  
 クエリの実行中に MAXRECURSION の指定した上限値または既定上限値に達した場合、クエリは終了し、エラーが返されます。  
  
 このエラーのため、ステートメントのすべての効果がロールバックされます。 ステートメントが SELECT ステートメントであった場合、結果の一部が返されるか、結果がまったく返されないかのいずれかになります。 結果の一部が返された場合でも、指定した最大再帰レベルを超える再帰レベルのすべての行は含まれていない可能性があります。  
  
 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 NO_PERFORMANCE_SPOOL  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 Spool 操作は、(を除く、計画、スプールが有効な更新のセマンティクスを保証するために必要な場合) のクエリ プランに追加されないようにします。 一部のシナリオでは、spool 操作にパフォーマンスが低下する可能性があります。 たとえば、spool のサイズは、tempdb を使用し、スプール操作を実行している多くの同時実行クエリがある場合に、tempdb の競合が発生することができます。  
  
 OPTIMIZE FOR (  *@variable_name*  {不明な | = *literal_constant}* [ **、** .*n* ] )  
 クエリをコンパイルおよび最適化するときにローカル変数に対して特定の値を使用するように、クエリ オプティマイザーに指示します。 この値はクエリを最適化する過程でのみ使用され、クエリの実行時には使用されません。  
  
 *@variable_name*  
 クエリで使用されるローカル変数の名前です。このローカル変数に OPTIMIZE FOR クエリ ヒントで使用する値を割り当てます。  
  
 *不明*  
 クエリ オプティマイザーでのクエリの最適化時に、初期値の代わりに統計データを使用してローカル変数の値を決定することを指定します。  
  
 *literal_constant*  
 割り当てるリテラル定数値は、  *@variable_name*  OPTIMIZE FOR クエリ ヒントを使用します。 *literal_constant*しの値としてではなく、クエリの最適化中にのみ使用 *@variable_name* クエリの実行中です。 *literal_constant*任意の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型をリテラル定数として表現できます。 データ型*literal_constant*必要があります暗黙的に、データに変換できる型でなくてを *@variable_name* クエリで参照します。  
  
 OPTIMIZE FOR はオプティマイザーの既定のパラメーター検出動作を無効にする場合や、プラン ガイドを作成する場合に使用できます。 詳細については、次を参照してください。[ストアド プロシージャを再コンパイル](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md)です。  
  
 OPTIMIZE FOR UNKNOWN  
 クエリ オプティマイザーでクエリをコンパイルおよび最適化するときに、強制パラメーター化によって作成されたパラメーターも含め、すべてのローカル変数に対して初期値の代わりに統計データを使用することを指定します。  
  
 場合 OPTIMIZE FOR @variable_name = *literal_constant* OPTIMIZE FOR UNKNOWN が同一のクエリ ヒントで使用、クエリ オプティマイザーが使用して、 *literal_constant*特定の値に指定されていると残りの変数の値を不明な値です。 これらの値はクエリを最適化する過程でのみ使用され、クエリの実行時には使用されません。  
  
 PARAMETERIZATION { SIMPLE | FORCED }  
 クエリのコンパイル時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーがそのクエリに適用するパラメーター化のルールを指定します。  
  
> [!IMPORTANT]  
>  PARAMETERIZATION クエリ ヒントはプラン ガイド内部でのみ指定できます。 クエリの中で直接指定することはできません。  
  
 SIMPLE は、クエリ オプティマイザーに対して簡易パラメーター化を試行するように指示します。 FORCED は、オプティマイザーに対して強制パラメーター化を試行するように指示します。 PARAMETERIZATION クエリ ヒントは、プラン ガイド内部の PARAMETERIZATION データベース SET オプションの現在の設定を上書きするのに使用します。 詳細については、次を参照してください。[を指定するパラメーター化クエリの動作を使用してプラン ガイドによって](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)です。  
  
 RECOMPILE  
 クエリの実行後、そのクエリに対して生成されたプランを破棄し、次回同じクエリが実行されたときにクエリ オプティマイザーにクエリ プランを再コンパイルさせるよう [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に指示します。 RECOMPILE を指定せず、[!INCLUDE[ssDE](../../includes/ssde-md.md)]クエリ プランをキャッシュして再利用します。 クエリ プランをコンパイルする場合、RECOMPILE クエリ ヒントは、クエリ内のローカル変数の現在値を使用し、クエリがストアド プロシージャ内にある場合は任意のパラメーターに渡された現在値を使用します。  
  
 RECOMPILE は、ストアド プロシージャ全体ではなくその中のクエリのサブセットだけを再コンパイルする必要がある場合に、WITH RECOMPILE 句を使用したストアド プロシージャを作成する代わりに使用すると便利です。 詳細については、次を参照してください。[ストアド プロシージャを再コンパイル](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md)です。 RECOMPILE はプラン ガイドを作成するときにも利用できます。  
  
 ROBUST PLAN  
 クエリ オプティマイザーで、最大許容行サイズで動作するプランを試行するよう設定します。ただし、この場合は性能が低下する可能性があります。 クエリの処理の際、中間テーブルや演算子が入力行よりも大きな行を格納し、処理しなければならない可能性があります。 行があまりに大きいと、演算子によっては行を処理できない場合もあります。 このような場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]クエリ実行中にエラーが生成されます。 ROBUST PLAN を使用することで、クエリ オプティマイザーに対して、このような問題を発生するクエリ プランを考慮しないことを指示します。  
  
 このようなプランが可能でない場合は、クエリ実行の後でエラー検出を行うのではなく、クエリ オプティマイザーがエラーを返します。 行は可変長列を含む可能性があります。[!INCLUDE[ssDE](../../includes/ssde-md.md)]では、機能を高めて、最大の潜在的なサイズを持つ行を定義する、[!INCLUDE[ssDE](../../includes/ssde-md.md)]それらを処理します。 一般に、最大の潜在的なサイズに関係なく、アプリケーションの行を格納、制限内での実際のサイズを[!INCLUDE[ssDE](../../includes/ssde-md.md)]を処理できます。 場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]が長すぎる、実行エラーが返される行を検出します。  
 
 使用してヒント ( **'***hint_name***'** )  
 **適用されます**: SQL Server (2016 SP1 以降) および Azure SQL データベースに適用されます。
 
 ヒントの名前で指定されたクエリ プロセッサに 1 つまたは複数追加するヒントを提供**単一引用符で囲んだ**です。 
  **適用されます**: で始まる[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1。

 次のヒント名がサポートされています。
 
*  ' DISABLE_OPTIMIZED_NESTED_LOOP'  
 クエリ プランを生成するときに、最適化された入れ子になったループ結合に対して並べ替え操作 (バッチ ソート) を使用しないように、クエリ プロセッサに指示します。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)2340 です。
*  ' FORCE_LEGACY_CARDINALITY_ESTIMATION'  
 クエリ オプティマイザーで使用する[基数の推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)のモデル[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と以前のバージョン。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)9481 または[Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) LEGACY_CARDINALITY_ESTIMATION を設定 = ON です。
*  ' ENABLE_QUERY_OPTIMIZER_HOTFIXES'  
 有効にはクエリ オプティマイザー修正プログラム (SQL Server の累積的な更新プログラムとサービス パックでリリースの変更) です。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)4199 または[Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) QUERY_OPTIMIZER_HOTFIXES 設定 = ON です。
*  ' DISABLE_PARAMETER_SNIFFING'  
 クエリ オプティマイザーでクエリがコンパイルされたときに使用された最初のパラメーター値、クエリ プランを独立したように、1 つまたは複数のパラメーターを持つクエリのコンパイル中に平均データ分布を使用するように指示します。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)4136 または[Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) PARAMETER_SNIFFING 設定 = OFF です。
*  ' ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES'  
 相関関係のために最低限の選択度を AND 述語フィルターを見積もるときに使用するプランを生成する SQL Server をによりします。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)4137 の基数の推定モデルを使用すると[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と以前のバージョンと同様の効果は、ときに[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)9471 は基数の使用推定モデル[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]またはそれ以降。
*  ' DISABLE_OPTIMIZER_ROWGOAL'  
 では、TOP、OPTION (FAST N) を含むクエリで行の目標の調整を使用しないプランを生成する SQL Server を招くまたはキーワードが存在します。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)4138 です。
*  ' ENABLE_HIST_AMENDMENT_FOR_ASC_KEYS'  
 自動的に生成されるクイックの統計情報 (ヒストグラム修正) どの基数の推定が必要です、先頭のインデックス列に対して有効にします。 基数を推定するために使用するヒストグラムは、この列の実際の最大値または最小値に対応するクエリのコンパイル時に調整されます。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)4139 です。 
*  ' ASSUME_JOIN_PREDICATE_DEPENDS_ON_FILTERS'  
 既定ベース コンテインメントという前提ではなく、クエリ オプティマイザーでの結合で簡単なコンテインメント前提を使用して、クエリ プランを生成する SQL server[基数の推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)のモデル[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]またはそれ以降。 これに相当[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)9476 です。 
*  ' FORCE_DEFAULT_CARDINALITY_ESTIMATION'  
 クエリ オプティマイザーで使用する[基数の推定](../../relational-databases/performance/cardinality-estimation-sql-server.md)現在のデータベース互換性レベルに対応するモデル。 このヒントを使用して上書きする[Database Scoped Configuration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) LEGACY_CARDINALITY_ESTIMATION を設定 = ON または[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)9481 です。
 
> [!TIP]
> ヒントの名前は区別されません。
  
  サポートされているすべてのヒントを使用する名前の一覧は、動的管理ビューを使用してクエリできる[sys.dm_exec_valid_use_hints](../../relational-databases/system-dynamic-management-views/sys-dm-exec-valid-use-hints-transact-sql.md)です。
> [!IMPORTANT] 
> USE ヒント ヒントは、グローバルに有効になっているトレース フラグと競合がありますか、セッション レベルまたはデータベース スコープ構成設定。 この場合、クエリ レベル ヒント (USE ヒント) は、常に優先されます。 使用するヒントと競合する別のクエリ ヒントまたはクエリ レベルで有効になっているトレース フラグ (など querytraceon ですが)、SQL Server クエリを実行しようとしているときにエラーが生成されます。 

 USE PLAN N**'***xml_plan***'**  
 指定されているクエリの既存のクエリ プランを使用する、クエリ オプティマイザー **'***xml_plan***'**です。 USE PLAN は、INSERT、UPDATE、MERGE、または DELETE の各ステートメントに指定することはできません。  
  
テーブル ヒント**(***exposed_object_name* [ **、** \<table_hint > [**、** ]. *n*  ] **)**をテーブルまたはビューに対応する、指定したテーブル ヒントを適用*exposed_object_name*です。 コンテキストのみでのクエリ ヒントとしてのテーブル ヒントを使用することをお勧め、[プラン ガイド](../../relational-databases/performance/plan-guides.md)です。  
  
 *exposed_object_name*次の参照のいずれかになります。  
  
-   テーブルまたはビューのエイリアスを使用する場合、 [FROM](../../t-sql/queries/from-transact-sql.md) 、クエリの句*exposed_object_name*エイリアスです。  
  
-   別名を使用しない場合は、 *exposed_object_name*のテーブルまたはビューの FROM 句で参照されている、完全に一致します。 たとえば、テーブルまたはビューが参照されている場合、2 つの部分名を使用して*exposed_object_name*同じ 2 つの部分から成る名前を指定します。  
  
 ときに*exposed_object_name*がオブジェクトのテーブル ヒントの一部は無視され、インデックスの使用状況は、クエリ オプティマイザーによって決定されます、クエリで指定されたインデックスのテーブル ヒントを指定せずに指定されています。 この手法を使用すると、元のクエリに変更を加えることができない場合に INDEX テーブル ヒントの効果を除去できます。 例 J を参照してください。  
  
**\<table_hint >:: =** {[NOEXPAND] {インデックス ( *index_value* [,...*n* ] ) |インデックス = ( *index_value* ) |FORCESEEK [**(***index_value***(***index_column_name* [**、**...]**))** ]|FORCESCAN |HOLDLOCK |NOLOCK |NOWAIT |PAGLOCK |READCOMMITTED |READCOMMITTEDLOCK |READPAST |READUNCOMMITTED |REPEATABLEREAD |ROWLOCK |シリアル化可能な |スナップショット |SPATIAL_WINDOW_MAX_CELLS |TABLOCK |TABLOCKX |UPDLOCK |XLOCK} は、適用するテーブル ヒントをテーブルまたはビューに対応する*exposed_object_name*クエリ ヒントとして。 これらのヒントについては、次を参照してください。[テーブル ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
 INDEX、FORCESCAN、および FORCESEEK 以外のテーブル ヒントは、クエリで既に WITH 句を使用してテーブル ヒントが指定されていない限り、クエリ ヒントとして使用できません。 詳細については、「解説」を参照してください。  
  
> [!CAUTION] 
> パラメーターを使用して FORCESEEK を指定すると、オプティマイザーで考慮できるプラン数の制限は、パラメーターなしで FORCESEEK を指定した場合よりも多くなります。 これにより、"プランを生成できない" というエラーが生じる回数が増加する可能性があります。 将来のリリースでは、オプティマイザーに対して内部変更を行うため、より多くのプランを考慮できるようになります。  
  
## <a name="remarks"></a>解説  
 ステートメント内部で SELECT 句が使用されている場合を除き、クエリ ヒントは INSERT ステートメントでは指定できません。  
  
 クエリ ヒントはサブクエリではなく、最上位レベルのクエリでのみ指定できます。 最上位のクエリまたはサブクエリ; でヒントを指定できますテーブル ヒントをクエリ ヒントとして指定すると、ただし、指定した値*exposed_object_name*句、テーブル ヒントに、クエリまたはサブクエリで正確に公開されている名前に一致する必要があります。  
  
## <a name="specifying-table-hints-as-query-hints"></a>クエリ ヒントとしてのテーブル ヒントの指定  
 コンテキストのみでのクエリ ヒントとしての INDEX、FORCESCAN、または FORCESEEK テーブル ヒントの使用をお勧め、[プラン ガイド](../../relational-databases/performance/plan-guides.md)です。 プラン ガイドは、たとえばクエリがサードパーティ アプリケーションである場合のように、元のクエリに変更を加えることができない場合に便利です。 プラン ガイドに指定されたクエリ ヒントは、コンパイルおよび最適化される前にクエリに追加されます。 アドホック クエリの場合は、プラン ガイド ステートメントをテストするときだけ TABLE HINT 句を使用します。 その他のアドホック クエリに対しては、テーブル ヒント内でのみこれらのヒントを指定することをお勧めします。  
  
 クエリ ヒントとして指定した場合、INDEX、FORCESCAN、および FORCESEEK テーブル ヒントは次のオブジェクトに対して有効です。  
  
-   テーブル  
  
-   ビュー  
  
-   インデックス付きビュー  
  
-   共通テーブル式 (ヒントは、結果セットが共通テーブル式に入力される SELECT ステートメントに指定する必要があります)  
  
-   動的管理ビュー  
  
-   名前付きサブクエリ  
  
 INDEX、FORCESCAN、および FORCESEEK テーブル ヒントは、既存のテーブル ヒントを持たないクエリのクエリ ヒントとして指定できます。また、それぞれ、クエリ内の既存の INDEX、FORCESCAN、または FORCESEEK ヒントの代わりに使用することもできます。 INDEX、FORCESCAN、および FORCESEEK 以外のテーブル ヒントは、クエリで既に WITH 句を使用してテーブル ヒントが指定されていない限り、クエリ ヒントとして使用できません。 この場合に、そのクエリのセマンティックを維持するには、OPTION 句で TABLE HINT を使用して、対応するヒントもクエリ ヒントとして指定する必要があります。 たとえば、クエリにテーブル ヒント NOLOCK がの OPTION 句が含まれている場合、  **@hints** プラン ガイドのパラメーターでは、NOLOCK ヒントを含める必要がありますもします。 K. の例を参照してください。せず、対応するクエリ ヒントでは、OPTION 句で TABLE HINT を使用して、INDEX、FORCESCAN、または FORCESEEK 以外のテーブル ヒントが指定されている場合またはその逆の場合(OPTION 句を変更するクエリのセマンティックになることを示す) にエラー 8702 が発生し、クエリが失敗します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-merge-join"></a>A. MERGE JOIN を使用する  
 次の例では、クエリの結合操作がマージ結合によって実行されていることを指定します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
SELECT *   
FROM Sales.Customer AS c  
INNER JOIN Sales.CustomerAddress AS ca ON c.CustomerID = ca.CustomerID  
WHERE TerritoryID = 5  
OPTION (MERGE JOIN);  
GO    
```  
  
### <a name="b-using-optimize-for"></a>B. OPTIMIZE FOR を使用する  
 次の例の値を使用して、クエリ オプティマイザーに指示`'Seattle'`ローカル変数に対して`@city_name`ローカル変数の値を決定する統計データを使用して`@postal_code`クエリを最適化するときにします。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
 MAXRECURSION を使用すると、不適切に作成された再帰共通テーブル式による無限ループの発生を防ぐことができます。 次の例は意図的に無限ループを作成し、2 つの再帰レベルの数を制限する、MAXRECURSION ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```tsql  
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
 次の例では、マージ結合クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
SELECT *  
FROM HumanResources.Employee AS e1  
UNION  
SELECT *  
FROM HumanResources.Employee AS e2  
OPTION (MERGE UNION);  
GO  
```  
  
### <a name="e-using-hash-group-and-fast"></a>E. HASH GROUP および FAST を使用する  
 次の例では、HASH GROUP および FAST クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO    
```  
  
### <a name="f-using-maxdop"></a>F. MAXDOP を使用する  
 次の例では、MAXDOP クエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (MAXDOP 2);    
GO
```  
  
### <a name="g-using-index"></a>G. INDEX を使用する  
 次の例では、INDEX ヒントを使用します。 最初の例では、単一のインデックスを指定します。 2 番目の例では、1 つのテーブル参照に対して複数のインデックスを指定します。 INDEX ヒントはどちらの例においても別名が使用されているテーブルに適用されるので、公開されたオブジェクト名と同じ別名を TABLE HINT 句でも指定する必要があります。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
 次の例では、FORCESEEK テーブル ヒントを使用します。 INDEX ヒントは 2 つの部分で構成される名前が使用されているテーブルに適用されるので、公開されたオブジェクト名と同じ 2 つの部分で構成される名前を TABLE HINT 句でも指定する必要があります。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
 次の例では、INDEX ヒントと FORCESEEK ヒントをそれぞれ別のテーブルに適用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
 次の例では、ヒントを指定しないで TABLE HINT ヒントを使用して、クエリの FROM 句に指定されている INDEX テーブル ヒントの動作をオーバーライドする方法を示します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
 次の例では、クエリに 2 つのテーブル ヒントが含まれています。1 つは、セマンティックに作用する NOLOCK で、もう 1 つはセマンティックに作用しない INDEX です。 クエリのセマンティックを保持するために、プラン ガイドの OPTIONS 句に NOLOCK ヒントが指定されています。 NOLOCK ヒントに加えて、INDEX および FORCESEEK ヒントが指定されているので、ステートメントをコンパイルおよび最適化するときにクエリのセマンティックに作用しない INDEX ヒントが置き換えられます。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
  
 次の例では、クエリのセマンティックを保持し、テーブル ヒントに指定されている以外のインデックスをオプティマイザーが選択できるようにする別の方法を示します。 これを実現するには、OPTIONS 句に (セマンティックに作用する) NOLOCK ヒントを指定する一方で、INDEX ヒントを持たないテーブル参照だけの TABLE HINT キーワードを指定します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
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
### <a name="l-using-use-hint"></a>L. 使用してヒントを使用します。  
 次の例では、再コンパイルしてヒントを使用するクエリ ヒントを使用します。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。  
  
```  
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (RECOMPILE, USE HINT ('ASSUME_MIN_SELECTIVITY_FOR_FILTER_ESTIMATES', 'DISABLE_PARAMETER_SNIFFING')); 
GO  
```  
    
## <a name="see-also"></a>参照  
 [ヒント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_control_plan_guide & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
 [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  

