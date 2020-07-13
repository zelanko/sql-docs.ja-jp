---
title: ネイティブコンパイルストアドプロシージャでサポートされるコンストラクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: rothja
ms.author: jroth
ms.openlocfilehash: 65e6e794c5858a68c4b2a9b298513911b487cf52
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025730"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a>ネイティブ コンパイル ストアド プロシージャ内でサポートされる構造
  このトピックには、ネイティブコンパイルストアドプロシージャでサポートされている機能の一覧が含まれています ([CREATE PROCEDURE &#40;transact-sql&#41;](/sql/t-sql/statements/create-procedure-transact-sql))。  
  
-   [ネイティブ コンパイル ストアド プロシージャでのプログラミング機能](#pncsp)  
  
-   [サポートされる演算子](#so)  
  
-   [ネイティブ コンパイル ストアド プロシージャでの組み込み関数](#bfncsp)  
  
-   [ネイティブ コンパイル ストアド プロシージャでのクエリ対象領域](#qsancsp)  
  
-   [監査](#auditing)  
  
-   [テーブル ヒント、クエリ ヒント、および結合ヒント](#tqh)  
  
-   [並べ替えに関する制限事項](#los)  
  
 ネイティブ コンパイル ストアド プロシージャでサポートされるデータ型については、「 [Supported Data Types](supported-data-types-for-in-memory-oltp.md)」を参照してください。  
  
 サポートされない構造に関する詳細と、ネイティブ コンパイル ストアド プロシージャのサポートされない一部の機能に対処する方法については、「 [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md)」を参照してください。 サポートされていない機能の詳細については、「 [インメモリ OLTP でサポートされていない Transact-SQL の構造](transact-sql-constructs-not-supported-by-in-memory-oltp.md)」をご覧ください。  
  
##  <a name="programmability-in-natively-compiled-stored-procedures"></a><a name="pncsp"></a>ネイティブコンパイルストアドプロシージャでのプログラミング  
 サポート対象は次のとおりです。  
  
-   BEGIN ATOMIC (ストアド プロシージャの外部レベル)、LANGUAGE、ISOLATION LEVEL、DATEFORMAT、および DATEFIRST。  
  
-   NULL または NOT NULL としての変数の宣言。 変数が NOT NULL として宣言されている場合、宣言には初期化子が必要です。 変数が NOT NULL として宣言されていない場合、初期化子は省略可能です。  
  
-   IF と WHILE  
  
-   INSERT/UPDATE/DELETE  
  
     サブクエリはサポートされていません。 WHERE または HAVING 句では、AND および BETWEEN がサポートされています。OR、NOT、および IN はサポートされていません。  
  
-   メモリ最適化テーブル型とテーブル変数。  
  
-   RETURN  
  
-   SELECT  
  
-   SET  
  
-   TRY/CATCH/THROW  
  
     パフォーマンスを最適化するには、ネイティブ コンパイル ストアド プロシージャ全体に対して 1 つの TRY/CATCH ブロックを使用します。  
  
##  <a name="supported-operators"></a><a name="so"></a>サポートされる演算子  
 サポートされている演算子は次のとおりです。  
  
-   [Transact-sql&#41;&#40;の比較演算子](/sql/t-sql/language-elements/comparison-operators-transact-sql)(たとえば、>、 \<, > =、および <=) は、条件 (IF、WHILE) でサポートされています。  
  
-   単項演算子 (+、-)。  
  
-   二項演算子 (*、/、+、-、% (剰余))。  
  
     プラス演算子 (+) は、数値と文字列の両方でサポートされています。  
  
-   論理演算子 (AND、OR、NOT)。 OR および NOT は、IF および WHILE ステートメントではサポートされていますが、WHERE または HAVING 句ではサポートされていません。  
  
-   ビット演算子 ~、&、|、および ^  
  
##  <a name="built-in-functions-in-natively-compiled-stored-procedures"></a><a name="bfncsp"></a>ネイティブコンパイルストアドプロシージャの組み込み関数  
 メモリ最適化テーブルの既定構造とネイティブ コンパイル ストアド プロシージャでは、次の関数がサポートされます。  
  
-   数学関数: ACOS、ASIN、ATAN、ATN2、COS、COT、DEGREES、EXP、LOG、LOG10、PI、POWER、RADIANS、RAND、SIN、SQRT、SQUARE、および TAN  
  
-   日付関数: CURRENT_TIMESTAMP、DATEADD、DATEDIFF、DATEFROMPARTS、DATEPART、DATETIME2FROMPARTS、DATETIMEFROMPARTS、DAY、EOMONTH、GETDATE、GETUTCDATE、MONTH、SMALLDATETIMEFROMPARTS、SYSDATETIME、SYSUTCDATETIME、および YEAR  
  
-   文字列関数: LEN、LTRIM、RTRIM、および SUBSTRING  
  
-   ID 関数: SCOPE_IDENTITY  
  
-   NULL 関数: ISNULL  
  
-   Uniqueidentifier 関数: NEWID および NEWSEQUENTIALID  
  
-   エラー関数: ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY、および ERROR_STATE  
  
-   変換: CAST および CONVERT。 Unicode 文字と非 Unicode 文字の文字列 (n(var)char および (var)char) の間の変換はサポートされません。  
  
-   システム関数: @@rowcount。 ネイティブ コンパイル ストアド プロシージャ内のステートメントによって、@@rowcount が更新されます。ネイティブ コンパイル ストアド プロシージャ内で @@rowcount を使用し、ネイティブ コンパイル ストアド プロシージャ内で実行された最後のステートメントによる影響を受けた行の数を決定することができます。 ただし、ネイティブ コンパイル ストアド プロシージャの実行の開始時および終了時に、@@rowcount は 0 にリセットされます。  
  
##  <a name="query-surface-area-in-natively-compiled-stored-procedures"></a><a name="qsancsp"></a>ネイティブコンパイルストアドプロシージャのクエリ領域  
 サポート対象は次のとおりです。  
  
-   BETWEEN  
  
-   列名のエイリアス (AS または = 構文を使用)。  
  
-   CROSS JOIN と INNER JOIN は、SELECT クエリでのみサポート。  
  
-   SELECT リストでは式がサポートされていますが、サポートされている演算子を使用する場合は、 [transact-sql&#41;句 &#40;](/sql/t-sql/queries/where-transact-sql)ます。 現在サポートされている演算子の一覧については、「 [Supported Operators](#so) 」を参照してください。  
  
-   フィルター述語 IS [NOT] NULL  
  
-   FROM \<memory optimized table>  
  
-   [GROUP BY &#40;transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql)は、集計関数の AVG、COUNT、COUNT_BIG、MIN、MAX、および SUM と共にサポートされています。 MIN および MAX は、nvarchar、char、varchar、varchar、varbinary、および binary 型ではサポートされていません。 Order by[句 &#40;transact-sql&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)は group by &#40;でサポートされています。 order by リスト内の式が group by リストにそのまま表示される場合は、 [transact-sql&#41;](/sql/t-sql/queries/select-group-by-transact-sql)を使用します。 たとえば、GROUP BY a + b ORDER BY a + b はサポートされますが、GROUP BY a, b ORDER BY a + b はサポートされません。  
  
-   HAVING (WHERE 句と同じ式の制限が適用されます)。  
  
-   INSERT VALUES (ステートメントごとに 1 行) と INSERT SELECT  
  
-   ORDER BY <sup>1</sup>  
  
-   列を参照しない述語。  
  
-   SELECT、UPDATE、および DELETE  
  
-   上位<sup>1</sup>  
  
-   SELECT リストでの変数代入。  
  
-   どこ。。。そして  
  
 <sup>1</sup> ORDER BY と TOP はネイティブコンパイルストアドプロシージャでサポートされていますが、いくつかの制限があります。  
  
-   `DISTINCT` 句または `SELECT` 句での `ORDER BY` のサポートはありません。  
  
-   `WITH TIES` 句での `PERCENT` または `TOP` のサポートはありません。  
  
-   `TOP` と `ORDER BY` の組み合わせでは、`TOP` 句内で定数を使用するときに 8,192 を超える値はサポートされません。 クエリに結合または集計関数が含まれている場合は、この制限値がさらに小さくなる場合があります (たとえば、1 回の結合 (2 つのテーブル) では、制限値は 4,096 行です。 2 回の結合 (3 つのテーブル) では、制限値は 2,730 行です)。  
  
     変数内に行の数を格納すると、8,192 より多くの結果を取得できます。  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 ただし、変数を使用する場合に比べて、`TOP` 句内で定数を使用する方がパフォーマンスが向上する結果になります。  
  
 これらの制限は、インタープリターによって処理される [!INCLUDE[tsql](../../includes/tsql-md.md)] によるメモリ最適化テーブルへのアクセスには適用されません。  
  
##  <a name="auditing"></a><a name="auditing"></a>監査  
 プロシージャ レベルの監査はネイティブ コンパイル ストアド プロシージャでサポートされています。 ステートメント レベルの監査はサポートされていません。  
  
 監査の詳細については、「 [Create a Server Audit and Database Audit Specification](../security/auditing/create-a-server-audit-and-database-audit-specification.md)」を参照してください。  
  
##  <a name="table-query-and-join-hints"></a><a name="tqh"></a>テーブル、クエリ、および結合ヒント  
 サポート対象は次のとおりです。  
  
-   テーブル ヒント構文またはクエリの [OPTION 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/option-clause-transact-sql) での INDEX、FORCESCAN、および FORCESEEK ヒント。  
  
-   FORCE ORDER  
  
-   INNER LOOP JOIN  
  
-   OPTIMIZE FOR  
  
 詳細については、「 [transact-sql&#41;&#40;ヒント](/sql/t-sql/queries/hints-transact-sql)」を参照してください。  
  
##  <a name="limitations-on-sorting"></a><a name="los"></a> 並べ替えに関する制限事項  
 [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) および [ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用するクエリでは、8,000 を超える行の並べ替えを行うことができます。 ただし、[ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用しない場合、[TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) で並べ替えができる行数は最大で 8,000 です (結合がある場合は、より少ない行数になります)。  
  
 クエリが [TOP &#40;Transact-SQL&#41;](/sql/t-sql/queries/top-transact-sql) 演算子および [ORDER BY 句 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql) を使用する場合、TOP 演算子には 8192 行まで指定できます。 8192行を超える行を指定した場合、次のエラーメッセージが表示されます: メッセージ**41398、レベル16、状態1、プロシージャ *\<procedureName>* 、行 *\<lineNumber>* TOP 演算子は、最大で8192行を返すことができます。は要求され *\<number>* ました。**  
  
 TOP 句がない場合は、ORDER BY で任意の数の行を並べ替えることができます。  
  
 ORDER BY 句を使用しない場合、TOP 演算子と共に任意の整数値を使用できます。  
  
 TOP N = 8192 の例: コンパイル  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 TOP N > 8192 の例: コンパイルは失敗します。  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 8192 行の制限は、 `TOP N` が定数の場合に、前の例のように、 `N` にのみ適用されます。  8192 より大きな `N` が必要である場合は、値を変数に割り当て、 `TOP`と共にその変数を使用することができます。  
  
 変数を使用した例: コンパイル  
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 **返される行に関する制限事項:** TOP 演算子から返される行数を減らせる可能性がある場合が 2 つあります。  
  
-   クエリで JOIN を使用します。  制限における JOIN の影響は、クエリ プランによって異なります。  
  
-   ORDER BY 句で集計関数または集計関数への参照を使用する。  
  
 TOP N での最悪のケースでサポートされる最大 N を計算する式は次のとおりです: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`。  
  
## <a name="see-also"></a>参照  
 [ネイティブコンパイルストアドプロシージャ](natively-compiled-stored-procedures.md)   
 [ネイティブ コンパイル ストアド プロシージャの移行に関する問題](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
