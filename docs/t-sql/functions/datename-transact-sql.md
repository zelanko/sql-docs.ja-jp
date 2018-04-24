---
title: DATENAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATENAME_TSQL
- DATENAME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATENAME function [SQL Server
- functions [SQL Server], time
- functions [SQL Server], date and time
- dateparts [SQL Server], datename
- date and time [SQL Server], DATENAME
- comparing dates times [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 11855b56-c554-495d-aad4-ba446990153b
caps.latest.revision: 59
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a8803278c567f01888b7b530885e82e4543c966a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="datename-transact-sql"></a>DATENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

表す、指定された文字列を返します *datepart* の指定された *日付*
  
すべての概要については [!INCLUDE[tsql](../../includes/tsql-md.md)] 日付と時刻のデータ型および関数、を参照してください。[ 日付と時刻のデータ型および関数と #40 です。TRANSACT-SQL と #41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATENAME ( datepart , date )  
```  
  
## <a name="arguments"></a>引数  
*datepart*  
返される *date* の一部を指定します。 次の表に一覧のすべての有効な *datepart* 引数。 ユーザー定義変数に相当するものは無効です。
  
|*datepart*|省略形|  
|---|---|
|**year**|**yy、yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy、y**|  
|**day**|**dd, d**|  
|**week**|**wk、ww**|  
|**weekday**|**dw、w**|  
|**hour**|**mm**|  
|**minute**|**mi、n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
|**TZoffset**|**tz**|  
|**ISO_WEEK**|**ISOWK、ISOWW**|  
  
*date*  
**time**、**date**、**smalldatetime**、**datetime**、**datetime2**、または **datetimeoffset** 値に解決できる式です。 *日付* 、式、列式、ユーザー定義変数、または文字列リテラルを指定できます。  
こうしたあいまいさを排除するため、4 桁の西暦を使用してください。 については 2 桁の年を参照してください [構成 two digit year cutoff サーバー構成オプション](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)です。
  
## <a name="return-type"></a>戻り値の型  
**nvarchar**
  
## <a name="return-value"></a>戻り値  
  
-   *-各日付構成要素とその省略形は、同じ値を返します。*  
  
* *、戻り値を使用して設定した言語環境によって異なります [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) および、 [サーバー構成オプションの既定の言語を構成する](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) ログインします。 戻り値に依存関係にあるは [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)*日付*が文字列の場合のいくつかの形式のリテラルです。 date が日付データ型や時刻データ型の列式である場合、SET DATEFORMAT は戻り値に影響しません。
  
*日付* パラメーターに **日付** データ型引数がある場合、戻り値は [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md) を使用して指定された設定に依存します。
  
## <a name="tzoffset-datepart-argument"></a>TZoffset (datepart 引数)  
*Datepart* 引数 **TZoffset** (**tz**) は、*date* 引数には、タイム ゾーン オフセットがない場合は、0 が返されます。
  
## <a name="smalldatetime-date-argument"></a>smalldatetime (date 引数)  
* * *日付*の場合 [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), 、秒は 00.* * として返されます。
  
## <a name="default-returned-for-a-datepart-that-is-not-in-the-date-argument"></a>date 引数に存在しない datepart を指定した場合に返される既定値  
*日付*引数のデータ型が指定された*日付要素*を持たない場合、リテラルの*日付*が指定されている場合にのみその *datepart* の既定値が返されます。
  
* * など、既定の年-月-日の任意の**日付**データ型は 1900年-01-01 です。 次のステートメントの引数の*日付*、*日付の要素*の日付引数があり、1900 年`1900, January, 1, 1, Monday`が返されます 1、1, 1, 2。*
  
```sql
SELECT DATENAME(year, '12:10:30.123')  
    ,DATENAME(month, '12:10:30.123')  
    ,DATENAME(day, '12:10:30.123')  
    ,DATENAME(dayofyear, '12:10:30.123')  
    ,DATENAME(weekday, '12:10:30.123');  
```  
  
*変数やテーブルの列として*日付*を指定して、データ型の変数または列に指定された*日付要素*をいないこと、エラー 9810 が返されます。 次のコード例は、年の部分が *@t*変数に対して宣言されている **time** データ型では有効でないために失敗します。
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATENAME(year, @t);  
```  
  
## <a name="remarks"></a>Remarks  
DATENAME は、選択リストのほか、WHERE 句、HAVING 句、GROUP BY 句、および ORDER BY 句で使用できます。
  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , 、DATENAME は、文字列リテラルを暗黙的にキャスト、 **datetime2** 型です。 つまり、DATENAME では、日付が文字列として渡される場合、YDM 形式をサポートしません。 文字列を明示的にキャストする必要があります、 **datetime** または **smalldatetime** YDM 形式を使用する型。
  
## <a name="examples"></a>使用例  
次の例は、指定された日付の日付部分を返します。
  
`SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');`
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*datepart*|戻り値|  
|---|---|
|**year、yyyy、yy**|2007|  
|**quarter、qq、q**|4|  
|**month、mm、m**|10 月|  
|**dayofyear、dy、y**|303|  
|**day、dd、d**|30|  
|**week、wk、ww**|44|  
|**weekday、dw**|火曜日|  
|**hour、hh**|12|  
|**minute、n**|15|  
|**second、ss、s**|32|  
|**millisecond、ms**|123|  
|**microsecond、mcs**|123456|  
|**nanosecond、ns**|123456700|  
|**TZoffset、tz**|310|  
|**ISO_WEEK、ISOWK、ISOWW**|44|  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

次の例は、指定された日付の日付部分を返します。
  
```sql
SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*datepart*|戻り値|  
|---|---|
|**year、yyyy、yy**|2007|  
|**quarter、qq、q**|4|  
|**month、mm、m**|10 月|  
|**dayofyear、dy、y**|303|  
|**day、dd、d**|30|  
|**week、wk、ww**|44|  
|**weekday、dw**|火曜日|  
|**hour、hh**|12|  
|**minute、n**|15|  
|**second、ss、s**|32|  
|**millisecond、ms**|123|  
|**microsecond、mcs**|123456|  
|**nanosecond、ns**|123456700|  
|**TZoffset、tz**|310|  
|**ISO_WEEK、ISOWK、ISOWW**|44|  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

