---
title: "日付および時刻データ型および関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/01/2017
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
- dates [SQL Server], functions
- dates [SQL Server]
- date and time [SQL Server], all data types and functions
- date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 83e378a2-6e89-4c80-bc4f-644958d9e0a9
caps.latest.revision: 79
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 60272ce672c0a32738b0084ea86f8907ec7fc0a5
ms.openlocfilehash: 7ce3baac7ec87ff3cad771234ab1196fb0a3855e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="date-and-time-data-types-and-functions-transact-sql"></a>日付と時刻のデータ型および関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

このトピックの以下のセクションでは、日付と時刻に関連して [!INCLUDE[tsql](../../includes/tsql-md.md)] が備えているすべてのデータ型および関数について概要を紹介します。
-   [日付と時刻のデータ型](#DateandTimeDataTypes)  
-   [日付と時刻関数](#DateandTimeFunctions)  
    -   [値をする Get のシステム日付と時刻関数](#GetSystemDateandTimeValues)  
    -   [日付を取得する関数と時刻の要素](#GetDateandTimeParts)  
    -   [要素から日付と時刻の値を取得する関数](#fromParts)  
    -   [日付を取得する関数や時刻の差](#GetDateandTimeDifference)  
    -   [日付を変更する関数と時刻の値](#ModifyDateandTimeValues)  
    -   [設定またはセッションの形式の関数を取得する関数](#SetorGetSessionFormatFunctions)  
    -   [日付を検証する関数と時刻の値](#ValidateDateandTimeValues)  
-   [日付と時刻 – 関連トピック](#DateandTimeRelatedTopics)  
  
##  <a name="DateandTimeDataTypes"></a>日付と時刻のデータ型
[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型は、次の表に一覧表示されます。
  
|データ型|Format|範囲|精度|記憶域のサイズ (バイト単位)|ユーザー定義の 1 秒未満の秒の有効桁数|タイム ゾーン オフセット|  
|---|---|---|---|---|---|---|
|[time](../../t-sql/data-types/time-transact-sql.md)|hh:mm:ss[.nnnnnnn]|00:00:00.0000000 ～ 23:59:59.9999999|100 ナノ秒|3 ～ 5|はい|不可|  
|[date](../../t-sql/data-types/date-transact-sql.md)|-YYYY-MM-DD|0001-01-01 ～ 31.12.99|1 日|3|不可|不可|  
|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|YYYY-MM-DD hh:mm:ss|1900-01-01 ～ 2079-06-06|1 分|4|不可|不可|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|YYYY-MM-DD hh:mm:ss[.nnn]|1753-01-01 ～ 9999-12-31|0.00333 秒|8|不可|不可|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|YYYY-MM-DD hh:mm:ss[.nnnnnnn]|0001-01-01 00:00:00.0000000 ～ 9999-12-31 23:59:59.9999999|100 ナノ秒|6 ～ 8|はい|不可|  
|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|YYYY-MM-DD hh:mm:ss [.nnnnnnn] [+ &#124;-] hh:mm|0001-01-01 00:00:00.0000000 ～ 9999-12-31 23:59:59.9999999 (UTC)|100 ナノ秒|8 ～ 10|はい|はい|  
  
> [!NOTE]  
>  [!INCLUDE[tsql](../../includes/tsql-md.md)] [Rowversion](../../t-sql/data-types/rowversion-transact-sql.md)データ型は日付または時刻のデータ型ではありません。 **タイムスタンプ**の非推奨シノニムは、 **rowversion**です。  
  
##  <a name="DateandTimeFunctions"></a>日付と時刻関数  
[!INCLUDE[tsql](../../includes/tsql-md.md)] の日付と時刻の関数を次の表に示します。 決定性の詳細については、次を参照してください。[決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)です。
  
###  <a name="GetSystemDateandTimeValues"></a>システム日付と時刻の値を取得する関数 
コンピューターのオペレーティング システムから派生したすべてのシステム日付と時刻の値は、インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。
  
#### <a name="higher-precision-system-date-and-time-functions"></a>高精度のシステム日付/時刻関数  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]GetSystemTimeAsFileTime() Windows API を使用して日付と時刻の値を取得します。 精度は、コンピューターのハードウェアとする Windows のバージョンによって異なります。 のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 この API の精度は 100 ナノ秒で固定されます。 GetSystemTimeAdjustment() Windows API を使用して、精度を確認できます。
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[SYSDATETIME](../../t-sql/functions/sysdatetime-transact-sql.md)|SYSDATETIME ()|返します、 **datetime2 (7)**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 タイム ゾーン オフセットは含まれません。|**datetime2(7)**|非決定的|  
|[SYSDATETIMEOFFSET](../../t-sql/functions/sysdatetimeoffset-transact-sql.md)|SYSDATETIMEOFFSET ( )|返します、 **datetimeoffset (7)**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 タイム ゾーン オフセットが含まれます。|**datetimeoffset (7)**|非決定的|  
|[SYSUTCDATETIME](../../t-sql/functions/sysutcdatetime-transact-sql.md)|SYSUTCDATETIME ( )|返します、 **datetime2 (7)**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 日付と時刻が UTC 時刻 (世界協定時刻) として返されます。|**datetime2(7)**|非決定的|  
  
#### <a name="lower-precision--system-date-and-time-functions"></a>低精度のシステム日付と時刻関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[CURRENT_TIMESTAMP](../../t-sql/functions/current-timestamp-transact-sql.md)|CURRENT_TIMESTAMP|返します、 **datetime**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 タイム ゾーン オフセットは含まれません。|**datetime**|非決定的|  
|[GETDATE](../../t-sql/functions/getdate-transact-sql.md)|GETDATE ( )|返します、 **datetime**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 タイム ゾーン オフセットは含まれません。|**datetime**|非決定的|  
|[GETUTCDATE](../../t-sql/functions/getutcdate-transact-sql.md)|GETUTCDATE ( )|返します、 **datetime**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 日付と時刻が UTC 時刻 (世界協定時刻) として返されます。|**datetime**|非決定的|  
  
###  <a name="GetDateandTimeParts"></a>日付と時刻の部分を取得する関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|--------------|------------|------------------|----------------------|-----------------|  
|[DATENAME](../../t-sql/functions/datename-transact-sql.md)|DATENAME ( *datepart* 、*日付*)|表す、指定した文字列を返します*datepart*の日付を指定します。|**nvarchar**|非決定的|  
|[DATEPART 関数](../../t-sql/functions/datepart-transact-sql.md)|DATEPART ( *datepart* 、*日付*)|指定されたを表す整数を返します*datepart*の指定した*日付*です。|**int**|非決定的|  
|[1 日](../../t-sql/functions/day-transact-sql.md)|1 日 (*日付*)|指定した日の部分を表す整数を返します*日付*です。|**int**|決定的|  
|[月](../../t-sql/functions/month-transact-sql.md)|月 (*日付*)|指定した月の部分を表す整数を返します*日付*です。|**int**|決定的|  
|[1 年](../../t-sql/functions/year-transact-sql.md)|年 (*日付*)|指定した年の部分を表す整数を返します*日付*です。|**int**|決定的|  
  
###  <a name="fromParts"></a>要素から日付と時刻の値を取得する関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[DATEFROMPARTS](../../t-sql/functions/datefromparts-transact-sql.md)|DATEFROMPARTS (*年*、*月*、*日*)|返します、**日付**指定した年、月、および日の値。|**date**|決定的|  
|[DATETIME2FROMPARTS](../../t-sql/functions/datetime2fromparts-transact-sql.md)|DATETIME2FROMPARTS (*年*、*月*、*日*、*時間*、*分*、 *(秒)*、*分数*、*精度*)|返します、 **datetime2**指定された有効桁数を使用して、指定した日付と時刻の値。|**datetime2 (** *精度* **)**|決定的|  
|[DATETIMEFROMPARTS](../../t-sql/functions/datetimefromparts-transact-sql.md)|DATETIMEFROMPARTS (*年*、*月*、*日*、*時間*、*分*、 *(秒)*、*ミリ秒*)|返します、 **datetime**指定した日付と時刻の値。|**datetime**|決定的|  
|[DATETIMEOFFSETFROMPARTS](../../t-sql/functions/datetimeoffsetfromparts-transact-sql.md)|DATETIMEOFFSETFROMPARTS (*年*、*月*、*日*、*時間*、*分*、 *秒*、*分数*、 *hour_offset*、 *minute_offset*、*精度*)|返します、 **datetimeoffset**指定されたオフセットおよび有効桁数を使用して、指定した日付と時刻の値。|**datetime (** *精度* **)**|決定的|  
|[SMALLDATETIMEFROMPARTS](../../t-sql/functions/smalldatetimefromparts-transact-sql.md)|SMALLDATETIMEFROMPARTS (*年*、*月*、*日*、*時間*、*分*)|返します、 **smalldatetime**指定した日付と時刻の値。|**smalldatetime**|決定的|  
|[TIMEFROMPARTS](../../t-sql/functions/timefromparts-transact-sql.md)|TIMEFROMPARTS (*時間*、*分*、*秒*、*分数*、*精度*)|返します、**時間**指定された有効桁数を使用して、指定した時間の値。|**時間 (** *精度* **)**|決定的|  
  
###  <a name="GetDateandTimeDifference"></a>日付と時刻の差を取得する関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[DATEDIFF 関数](../../t-sql/functions/datediff-transact-sql.md)|DATEDIFF ( *datepart* 、 *startdate* 、 *enddate* )|日付または時刻の数を返します*datepart* 2 つの指定した日付の差の境界。|**int**|決定的|  
|[DATEDIFF_BIG](../../t-sql/functions/datediff-big-transact-sql.md)|DATEDIFF_BIG ( *datepart* 、 *startdate* 、 *enddate* )|日付または時刻の数を返します*datepart* 2 つの指定した日付の差の境界。|**bigint**|決定的|  
  
###  <a name="ModifyDateandTimeValues"></a>日付と時刻の値を変更する関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[DATEADD 関数](../../t-sql/functions/dateadd-transact-sql.md)|DATEADD (*datepart* 、*数*、*日付*)|新しいを返します**datetime**を指定した期間を加えた値*datepart*の指定した*日付*です。|データ型、*日付*引数|決定的|  
|[EOMONTH](../../t-sql/functions/eomonth-transact-sql.md)|EOMONTH ( *start_date* [、 *month_to_add* ])|オプションのオフセットを使用して、指定された日付を含んでいる月の最後の日付を返します。|戻り値の型の型は、 *start_date*または**日付**です。|決定的|  
|[SWITCHOFFSET](../../t-sql/functions/switchoffset-transact-sql.md)|スイッチ*オフセット*(*DATETIMEOFFSET* 、 *time_zone*)|スイッチ*オフセット*DATETIMEOFFSET 値のタイム ゾーン オフセットを変更し、UTC 値を保持します。|**datetimeoffset**の桁数を持つ、 *DATETIMEOFFSET*|決定的|  
|[TODATETIMEOFFSET](../../t-sql/functions/todatetimeoffset-transact-sql.md)|TODATETIMEOFFSET (*式*、 *time_zone*)|TODATETIMEOFFSET は、datetime2 値を datetimeoffset 値に変換します。 datetime2 値は、指定された time_zone のローカル時刻で解釈されます。|**datetimeoffset**の桁数を持つ、 *datetime*引数|決定的|  
  
###  <a name="SetorGetSessionFormatFunctions"></a>取得するか、またはセッションの書式設定関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)|@@DATEFIRST|現在のセッションにおける、SET DATEFIRST の現在の値を返します。|**tinyint**|非決定的|  
|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)|SET DATEFIRST {*数*& #124 です。 **@**  *number_var* }|週の最初の曜日を 1 ～ 7 の数値で設定します。|適用なし|適用なし|  
|[DATEFORMAT の設定](../../t-sql/statements/set-dateformat-transact-sql.md)|SET DATEFORMAT {*形式*& #124 です。 **@**  *format_var* }|入力するため、日付要素 (月/日/年) の順序を設定**datetime**または**smalldatetime**データ。|適用なし|適用なし|  
|[@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)|@@LANGUAGE|現在使用されている言語の名前を返します。 @@LANGUAGE日付または時刻の関数ではありません。 ただし、言語設定は日付関数の出力に影響します。|適用なし|適用なし|  
|[言語を設定します。](../../t-sql/statements/set-language-transact-sql.md)|SET LANGUAGE {[N] **'***言語***'** & #124 です。 **@**  *language_var* }|セッションおよびシステム メッセージの言語環境を設定します。 SET LANGUAGE は日付または時刻の関数ではありません。 ただし、言語設定には、日付関数の出力が影響します。|適用なし|適用なし|  
|[sp_helplanguage](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)|**sp_helplanguage** [  **@language =** ] **'***言語***'** ]|サポートされている言語の日付形式に関する情報を返します。 **sp_helplanguage**日付または時刻ではないストアド プロシージャです。 ただし、言語設定には、日付関数の出力が影響します。|適用なし|適用なし|  
  
###  <a name="ValidateDateandTimeValues"></a>日付と時刻の値を検証する関数
  
|関数|構文|戻り値|戻り値のデータ型|決定性|  
|---|---|---|---|---|
|[ISDATE 関数](../../t-sql/functions/isdate-transact-sql.md)|ISDATE (*式*)|指定するかどうか、 **datetime**または**smalldatetime**入力式が有効な日付または時刻の値。|**int**|ISDATE は、CONVERT 関数と共に使用され、CONVERT スタイル パラメーターが指定されており、スタイルが 0、100、9、または 109 と等しくない場合にのみ決定的関数になります。|  
  
##  <a name="DateandTimeRelatedTopics"></a>日付と時間に関連するトピック 
  
|トピック|Description|  
|-----------|-----------------|  
|[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)|文字列リテラルとその他の日付/時刻形式間の変換に関する情報を提供します。|  
|[国際化に対応した Transact-SQL ステートメントの記述](../../relational-databases/collations/write-international-transact-sql-statements.md)|データベースとを使用するデータベース アプリケーションの移植性のガイドラインを示します[!INCLUDE[tsql](../../includes/tsql-md.md)]言語から、1 つ別、またはそのステートメントが複数の言語をサポートします。|  
|[ODBC スカラー関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/odbc-scalar-functions-transact-sql.md)|使用できる ODBC スカラー関数に関する情報を提供[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 これには、ODBC の日付と時刻の関数が含まれます。|  
|[タイム ゾーンと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/at-time-zone-transact-sql.md)|タイム ゾーンの変換を提供します。|  
  
## <a name="see-also"></a>参照
[関数](../../t-sql/functions/functions.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

