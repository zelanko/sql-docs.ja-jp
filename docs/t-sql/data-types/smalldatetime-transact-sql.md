---
title: "smalldatetime (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07012d85a54292fa763a7b291d1b7318b6969ca4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetime-transact-sql"></a>smalldatetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

日付を時刻と組み合わせて定義します。 時刻は 24 時間制です。秒数は常にゼロ (:00) で、1 秒未満の秒を持ちません。
  
> [!NOTE]  
>  使用して、**時間**、**日付**、 **datetime2**と**datetimeoffset**新しい作業のデータ型。 これらの型は、SQL 標準に準拠しています。 これらの型は、より高い移植性を持ちます。 **時間**、 **datetime2**と**datetimeoffset**提供し、有効桁数 (秒)。 **datetimeoffset**グローバルに配置されるアプリケーションのタイム ゾーンのサポートを提供します。  
  
## <a name="smalldatetime-description"></a>smalldatetime の説明
  
|||  
|-|-|  
|構文|**smalldatetime**|  
|使用方法|宣言@MySmalldatetime **smalldatetime**<br /><br /> テーブル Table1 の作成 (Column1 **smalldatetime** )|  
|既定の文字列リテラル形式<br /><br /> (下位のクライアントに使用)|適用なし|  
|日付範囲|1900-01-01 ～ 2079-06-06<br /><br /> 1900 年 1 月 1 日～ 2079 年 6 月 6 日|  
|時刻範囲|00:00:00 ～ 23:59:59<br /><br /> 2007-05-09 23:59:59 は次のように丸められます。<br /><br /> 2007-05-10 00:00:00|  
|要素範囲|YYYY は、1900 ～ 2079 の年を表す 4 桁の数字です。<br /><br /> MM は 2 桁の数字、01 から指定した年、月を表す 12 までの範囲です。<br /><br /> DD は 2 桁の数字、01 から指定した月の日を表す 31、月に応じてです。<br /><br /> hh は、00 ～ 23 の時を表す 2 桁の数字です。<br /><br /> mm は、00 ～ 59 の分を表す 2 桁の数字です。<br /><br /> ss は、00 ～ 59 の秒を表す 2 桁の数字です。 29.998 秒以下の値は最も近い分単位の値に切り捨てられます。29.999 秒以上の値は最も近い分単位の値に切り上げられます。|  
|文字長|最大 19 文字|  
|ストレージのサイズ|4 バイト、固定|  
|精度|1 分|  
|既定値|1900-01-01 00:00:00|  
|カレンダー|グレゴリオ暦<br /><br /> (完全な年の範囲は含まれません。)|  
|ユーザー定義の 1 秒未満の秒の有効桁数|不可|  
|タイム ゾーン オフセットへの対応と保持|不可|  
|夏時間への対応|不可|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI および ISO 8601 への準拠  
**smalldatetime**は ANSI または ISO 8601 準拠していません。
  
## <a name="converting-date-and-time-data"></a>日付と時刻のデータを変換します。
日付と時刻のデータ型に変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付や時刻として認識できないすべての値を拒否します。 CAST および CONVERT 関数の日付と時刻のデータの使用方法については、次を参照してください。 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>その他の日付と時刻型から smalldatetime への変換
このセクションでは、どうなるかについて説明しますと、 **smalldatetime**データ型は他の日付と時刻のデータ型に変換します。
  
変換の場合**日付**年、月、および日がコピーされます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`date`値。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
ときに、変換を**time (n)**時間、分、および秒がコピーされます。 秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`time(4)`値。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
ときに、変換を**datetime**、 **smalldatetime**値をコピー、 **datetime**値。 秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`datetime`値。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
変換の場合**datetimeoffset (n)**、 **smalldatetime**値をコピー、 **datetimeoffset (n)**値。 秒の小数部は 0 に設定され、タイム ゾーン オフセットは +00:0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`datetimeoffset(4)`値。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
変換の**datetime2 (n)**、 **smalldatetime**値をコピー、 **datetime2 (n)**値。 秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`datetime2(4)`値。
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>A. 秒を含む文字列リテラルを smalldatetime にキャストする  
次の例では、文字列リテラル内の秒の `smalldatetime` への変換を比較します。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|入力|出力|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>B. 日付/時刻データ型を比較する  
次の例では、文字列をそれぞれの日付および時刻データ型にキャストした結果を比較します。
  
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
  
  

