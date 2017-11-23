---
title: "datetime (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime_TSQL
- datetime
dev_langs: TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetime
- dates [SQL Server], data types
- datetime data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: 9bd1cc5b-227b-4032-95d6-7581ddcc9924
caps.latest.revision: "64"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4493e165efbc0410d444f34fc41e30cc08e90307
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="datetime-transact-sql"></a>datetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

24 時間形式の時刻 (1 秒未満の秒を含む) と組み合わせた日付を定義します。
  
> [!NOTE]  
>  使用して、**時間**、**日付**、 **datetime2**と**datetimeoffset**新しい作業のデータ型。 これらの型は、SQL 標準に準拠しています。 これらの型は、より高い移植性を持ちます。 **時間**、 **datetime2**と**datetimeoffset**提供し、有効桁数 (秒)。 **datetimeoffset**グローバルに配置されるアプリケーションのタイム ゾーンのサポートを提供します。  
  
## <a name="datetime-description"></a>datetime の説明  
  
|プロパティ|値|  
|---|---|
|構文|**datetime**|  
|使用方法|宣言@MyDatetime **datetime**<br /><br /> テーブル Table1 の作成 (Column1 **datetime** )|  
|既定の文字列リテラル形式<br /><br /> (下位のクライアントに使用)|適用なし|  
|日付範囲|1753 年 1 月 1 日～ 9999 年 12 月 31 日|  
|時刻範囲|00時 00分: 00 23:59:59.997 経由|  
|タイム ゾーン オフセット範囲|なし|  
|要素範囲|YYYY は、1753 ～ 9999 の年を表す 4 桁の数字です。<br /><br /> MM は 2 桁の数字、01 から指定した年、月を表す 12 までの範囲です。<br /><br /> DD は 2 桁の数字、01 から指定した月の日を表す 31、月に応じてです。<br /><br /> hh は、00 ～ 23 の時を表す 2 桁の数字です。<br /><br /> mm は、00 ～ 59 の分を表す 2 桁の数字です。<br /><br /> ss は、00 ～ 59 の秒を表す 2 桁の数字です。<br /><br /> n* は、秒の有効桁数を表す 3 桁の数字です (0 ～ 999)。|  
|文字長|19 文字以上、23 文字以下|  
|ストレージのサイズ|8 バイト|  
|精度|値は、.000、.003、または .007 秒単位に丸められます。|  
|既定値|1900-01-01 00:00:00|  
|カレンダー|グレゴリオ暦 (完全な年の範囲は含まれません。)|  
|ユーザー定義の 1 秒未満の秒の有効桁数|不可|  
|タイム ゾーン オフセットへの対応と保持|不可|  
|夏時間への対応|不可|  
  
## <a name="supported-string-literal-formats-for-datetime"></a>datetime でサポートされる文字列リテラル形式  
次の表に、サポートされている文字列リテラル形式を**datetime**です。 ODBC を除き、 **datetime**文字列リテラルは単一引用符 (')、たとえば、'string_literaL' です。 環境がない場合**us_english**、文字列リテラルが形式 N 'string_literaL' にする必要があります。
  
|数値|Description|  
|---|---|
|日付形式 :<br /><br /> [0]4/15/[19]96 -- (mdy)<br /><br /> [0]4-15-[19]96 -- (mdy)<br /><br /> [0]4.15.[19]96 -- (mdy)<br /><br /> [0]4/[19]96/15 -- (myd)<br /><br /> 15/[0]4/[19]96 -- (dmy)<br /><br /> 15/[19]96/[0]4 -- (dym)<br /><br /> [19]96/15/[0]4 -- (ydm)<br /><br /> [19]96/[0]4/15 -- (ymd)<br /><br /> 時刻形式 :<br /><br /> 14:30<br /><br /> 14:30[:20:999]<br /><br /> 14:30[:20.9]<br /><br /> 4am<br /><br /> 4 PM|月名を数値で表して日付データを指定できます。 たとえば、5/20/97 は 1997 年 5 月 20 日を表します。 数値データの形式を使用する場合、文字列の年、月、日は、スラッシュ (/)、ハイフン (-)、またはピリオド (.) で区切って指定します。 この文字列は、次の形式に従う必要があります。<br /><br /> *数値の区切り記号番号区切り番号 [time] [時間]*<br /><br /> <br /><br /> ときに、言語に設定されている**us_english**日付の既定の順序が mdy します。 使用して日付順序を変更することができます、 [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)ステートメントです。<br /><br /> SET DATEFORMAT の設定は、日付の値がどのように解釈されるかを決定します。 指定した順序が設定と一致しない場合、範囲外となって日付として解釈されないか、または間違って解釈されます。 たとえば、12/10/08 は、DATEFORMAT の設定によっては、6 種類の日付形式のうちのいずれにも解釈できます。 4 桁の部分は年と解釈されます。|  
  
|アルファベット|Description|  
|---|---|
|Apr[il] [15][,] 1996<br /><br /> Apr[il] 15[,] [19]96<br /><br /> Apr[il] 1996 [15]<br /><br /> [15] Apr[il][,] 1996<br /><br /> 15 Apr[il][,][19]96<br /><br /> 15 [19]96 apr[il]<br /><br /> [15] 1996 apr[il]<br /><br /> 1996 APR[IL] [15]<br /><br /> 1996 [15] APR[IL]|月の正式名を使って日付データを指定できます。 たとえば、現在の言語で指定されている April やその省略形である Apr を使用できます。コンマは省略でき、大文字と小文字の違いは無視されます。<br /><br /> アルファベット日付形式の使用に関するガイドラインを次に示します。<br /><br /> 1) の日付と時刻のデータを単一引用符 (') で囲みます。 English 以外の言語では、N' を使用します。<br /><br /> 角かっこで囲まれた 2) 文字は省略できます。<br /><br /> 3) 年の最後の 2 桁のみを指定すると、値の値の最後の 2 つの桁より小さければ、[構成 two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)構成オプションは、終了年と同じ世紀には. この構成オプションより値が大きいか、または同じである場合、指定した西暦は終了年の世紀より前の世紀になります。 たとえば場合、**カットオフの 2 桁の年**が 2050 (既定)、25 は 2025 年と解釈 50 は 1950 年と解釈されます。 こうしたあいまいさを排除するため、4 桁の西暦を使用してください。<br /><br /> 4)、1 日が見つからない場合、月の最初の日を指定します。<br /><br /> <br /><br /> 月をアルファベット形式で指定したときは、SET DATEFORMAT のセッション設定は適用されません。|  
  
|ISO 8601|Description|  
|---|---|
|YYYY-MM-DDThh:mm:ss[.mmm]<br /><br /> YYYYMMDD[ hh:mm:ss[.mmm]]|例 :<br /><br /> 1) 2004-05-23T14:25:10<br /><br /> 2) 2004-05-23T14:25:10.487<br /><br /> <br /><br /> ISO 8601 形式を使用するには、その形式で各要素を指定する必要があります。 これも含まれています、 **T**コロン (:)、およびピリオド (.) の形式で示されています。<br /><br /> 秒の構成要素を示す角かっこは省略できます。 時の構成要素は 24 時間形式で指定します。<br /><br /> T の時刻部分の先頭を示す、 **datetime**値。<br /><br /> ISO 8601 形式を使用する利点は、これが明確な仕様を持つ国際標準であるという点です。 また、この形式は影響しません、SET DATEFORMAT または[SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)設定します。|  
  
|区切りなし|Description|  
|---|---|
|YYYYMMDD hh:mm:ss[.mmm]||  
  
|ODBC|Description|  
|---|---|
|{ ts '1998-05-02 01:23:56.123' }<br /><br /> { d '1990-10-02' }<br /><br /> { t '13:33:41' }|ODBC API では、日付時刻値を表すエスケープ シーケンスが定義されます。ODBC ではこれをタイムスタンプ データと呼びます。 サポートされている OLE DB 言語定義 (DBGUID-SQL) では、この ODBC タイムスタンプ形式はサポートされても、[!INCLUDE[msCoName](../../includes/msconame-md.md)]の OLE DB プロバイダー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ADO、OLE DB、および ODBC ベースの API を使用しているアプリケーションでは、この ODBC タイムスタンプ形式を使用して日付/時刻を表すことができます。<br /><br /> ODBC タイムスタンプ エスケープ シーケンスは、の形式: { *literal_type* '*constant_value*'}。<br /><br /> <br /><br /> - *literal_type*エスケープ シーケンスの種類を指定します。 タイムスタンプがある 3 つ*literal_type*指定子。<br />1) d = 日付のみ<br />2) t = 時刻のみ<br />3) ts = タイムスタンプ (時刻と日付)<br /><br /> <br /><br /> -'*constant_value*' エスケープ シーケンスの値です。 *constant_value*ごとにこれらの形式に従う必要があります*literal_type*です。<br />d: yyyy mm dd<br />t: hh:mm:ss [.fff]<br />ts: - yyyy-mm-dd hh:mm:ss [.fff]|  
  
## <a name="rounding-of-datetime-fractional-second-precision"></a>datetime における 1 秒未満の秒の有効桁数の丸め処理  
**datetime**次の表に示すように、値は.000、.003、または.007 秒単位に丸められます。
  
|ユーザー指定の値|システム格納値|  
|---|---|
|01/01/98 23:59:59.999|1998-01-02 00:00:00.000|  
|01/01/98 23:59:59.995<br /><br /> 01/01/98 23:59:59.996<br /><br /> 01/01/98 23:59:59.997<br /><br /> 01/01/98 23:59:59.998|1998-01-01 23:59:59.997|  
|01/01/98 23:59:59.992<br /><br /> 01/01/98 23:59:59.993<br /><br /> 01/01/98 23:59:59.994|1998-01-01 23:59:59.993|  
|01/01/98 23:59:59.990<br /><br /> 01/01/98 23:59:59.991|1998-01-01 23:59:59.990|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI および ISO 8601 への準拠  
**datetime**は ANSI または ISO 8601 準拠していません。
  
##  <a name="_datetime"></a>日付と時刻のデータを変換します。  
日付と時刻のデータ型に変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付や時刻として認識できないすべての値を拒否します。 CAST および CONVERT 関数の日付と時刻のデータの使用方法については、次を参照してください。 [CAST および CONVERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-other-date-and-time-types-to-the-datetime-data-type"></a>その他の日付と時刻型を datetime データ型に変換します。 
このセクションでは、他の日付と時刻データ型が変換するときの動作について説明します、 **datetime**データ型。  
  
変換がから場合**日付**年、月、日がコピーされます。 時刻部分は 00:00:00.000 に設定されます。 次のコードは、変換した結果を示しています、`date`値を`datetime`値。  
  
```sql
DECLARE @date date = '12-21-16';  
DECLARE @datetime datetime = @date;  
  
SELECT @datetime AS '@datetime', @date AS '@date';  
  
--Result  
--@datetime               @date  
------------------------- ----------  
--2016-12-21 00:00:00.000 2016-12-21  
```  
  
変換がから場合**time (n)**時刻部分がコピーされ、日付部分に設定、' 1900-01-01' です。 ときの有効桁数、 **time (n)**値が 3 桁を超える場合、値に合わせて切り捨てられます。 次の例は、`time(4)` 値を `datetime` 値に変換した結果を示しています。  
  
```sql
DECLARE @time time(4) = '12:10:05.1237';  
DECLARE @datetime datetime = @time;  
  
SELECT @datetime AS '@datetime', @time AS '@time';  
  
--Result  
--@datetime               @time  
------------------------- -------------  
--1900-01-01 12:10:05.123 12:10:05.1237  
```  
  
変換がから場合**smalldatetime**時間と分がコピーされます。 秒と秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`datetime`値。  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @datetime AS '@datetime', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetime               @smalldatetime  
------------------------- -----------------------  
--2016-12-01 12:32:00.000 2016-12-01 12:32:00  
```  
  
変換がから場合**datetimeoffset (n)**日付と時刻のコンポーネントがコピーされます。 タイム ゾーンは切り捨てられます。 ときの有効桁数、 **datetimeoffset (n)**値が 3 桁を超える場合、値が切り捨てられます。 次の例は、`datetimeoffset(4)` 値を `datetime` 値に変換した結果を示しています。  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1968-10-23 12:45:37.1234 +10:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetime AS '@datetime', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@datetime               @datetimeoffset  
------------------------- ------------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237 +01:0   
```  
  
変換がから場合**datetime2 (n)**日付と時刻がコピーされます。 ときの有効桁数、 **datetime2 (n)**値が 3 桁を超える場合、値が切り捨てられます。 次の例は、`datetime2(4)` 値を `datetime` 値に変換した結果を示しています。  
  
```sql
DECLARE @datetime2 datetime2(4) = '1968-10-23 12:45:37.1237';  
DECLARE @datetime datetime = @datetime2;  
  
SELECT @datetime AS '@datetime', @datetime2 AS '@datetime2';  
  
--Result  
--@datetime               @datetime2  
------------------------- ------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237  
```  
  
## <a name="examples"></a>使用例  
次の例は、文字列をそれぞれをキャストした結果を比較**日付**と**時間**データ型。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|データ型|出力|  
|---|---|
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
