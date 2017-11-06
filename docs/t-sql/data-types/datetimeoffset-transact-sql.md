---
title: "datetimeoffset (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetimeoffset_TSQL
- datetimeoffset
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetimeoffset
- datetimeoffset data type [SQL Server]
- dates [SQL Server], data types
- data types [SQL Server], date and time
- time zones [SQL Server]
ms.assetid: a0455b71-ca25-476e-a7a8-0770f1860bb7
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a6c143380711d1af39a6c11f311e9ce3caf87c7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datetimeoffset-transact-sql"></a>datetimeoffset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

タイム ゾーンを認識する 24 時間形式の時刻と組み合わせた日付を定義します。
  
## <a name="datetimeoffset-description"></a>datetimeoffset の説明
  
|プロパティ|値|  
|---|---|
|構文|**datetimeoffset** [(*秒の小数部の有効桁数*)]|  
|使用方法|宣言@MyDatetimeoffset **datetimeoffset (7)**<br /><br /> Table1 のテーブルの作成 (Column1 **datetimeoffset (7)** )|  
|既定の文字列リテラル形式 (下位クライアント用)|YYYY-MM-DD hh:mm:ss [.nnnnnnn] [{+&#124;-} hh:mm]<br /><br /> 詳細については、以下の「下位クライアントの下位互換性」セクションを参照してください。|  
|日付範囲|0001-01-01 ～ 31.12.99<br /><br /> 1 月 1 日 1 年 12 月 31 日まで CE ~ 9999 CE|  
|時刻範囲|00時 00分: 00 23:59:59.9999999 から (Informatica では、秒の小数部はサポートされていません)|  
|タイム ゾーン オフセット範囲|-14:00 ~ + 14:00 (Informatica でタイム ゾーン オフセットは無視されます)|  
|要素範囲|YYYY は、0001 ～ 9999 の年を表す 4 桁の数字です。<br /><br /> MM は 2 桁の数字、01 から指定した年、月を表す 12 までの範囲です。<br /><br /> DD は 2 桁の数字、01 から指定した月の日を表す 31、月に応じてです。<br /><br /> hh は、00 ～ 23 の時を表す 2 桁の数字です。<br /><br /> mm は、00 ～ 59 の分を表す 2 桁の数字です。<br /><br /> ss は、00 ～ 59 の秒を表す 2 桁の数字です。<br /><br /> n* は、秒の有効桁数を表す 0 ～ 7 桁の数字です (0 ～ 9999999)。 Informatica では、秒の小数部はサポートされていません。<br /><br /> hh は、-14 ～ +14 までの 2 桁の数字です。 Informatica でタイム ゾーン オフセットは無視されます。<br /><br /> mm は、00 ～ 59 の 2 桁の数字です。 Informatica でタイム ゾーン オフセットは無視されます。|  
|文字長|26 文字 (- YYYY-MM-DD hh:mm:ss {+&#124;-} hh:mm) 34 文字 (- YYYY-MM-DD hh:mm:ss.nnnnnnn {+&#124;-} hh:mm)|  
|有効桁数、小数点以下桁数|次の表を参照してください。|  
|ストレージのサイズ|既定では 10 バイト固定 (秒部分の既定の有効桁数は 100ns) です。|  
|精度|100 ナノ秒|  
|既定値|1900-01-01 00:00:00 00:00|  
|カレンダー|グレゴリオ暦|  
|ユーザー定義の 1 秒未満の秒の有効桁数|はい|  
|タイム ゾーン オフセットへの対応と保持|はい|  
|夏時間への対応|不可|  
  
|指定した小数点以下桁数|結果 (有効桁数、小数点以下桁数)|列長 (バイト単位)|秒の小数部の有効桁数|  
|---|---|---|---|
|**datetimeoffset**|(34,7)|10|7|  
|**datetimeoffset(0)**|(26,0)|8|0-2|  
|**datetimeoffset(1)**|(28,1)|8|0-2|  
|**datetimeoffset(2)**|(29,2)|8|0-2|  
|**datetimeoffset(3)**|(30,3)|9|3-4|  
|**datetimeoffset(4)**|(31,4)|9|3-4|  
|**datetimeoffset(5)**|(32,5)|10|5-7|  
|**datetimeoffset(6)**|(33,6)|10|5-7|  
|**datetimeoffset (7)**|(34,7)|10|5-7|  
  
## <a name="supported-string-literal-formats-for-datetimeoffset"></a>Datetimeoffset の文字列リテラル形式をサポート
次の表は、サポートされている ISO 8601 文字列リテラル形式を**datetimeoffset**です。 日付と時刻の部分のアルファベット、数字、区切りなし、時間の形式については**datetimeoffset**を参照してください[日付と &#40;です。TRANSACT-SQL と&#41; です。](../../t-sql/data-types/date-transact-sql.md)と[&#40;TRANSACT-SQL と&#41; です。](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601|Description|  
|---|---|
|YYYY、MM、DDThh:mm:ss [.nnnnnnn] [{+&#124;- hh:mm]|この 2 つの形式は、セッションのロケール設定である SET LANGUAGE および SET DATEFORMAT の影響を受けません。 間のスペースは使用できません、 **datetimeoffset**と**datetime**部分。|  
|YYYY-MM-DDThh:mm:ss[.nnnnnnn]Z (UTC)|ISO 定義に基づくこの形式を示します、 **datetime**部分は、世界協定時刻 (UTC) で表す必要があります。 たとえば、1999-12-12 12:30:30.12345 -07:00 は 1999-12-12 19:30:30.12345Z と表す必要があります。|  
  
## <a name="time-zone-offset"></a>タイム ゾーン オフセット
タイム ゾーン オフセットの utc を基準とゾーン オフセットを指定する、**時間**または**datetime**値。 タイム ゾーン オフセットは、[+|-] hh:mm として表すことができます。
-   hh は、タイム ゾーン オフセットの時間数を表す 00 ～ 14 の 2 桁の数字です。  
-   mm は、タイム ゾーン オフセットの付加的な分数を表す 00 ～ 59 の 2 桁の数字です。  
-   \+(正符号 +) または – (負) には、タイム ゾーン オフセットの必須の符号。 ローカル時刻を取得する際、UTC 時刻を基準としてタイム ゾーン オフセットを加算するか、減算するかを示します。 タイム ゾーン オフセットの有効範囲は -14:00 ～ +14:00 までです。  
  
タイム ゾーン オフセットの範囲は、XSD スキーマ定義の W3C XML 標準に準拠しており、SQL 2003 標準の定義 (12:59 ～ +14:00) とは若干異なります。
  
省略可能な型パラメーター*秒の小数部の有効桁数*秒の小数部の桁の数字の数を指定します。 この値は、0 ～ 7 (100 ナノ秒) の整数で指定できます。 既定値*秒の小数部の有効桁数*は 100 ns (7 桁の秒の小数部)。
  
データベースに格納されたデータは、サーバーで UTC として処理、比較、並べ替え、およびインデックス化されます。 タイム ゾーン オフセットは、データベースに保持され、必要に応じて取得できます。
  
指定したタイム ゾーン オフセットは夏時間 (DST) 認識し、特定の調整済みであると想定されます**datetime** DST 期間内にあります。
  
**Datetimeoffset** UTC とオフセットのローカル (、永続的なと変換後のタイム ゾーン) の両方を入力**datetime**値が挿入、更新、算術演算、変換、または割り当て操作中に検証されます。 無効な UTC または (永続的なと変換後のタイム ゾーン オフセット) にローカルの検出**datetime**値には、無効な値がエラーが発生します。 たとえば、9999-12-31 10:10:00 は UTC では有効ですが、タイム ゾーン オフセットを +13:50 に設定したローカル時間ではオーバーフローします。
  
対応した日付に変換する**datetimeoffset**ターゲット タイム ゾーン内の値を参照してください[AT TIME ZONE &#40;です。TRANSACT-SQL と&#41; です。](../../t-sql/queries/at-time-zone-transact-sql.md).
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI および ISO 8601 準拠  
ANSI および ISO 8601 準拠のセクションで、[日付](../../t-sql/data-types/date-transact-sql.md)と[時間](../../t-sql/data-types/time-transact-sql.md)トピックに適用**datetimeoffset**です。
  
## <a name="backward-compatibility-for-down-level-clients"></a>ダウンレベル クライアントの旧バージョンとの互換性
一部のダウンレベルのクライアントをサポートしていない、**時間**、**日付**、 **datetime2**と**datetimeoffset**データ型。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の上位インスタンスと下位クライアントの間のデータ型マッピングを次の表に示します。
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型|下位クライアントに渡される既定の文字列リテラル形式|下位 ODBC|下位 OLEDB|下位 JDBC|下位 SQLCLIENT|  
|---|---|---|---|---|---|
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**date**|-YYYY-MM-DD|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetime2**|YYYY-MM-DD hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetimeoffset**|YYYY-MM-DD hh:mm:ss [.nnnnnnn] [+&#124;-] hh:mm|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
  
## <a name="converting-date-and-time-data"></a>日付と時刻のデータを変換します。
日付と時刻のデータ型に変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付や時刻として認識できないすべての値を拒否します。 CAST および CONVERT 関数の日付と時刻のデータの使用方法については、次を参照してください。 [CAST および CONVERT &#40;です。TRANSACT-SQL と&#41; です。](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
変換するときに**日付**年、月、および日がコピーされます。 次のコードは、変換した結果を示しています、`datetimeoffset(4)`値を`date`値。  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10 +01:00';  
DECLARE @date date= @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @date AS 'date';  
  
--Result  
--@datetimeoffset                date  
-------------------------------- ----------  
--2025-12-10 12:32:10.0000 +01:0 2025-12-10  
--  
--(1 row(s) affected)  
  
```  
  
変換することが場合**time (n)**、分、秒、および秒の小数部がコピーされます。 タイム ゾーンの値は切り捨てられます。 ときの有効桁数、 **datetimeoffset (n)**値が、有効桁数より大きい、 **time (n)**値、値は切り上げられます。 次のコードは、変換した結果を示しています、`datetimeoffset(4)`値を`time(3)`値。
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @time time(3) = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @time AS 'time';  
  
--Result  
--@datetimeoffset                time  
-------------------------------- ------------  
-- 2025-12-10 12:32:10.1237 +01:00    12:32:10.124  
  
--  
--(1 row(s) affected)  
  
```  
  
変換するときに**datetime**日付と時刻の値がコピーされ、タイム ゾーンが切り捨てられます。 ときの有効桁数、 **datetimeoffset (n)**値が 3 桁を超える場合、値は切り捨てられます。 次のコードは、変換した結果を示しています、`datetimeoffset(4)`値を`datetime`値。
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @datetime AS 'datetime';  
  
--Result  
--@datetimeoffset                datetime  
-------------------------------- -----------------------  
--2025-12-10 12:32:10.1237 +01:0 2025-12-10 12:32:10.123  
--  
--(1 row(s) affected)  
```  
  
変換**smalldatetime**日付と時間がコピーされます。 分は秒の値に応じて切り上げられ、秒は 0 に設定されます。 次のコードは、変換した結果を示しています、`datetimeoffset(3)`値を`smalldatetime`値。  
  
```sql
DECLARE @datetimeoffset datetimeoffset(3) = '1912-10-25 12:24:32 +10:0';  
DECLARE @smalldatetime smalldatetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetimeoffset                @smalldatetime  
-------------------------------- -----------------------  
--1912-10-25 12:24:32.000 +10:00 1912-10-25 12:25:00  
--  
--(1 row(s) affected)  
```  
  
変換することが場合**datetime2 (n)**、日付と時刻にコピーされます、 **datetime2**値、およびタイム ゾーンは切り捨てられます。 ときの有効桁数、 **datetime2 (n)**値が、有効桁数より大きい、 **datetimeoffset (n)**値に合わせて、秒の小数部が切り捨てられます。 次のコードは、変換した結果を示しています、`datetimeoffset(4)`値を`datetime2(3)`値。
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1912-10-25 12:24:32.1277 +10:0';  
DECLARE @datetime2 datetime2(3)=@datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @datetime2 AS '@datetime2';  
  
--Result  
@datetimeoffset                    @datetime2  
---------------------------------- ----------------------  
1912-10-25 12:24:32.1277 +10:00    1912-10-25 12:24:32.12  
  
--(1 row(s) affected)  
```  
  
### <a name="converting-datetimeoffset-data-type-to-other-date-and-time-types"></a>Datetimeoffset データ型を他の日付と時刻型に変換します。
次の表では、どうなるかについて説明しますと、 **datetimeoffset**データ型は他の日付と時刻のデータ型に変換します。
  
### <a name="converting-string-literals-to-datetimeoffset"></a>文字列リテラルの datetimeoffset への変換
文字列リテラルから日付/時刻データ型への変換は、文字列のすべての部分が有効な形式になっている場合に可能になります。 それ以外の場合は実行時エラーが発生します。 日付/時刻データ型から文字列リテラルへの暗黙的な変換や、スタイルを指定しない明示的な変換では、現在のセッションの既定の形式が使用されます。 次の表はリテラルを文字列に変換するための規則は、 **datetimeoffset**データ型。
  
|入力文字列リテラル|**datetimeoffset (n)**|  
|---|---|
|ODBC 日付|ODBC 文字列リテラルにマップされる、 **datetime**データ型。 ODBC 日付時刻リテラルから代入演算を行う**datetimeoffset**型間の暗黙的な変換の場合は**datetime**この型の変換規則で定義されているとします。|  
|ODBC 時刻|上記の ODBC 日付の規則を参照。|  
|ODBC 日付時刻|上記の ODBC 日付の規則を参照。|  
|日付のみ|時刻部分は既定値の 00:00:00 に設定される タイム ゾーン既定値は + 00時 00分です。|  
|時刻のみ|日付部分は既定値の 1900-1-1 に設定される タイム ゾーンは既定値の +00:00 に設定される|  
|タイム ゾーンのみ|既定値を指定します。|  
|日付 + 時刻|タイム ゾーン既定値は + 00時 00分です。|  
|日付 + タイム ゾーン|使用不可|  
|時刻 + タイム ゾーン|日付部分は既定値の 1900-1-1 に設定される|  
|日付 + 時刻 + タイム ゾーン|単純変換|  
  
## <a name="examples"></a>使用例  
次の例は、文字列をそれぞれをキャストした結果を比較**日付**と**時間**データ型。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset'  
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetimeoffset(7)) AS  
        'datetimeoffset IS08601';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|データ型|出力|  
|---|---|
|**[時刻]**|12:35:29. 1234567|  
|**[日付]**|2007-05-08|  
|**Smalldatetime**|2007-05-08 12:35:00|  
|**DateTime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**Datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[タイム ゾーンと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  

