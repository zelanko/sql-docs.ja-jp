---
title: "予約済みキーワード (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ODBC function calls
- keywords [SQL Server], reserved
- reserved words [SQL Server]
- keywords [SQL Server]
ms.assetid: ed8b3e27-6796-40f0-aef3-0cac5e0e2418
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: efaa21099f422ae812168561351a359fc89f8e0d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="reserved-keywords-transact-sql"></a>予約済みキーワードの TRANSACT-SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データベースの定義、操作、アクセスに予約済みキーワードが使用されます。 予約済みキーワードの文法の一部である、[!INCLUDE[tsql](../../includes/tsql-md.md)]によって使用される言語[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を解析し、理解[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントとバッチです。 構文的に使用することはできますが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子とオブジェクト名の予約済みキーワード[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプト、これを行うを区切られた識別子を使用します。  
  
 次の表にリスト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]予約済みキーワード。  
  
||||  
|-|-|-|  
|ADD|EXTERNAL|PROCEDURE|  
|ALL|FETCH|PUBLIC|  
|ALTER|FILE|RAISERROR|  
|[AND]|FILLFACTOR|READ|  
|ANY|FOR|READTEXT|  
|AS|FOREIGN|RECONFIGURE|  
|ASC|FREETEXT|REFERENCES|  
|AUTHORIZATION|FREETEXTTABLE|レプリケーション|  
|BACKUP|FROM|RESTORE|  
|BEGIN|FULL|RESTRICT|  
|BETWEEN|FUNCTION|RETURN|  
|BREAK|GOTO|REVERT|  
|BROWSE|GRANT|REVOKE|  
|BULK|GROUP|[RIGHT]|  
|BY|HAVING|ROLLBACK|  
|CASCADE|HOLDLOCK|ROWCOUNT|  
|CASE|IDENTITY|ROWGUIDCOL|  
|CHECK|IDENTITY_INSERT|RULE|  
|CHECKPOINT|IDENTITYCOL|SAVE|  
|CLOSE|[IF]|SCHEMA|  
|CLUSTERED|IN|SECURITYAUDIT|  
|COALESCE|INDEX|SELECT|  
|COLLATE|INNER|SEMANTICKEYPHRASETABLE|  
|COLUMN|INSERT|SEMANTICSIMILARITYDETAILSTABLE|  
|COMMIT|INTERSECT|SEMANTICSIMILARITYTABLE|  
|COMPUTE|INTO|SESSION_USER|  
|CONSTRAINT|IS|SET|  
|CONTAINS|JOIN|SETUSER|  
|CONTAINSTABLE|KEY|SHUTDOWN|  
|CONTINUE|KILL|SOME|  
|CONVERT|[LEFT]|STATISTICS|  
|CREATE|LIKE|SYSTEM_USER|  
|CROSS|LINENO|TABLE|  
|CURRENT|LOAD|TABLESAMPLE|  
|CURRENT_DATE|MERGE|TEXTSIZE|  
|CURRENT_TIME|NATIONAL|THEN|  
|CURRENT_TIMESTAMP|NOCHECK|TO|  
|CURRENT_USER|NONCLUSTERED|先頭に戻る|  
|CURSOR|[NOT]|TRAN|  
|DATABASE|NULL|TRANSACTION|  
|DBCC|NULLIF|TRIGGER|  
|DEALLOCATE|OF|TRUNCATE|  
|DECLARE|OFF|TRY_CONVERT|  
|DEFAULT|OFFSETS|TSEQUAL|  
|DELETE|ON|UNION|  
|DENY|OPEN|UNIQUE|  
|DESC|OPENDATASOURCE|UNPIVOT|  
|DISK|OPENQUERY|UPDATE|  
|DISTINCT|OPENROWSET|UPDATETEXT|  
|DISTRIBUTED|OPENXML|USE|  
|DOUBLE|OPTION|USER|  
|DROP|または|VALUES|  
|DUMP|ORDER|VARYING|  
|ELSE|OUTER|VIEW|  
|END|OVER|WAITFOR|  
|ERRLVL|PERCENT|WHEN|  
|ESCAPE|PIVOT|WHERE|  
|EXCEPT|PLAN|WHILE|  
|EXEC|PRECISION|のすべてのメンションを|  
|CREATE ステートメントを実行する前に、|PRIMARY|WITHIN GROUP|  
|EXISTS|PRINT|WRITETEXT|  
|EXIT|PROC||  
  
 これに加えて、ISO 標準では予約済みキーワードの一覧が定義されています。 オブジェクト名と識別子には、ISO の予約済みキーワードを使用しないでください。 次の表にある ODBC の予約済みキーワードの一覧は、ISO の予約済みキーワードの一覧と同じです。  
  
> [!NOTE]  
>  ISO 標準の予約済みキーワードの一覧に記載されているキーワードを使用するとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よりも制限が厳しい場合もあれば、制限が緩やかな場合もあります。 たとえば、ISO 予約済みキーワードの一覧が含まれている**INT**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこれを予約済みキーワードとして区別する必要はありません。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] の予約済みキーワードは、データベースやテーブル、列、ビューなどのデータベース オブジェクトの識別子や名前として使用できます。 識別子は引用符で囲むか区切り文字で区切って使用してください。 変数やストアド プロシージャ パラメーターの名前として予約済みキーワードを使用する場合は、制限はありません。  
  
## <a name="odbc-reserved-keywords"></a>ODBC の予約済みキーワード  
 次の文字列は、ODBC 関数呼び出し用に予約されています。 この文字列によって SQL の文法が制限されることは一切ありませんが、主要な SQL 文法をサポートするドライバーとの互換性を維持するため、アプリケーションではこのキーワードを使用しないでください。  
  
 次に、現在の ODBC の予約済みキーワードの一覧を示します。  
  
||||  
|-|-|-|  
|**絶対**|**EXEC**|**重複しています**|  
|**アクション**|**EXECUTE**|**パッド**|  
|**ADA**|**存在します。**|**部分的です**|  
|**追加**|**EXTERNAL**|**PASCAL**|  
|**ALL**|**抽出**|**位置**|  
|**割り当てる**|**FALSE**|**有効桁数**|  
|**ALTER**|**フェッチ**|**準備します。**|  
|**AND**|**まずは**|**保持します。**|  
|**任意**|**浮動小数点数**|**PRIMARY**|  
|**します。**|**の**|**前に**|  
|**AS**|**外部**|**特権**|  
|**ASC**|**FORTRAN**|**プロシージャ**|  
|**アサーション**|**見つかりません**|**パブリック**|  
|**AT**|**FROM**|**読み取り**|  
|**承認**|**FULL**|**本当の**|  
|**AVG**|**取得**|**参照**|  
|**BEGIN**|**グローバル**|**相対**|  
|**BETWEEN**|**移動します。**|**制限します。**|  
|**ビット**|**GOTO**|**REVOKE**|  
|**BIT_LENGTH**|**GRANT**|**RIGHT**|  
|**両方とも**|**グループ**|**ロールバック**|  
|**によって**|**持つ**|**行**|  
|**CASCADE**|**1 時間**|**スキーマ**|  
|**カスケード**|**ID**|**スクロール**|  
|**場合**|**イミディ エイト**|**1 秒**|  
|**キャスト**|**IN**|**セクション**|  
|**カタログ**|**含まれます**|**SELECT**|  
|**CHAR 型**|**インデックス**|**セッション**|  
|**CHAR_LENGTH**|**インジケーター**|**SESSION_USER**|  
|**文字**|**最初に**|**設定**|  
|**CHARACTER_LENGTH**|**内部**|**サイズ**|  
|**チェック**|**入力**|**SMALLINT**|  
|**閉じる**|**小文字を区別しません。**|**いくつか**|  
|**結合**|**INSERT**|**領域**|  
|**部単位印刷します。**|**INT**|**SQL**|  
|**照合順序**|**整数**|**SQLCA**|  
|**列**|**INTERSECT**|**SQLCODE**|  
|**コミット**|**間隔**|**SQLERROR**|  
|**接続**|**に**|**SQLSTATE**|  
|**接続**|**IS**|**行いません**|  
|**制約**|**分離**|**SUBSTRING**|  
|**制約**|**結合**|**合計**|  
|**続行**|**キー**|**SYSTEM_USER**|  
|**変換**|**LANGUAGE**|**テーブル**|  
|**対応します。**|**前の**|**一時**|  
|**カウント**|**先行します。**|**そうしたら**|  
|**作成します。**|**LEFT**|**時間**|  
|**クロス**|**レベル**|**タイムスタンプ**|  
|**現在の**|**LIKE**|**TIMEZONE_HOUR**|  
|**CURRENT_DATE**|**地元の**|**TIMEZONE_MINUTE**|  
|**CURRENT_TIME**|**低い**|**宛先**|  
|**CURRENT_TIMESTAMP**|**MATCH**|**末尾**|  
|**CURRENT_USER**|**最大値**|**トランザクション**|  
|**カーソル**|**最小値**|**翻訳**|  
|**日付**|**1 分**|**翻訳**|  
|**1 日**|**モジュール**|**TRIM**|  
|**割り当てを解除します。**|**月**|**場合は TRUE。**|  
|**年 12 月**|**名**|**共用体**|  
|**10 進数**|**各国語**|**一意**|  
|**宣言**|**自然です**|**不明**|  
|**既定値**|**NCHAR**|**UPDATE**|  
|**遅延**|**次に**|**上限**|  
|**遅延**|**違います**|**使用状況**|  
|**DELETE**|**NONE**|**ユーザー**|  
|**DESC**|**NOT**|**使用します。**|  
|**説明**|**NULL**|**VALUE**|  
|**記述子**|**NULLIF**|**値**|  
|**診断**|**数値**|**VARCHAR**|  
|**切断**|**OCTET_LENGTH**|**さまざまな**|  
|**DISTINCT**|**の**|**ビュー**|  
|**ドメイン**|**ON**|**いつ**|  
|**DOUBLE**|**のみ**|**ときに**|  
|**ドロップ**|**開いています。**|**WHERE**|  
|**その他**|**オプション**|**と**|  
|**END**|**OR**|**作業**|  
|**終了 EXEC**|**順序**|**書き込み**|  
|**エスケープ**|**外部**|**1 年**|  
|**点を除いて**|**出力**|**ゾーン**|  
|**例外**|||  
  
## <a name="future-keywords"></a>将来のキーワード  
 次に示すキーワードは、将来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリリースで新しい機能が実装されたときに予約される可能性があります。 これらの語はできるだけ識別子として使用しないでください。  
  
||||  
|-|-|-|  
|ABSOLUTE|HOST|RELATIVE|  
|ACTION|[HOUR]|RELEASE|  
|ADMIN|IGNORE|RESULT|  
|AFTER|IMMEDIATE|RETURNS|  
|AGGREGATE|INDICATOR|ROLE|  
|ALIAS|INITIALIZE|ROLLUP|  
|ALLOCATE|INITIALLY|ROUTINE|  
|ARE|INOUT|ROW|  
|ARRAY|INPUT|ROWS|  
|ASENSITIVE|INT|SAVEPOINT|  
|ASSERTION|INTEGER|SCROLL|  
|ASYMMETRIC|INTERSECTION|SCOPE|  
|AT|INTERVAL|SEARCH|  
|ATOMIC|ISOLATION|[SECOND]|  
|BEFORE|ITERATE|SECTION|  
|BINARY|LANGUAGE|SENSITIVE|  
|BIT|LARGE|SEQUENCE|  
|BLOB|LAST|SESSION|  
|BOOLEAN|LATERAL|SETS|  
|BOTH|LEADING|SIMILAR|  
|BREADTH|LESS|SIZE|  
|CALL|LEVEL|SMALLINT|  
|CALLED|LIKE_REGEX|Space|  
|CARDINALITY|LIMIT|SPECIFIC|  
|CASCADED|LN|SPECIFICTYPE|  
|CAST|LOCAL|SQL|  
|CATALOG|LOCALTIME|SQLEXCEPTION|  
|CHAR|LOCALTIMESTAMP|SQLSTATE|  
|CHARACTER|LOCATOR|SQLWARNING|  
|CLASS|MAP|START|  
|CLOB|MATCH|STATE|  
|COLLATION|MEMBER|STATEMENT|  
|COLLECT|METHOD|STATIC|  
|COMPLETION|[MINUTE]|STDDEV_POP|  
|CONDITION|[MOD]|STDDEV_SAMP|  
|CONNECT|MODIFIES|STRUCTURE|  
|CONNECTION|MODIFY|SUBMULTISET|  
|CONSTRAINTS|MODULE|SUBSTRING_REGEX|  
|CONSTRUCTOR|[MONTH]|SYMMETRIC|  
|CORR|MULTISET|SYSTEM|  
|CORRESPONDING|NAMES|TEMPORARY|  
|COVAR_POP|NATURAL|TERMINATE|  
|COVAR_SAMP|NCHAR|THAN|  
|CUBE|NCLOB|TIME|  
|CUME_DIST|NEW|timestamp|  
|CURRENT_CATALOG|NEXT|TIMEZONE_HOUR|  
|CURRENT_DEFAULT_TRANSFORM_GROUP|いいえ|TIMEZONE_MINUTE|  
|CURRENT_PATH|なし|TRAILING|  
|CURRENT_ROLE|NORMALIZE|TRANSLATE_REGEX|  
|CURRENT_SCHEMA|NUMERIC|TRANSLATION|  
|CURRENT_TRANSFORM_GROUP_FOR_TYPE|OBJECT|TREAT|  
|CYCLE|OCCURRENCES_REGEX|TRUE|  
|DATA|OLD|UESCAPE|  
|[DATE]|ONLY|UNDER|  
|[DAY]|OPERATION|UNKNOWN|  
|DEC|ORDINALITY|UNNEST|  
|[DECIMAL]|OUT|USAGE|  
|DEFERRABLE|OVERLAY|USING|  
|DEFERRED|OUTPUT|Value|  
|DEPTH|PAD|VAR_POP|  
|DEREF|パラメーター|VAR_SAMP|  
|DESCRIBE|PARAMETERS|VARCHAR|  
|DESCRIPTOR|PARTIAL|VARIABLE|  
|DESTROY|PARTITION|WHENEVER|  
|DESTRUCTOR|PATH|WIDTH_BUCKET|  
|DETERMINISTIC|POSTFIX|WITHOUT|  
|DICTIONARY|PREFIX|WINDOW|  
|DIAGNOSTICS|PREORDER|WITHIN|  
|DISCONNECT|PREPARE|WORK|  
|DOMAIN|PERCENT_RANK|WRITE|  
|DYNAMIC|PERCENTILE_CONT|XMLAGG|  
|EACH|PERCENTILE_DISC|XMLATTRIBUTES|  
|ELEMENT|POSITION_REGEX|XMLBINARY|  
|END-EXEC|PRESERVE|XMLCAST|  
|EQUALS|PRIOR|XMLCOMMENT|  
|EVERY|PRIVILEGES|XMLCONCAT|  
|EXCEPTION|RANGE|XMLDOCUMENT|  
|FALSE|READS|XMLELEMENT|  
|FILTER|REAL|XMLEXISTS|  
|FIRST|RECURSIVE|XMLFOREST|  
|[FLOAT]|REF|XMLITERATE|  
|FOUND|REFERENCING|XMLNAMESPACES|  
|FREE|REGR_AVGX|XMLPARSE|  
|FULLTEXTTABLE|REGR_AVGY|XMLPI|  
|FUSION|REGR_COUNT|XMLQUERY|  
|GENERAL|REGR_INTERCEPT|XMLSERIALIZE|  
|GET|REGR_R2|XMLTABLE|  
|GLOBAL|REGR_SLOPE|XMLTEXT|  
|GO|REGR_SXX|XMLVALIDATE|  
|GROUPING|REGR_SXY|[YEAR]|  
|HOLD|REGR_SYY|ZONE|  
  
## <a name="see-also"></a>参照  
 [SET QUOTED_IDENTIFIER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [ALTER DATABASE 互換性レベル &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

