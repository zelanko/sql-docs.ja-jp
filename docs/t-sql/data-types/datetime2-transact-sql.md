---
title: "datetime2 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime2
- datetime2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- dates [SQL Server], data types
- date and time [SQL Server], datetime2
- data types [SQL Server], date and time
- datetime2 data type [SQL Server]
ms.assetid: 868017f3-214f-43ef-8536-cc1632a2288f
caps.latest.revision: 58
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 13766b3d0cb86780c2eca55c7f36e8fd16e973c5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datetime2-transact-sql"></a>datetime2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

24 時間形式の時刻と組み合わせた日付を定義します。 **datetime2** 、既存の拡張機能と見なされる**datetime**日付範囲が広い、大規模な既定の有効桁数、および省略可能なユーザー指定の有効桁数を持つ型。
  
## <a name="datetime2-description"></a>datetime2 の説明
  
|プロパティ|値|  
|--------------|-----------|  
|構文|**datetime2** [(*秒の小数部の有効桁数*)]|  
|使用方法|宣言@MyDatetime2 **datetime2 (7)**<br /><br /> Table1 のテーブルの作成 (Column1 **datetime2 (7)** )|  
|既定の文字列リテラル形式<br /><br /> (下位のクライアントに使用)|YYYY-MM-DD hh:mm:ss[.fractional seconds]<br /><br /> 詳細については、以下の「下位クライアントの下位互換性」セクションを参照してください。|  
|日付範囲|0001-01-01 ～ 31.12.99<br /><br /> 年 1 月 1, 1 年 12 月 31 日まで CE ~ 9999 CE|  
|時刻範囲|00:00:00 ～ 23:59:59.9999999|  
|タイム ゾーン オフセット範囲|なし|  
|要素範囲|YYYY は、年を表す 0001 ～ 9999 の 4 桁の数字です。<br /><br /> MM は 2 桁の数値、01 から 12 までの範囲を指定した年、月を表すです。<br /><br /> DD は、01 から指定した月の日を表す月に応じて 31 まで、2 桁の数字です。<br /><br /> hh は、時を表す 00 ～ 23 の 2 桁の数字です。<br /><br /> mm は、分を表す 00 ～ 59 の 2 桁の数字です。<br /><br /> ss は、秒を表す 00 ～ 59 の 2 桁の数字です。<br /><br /> n * 0 ~ 7 桁の数値は 0 から 9999999 秒の小数部を表すです。 Informatica で秒の小数部が切り捨てられますときに n > 3 です。|  
|文字長|19 文字 (YYYY-MM-DD hh:mm:ss ) 以上、27 文字 (YYYY-MM-DD hh:mm:ss.0000000) 以下|  
|有効桁数、小数点以下桁数|0 ～ 7 桁で、精度は 100ns です。 既定の有効桁数は 7 桁です。|  
|ストレージのサイズ|有効桁数が 3 未満の場合は 6 バイト、有効桁数が 3 および 4 の場合は 7 バイトです。 その他のすべての有効桁数には 8 バイトが必要です。|  
|精度|100 ナノ秒|  
|既定値|1900-01-01 00:00:00|  
|カレンダー|グレゴリオ暦|  
|ユーザー定義の 1 秒未満の秒の有効桁数|はい|  
|タイム ゾーン オフセットへの対応と保持|不可|  
|夏時間への対応|不可|  
  
データ型のメタデータを参照してください。 [sys.systypes & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md)または[TYPEPROPERTY (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md). 一部の日付時刻データ型では、有効桁数および小数点以下桁数が可変です。 有効桁数と列の小数点以下桁数を取得する、次を参照してください。 [COLUMNPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columnproperty-transact-sql.md)、 [COL_LENGTH (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/col-length-transact-sql.md)、または[sys.columns & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).
  
## <a name="supported-string-literal-formats-for-datetime2"></a>Datetime2 の文字列リテラル形式をサポート
次の表は、サポートされている ISO 8601 および ODBC 文字列リテラル形式を**datetime2**です。 日付と時刻の部分のアルファベット、数値、区切りなし、および時刻の形式については**datetime2**を参照してください[日付と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/date-transact-sql.md)と[&#40;TRANSACT-SQL と #41 です。](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601|[説明]|  
|---|---|
|YYYY-MM-DDThh:mm:ss[.nnnnnnn]<br /><br /> YYYY-MM-DDThh:mm:ss[.nnnnnnn]|この形式は、セッションのロケール設定である SET LANGUAGE および SET DATEFORMAT の影響を受けません。 **T**コロン (:)、およびピリオド (.) に含まれる文字列リテラル、たとえば ' 2007-05-02T19:58:47.1234567' です。|  
  
|ODBC|Description|  
|---|---|
|{ ts 'yyyy-mm-dd hh:mm:ss[.fractional seconds]' }|ODBC API 固有:<br /><br /> 1 秒未満の秒を表す小数点の右側の桁数は、0 ～ 7 (100 ナノ秒) の範囲で指定できます。|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI および ISO 8601 準拠  
ANSI および ISO 8601 準拠[日付](../../t-sql/data-types/date-transact-sql.md)と[時間](../../t-sql/data-types/time-transact-sql.md)に適用**datetime2**です。
  
##  <a name="backward-compatibility-for-down-level-clients"></a>下位クライアントの下位互換性  
一部のダウンレベルのクライアントをサポートしていない、**時間**、**日付**、 **datetime2**と**datetimeoffset**データ型。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の上位インスタンスと下位クライアントの間のデータ型マッピングを次の表に示します。
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型|下位クライアントに渡される既定の文字列リテラル形式|下位 ODBC|下位 OLEDB|下位 JDBC|下位 SQLCLIENT|  
| --- | --- | --- | --- | --- | --- |
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**date**|-YYYY-MM-DD|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetime2**|YYYY-MM-DD hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetimeoffset**|YYYY-MM-DD hh:mm:ss [.nnnnnnn] [+ &#124;-] hh:mm|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
  
## <a name="converting-date-and-time-data"></a>日付と時刻のデータを変換します。
日付と時刻のデータ型に変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日付や時刻として認識できないすべての値を拒否します。 CAST および CONVERT 関数の日付と時刻のデータの使用方法については、次を参照してください。 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
### <a name="converting-other-date-and-time-types-to-the-datetime2-data-type"></a>その他の日付と時刻型、datetime2 データ型に変換
このセクションでは、他の日付と時刻データ型が変換するときの動作について説明します、 **datetime2**データ型。  
  
変換がから場合**日付**年、月、日がコピーされます。  時刻部分は、00:00:00.0000000 に設定されます。  次のコードは、変換した結果を示しています、`date`値を`datetime2`値。  
  
```sql
DECLARE @date date = '12-21-16';
DECLARE @datetime2 datetime2 = @date;

SELECT @datetime2 AS '@datetime2', @date AS '@date';
  
--Result  
--@datetime2                  @date
----------------------------- ----------
--2016-12-21 00:00:00.0000000 2016-12-21
```  
  
変換がから場合**time (n)**時刻部分がコピーされ、日付部分に設定、' 1900-01-01' です。 次の例は、`time(7)` 値を `datetime2` 値に変換した結果を示しています。  
  
```sql
DECLARE @time time(7) = '12:10:16.1234567';
DECLARE @datetime2 datetime2 = @time;

SELECT @datetime2 AS '@datetime2', @time AS '@time';
  
--Result  
--@datetime2                  @time
----------------------------- ----------------
--1900-01-01 12:10:16.1234567 12:10:16.1234567
```  
  
変換がから場合**smalldatetime**時間と分がコピーされます。 秒と秒の小数部は 0 に設定されます。 次のコードは、変換した結果を示しています、`smalldatetime`値を`datetime2`値。  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';
DECLARE @datetime2 datetime2 = @smalldatetime;

SELECT @datetime2 AS '@datetime2', @smalldatetime AS '@smalldatetime'; 
  
--Result  
--@datetime2                  @smalldatetime
----------------------------- -----------------------
--2016-12-01 12:32:00.0000000 2016-12-01 12:32:00 
```  
  
変換がから場合**datetimeoffset (n)**日付と時刻のコンポーネントがコピーされます。 タイム ゾーンは切り捨てられます。 次の例は、`datetimeoffset(7)` 値を `datetime2` 値に変換した結果を示しています。  
  
```sql
DECLARE @datetimeoffset datetimeoffset(7) = '2016-10-23 12:45:37.1234567 +10:0';
DECLARE @datetime2 datetime2 = @datetimeoffset;

SELECT @datetime2 AS '@datetime2', @datetimeoffset AS '@datetimeoffset'; 
  
--Result  
--@datetime2                  @datetimeoffset
----------------------------- ----------------------------------
--2016-10-23 12:45:37.1234567 2016-10-23 12:45:37.1234567 +10:00
```  

変換がから場合**datetime**日付と時刻がコピーされます。  小数部の有効桁数は 7 桁まで拡張されます。  次の例は、`datetime` 値を `datetime2` 値に変換した結果を示しています。

```sql
DECLARE @datetime datetime = '2016-10-23 12:45:37.333';
DECLARE @datetime2 datetime2 = @datetime;

SELECT @datetime2 AS '@datetime2', @datetime AS '@datetime';
   
--Result  
--@datetime2                  @datetime
------------------------- ---------------------------
--2016-10-23 12:45:37.3333333 2016-10-23 12:45:37.333
```  
  
### <a name="converting-string-literals-to-datetime2"></a>文字列リテラルから datetime2 への変換  
文字列リテラルから日付/時刻データ型への変換は、文字列のすべての部分が有効な形式になっている場合に可能になります。 それ以外の場合は実行時エラーが発生します。 日付/時刻データ型から文字列リテラルへの暗黙的な変換や、スタイルを指定しない明示的な変換では、現在のセッションの既定の形式が使用されます。 次の表はリテラルを文字列に変換するための規則は、 **datetime2**データ型。
  
|入力文字列リテラル|**datetime2 (n)**|  
|---|---|
|ODBC 日付|ODBC 文字列リテラルにマップされる、 **datetime**データ型。 ODBC 日付時刻リテラルから代入演算を行う**datetime2**型間の暗黙的な変換の場合は**datetime**この型の変換規則で定義されているとします。|  
|ODBC 時刻|上記の ODBC 日付の規則を参照。|  
|ODBC 日付時刻|上記の ODBC 日付の規則を参照。|  
|日付のみ|時刻部分は既定値の 00:00:00 に設定される|  
|時刻のみ|日付部分は既定値の 1900-1-1 に設定される|  
|タイム ゾーンのみ|既定値が設定される|  
|日付 + 時刻|単純変換|  
|日付 + タイム ゾーン|許可されていません。|  
|時刻 + タイム ゾーン|日付部分は既定値の 1900-1-1 に設定される タイム ゾーンの入力は無視される。|  
|日付 + 時刻 + タイム ゾーン|ローカル datetime が使用される|  
  
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
  
  

