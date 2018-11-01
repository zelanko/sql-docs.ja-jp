---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATEDIFF_BIG
- DATEDIFF_BIG_TSQL
helpviewer_keywords:
- DATEDIFF_BIG function [SQL Server]
- dates [SQL Server]. functions
- date and time [SQL Server], DATEDIFF_BIG
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 19ac1693-3cfa-400d-bf83-20a9cb46599a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4516965f66256e21e5e68310f7668770e17cabb9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644850"
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

この関数は、*startdate* と *enddate* で指定された 2 つの日付間の差を、指定された *datepart* 境界の数で (符号付き多倍長整数値として) 返します。
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] の日付と時刻のあらゆるデータ型と関数に関する概要については、「[日付と時刻のデータ型および関数 &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)」を参照してください。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>引数  
*datepart*  
*startdate* と *enddate* の差を求めるときの単位に使用する要素を指定します。 `DATEDIFF_BIG` では、ユーザー定義変数に相当するものは受け入れられません。 この表には、有効な *datepart* 引数をすべて一覧表示しています。

> [!NOTE]
> `DATEDIFF_BIG` は、*datepart* 引数に関して、ユーザー定義変数に相当するものは受け入れられません。
  
|*datepart*|省略形|  
|---|---|
|**year**|**yy、yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy、y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi、n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
次のいずれかの値に解決できる式。

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

*date* の場合、`DATEDIFF_BIG` では、列式、式、文字列リテラル、ユーザー定義の変数が受け入れられます。 文字列リテラル値は **datetime** に解決する必要があります。 あいまいさの問題を排除するために、4 桁の西暦を使用してください。 `DATEDIFF_BIG` では、*enddate* から *startdate* が減算されます。 こうしたあいまいさを排除するため、4 桁の西暦を使用してください。 2 桁の西暦については、「[two digit year cutoff サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)」を参照してください。
  
*enddate*  
「*startdate*」をご覧ください。
  
## <a name="return-type"></a>戻り値の型  

符号付き **bigint**  
  
## <a name="return-value"></a>戻り値  
startdate と enddate で指定された 2 つの日付間の差を、指定された datepart 境界の数で (符号付き多倍長整数値として) 返します。
-   特定の各 *datepart* と、その *datepart* の省略形では、同じ値が返されます。  
  
**bigint** の範囲外の戻り値 (-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807) の場合、`DATEDIFF_BIG` はエラーを返します。 **millisecond** の場合、*enddate* と *startdate* の差の最大値は 24 日 20 時間 31 分 23.647 秒です。 **second** の場合、差の最大値は 68 年です。
  
*startdate* と *enddate* の両方に時刻値のみが割り当てられており、*datepart* が時刻の *datepart* でない場合、`DATEDIFF_BIG` は 0 を返します。
  
`DATEDIFF_BIG` では、戻り値を計算する際に、*startdate* または *enddate* のタイム ゾーン オフセット要素を使用しません。
  
[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) の精度は分単位までなので、*startdate* または *enddate* に **smalldatetime** 値を使用した場合、`DATEDIFF_BIG` では、戻り値で秒とミリ秒が常に 0 に設定されます。
  
日付データ型の変数に時刻値のみが割り当てられている場合、`DATEDIFF_BIG` では、欠落している日付要素の値が既定値である 1900-01-01 に設定されます。 時刻データ型または日付データ型の変数に日付値のみが割り当てられている場合、`DATEDIFF_BIG` では、欠落している時刻要素の値が既定値である 00:00:00 に設定されます。 *startdate* または *enddate* のいずれか一方が時刻要素のみで、もう一方が日付要素のみであった場合、`DATEDIFF_BIG` では、欠落している時刻要素と日付要素がそれぞれの既定値に設定されます。
  
*startdate* と *enddate* で異なる日付データ型が使用されており、一方の時刻要素の数または秒の小数部の有効桁数が、もう一方のデータ型を超えている場合、`DATEDIFF_BIG` では、欠落している要素が 0 に設定されます。
  
## <a name="datepart-boundaries"></a>datepart の差
次の各ステートメントには、すべて同じ *startdate* と *enddate* の値が指定されています。 これらの日付は隣接しており、時間的な差は .0000001 秒です。 各ステートメントにおける *startdate* と *enddate* の差は、どの要素をとっても、*datepart* の 1 単位分となるように配慮されています。 いずれのステートメントも戻り値は 1 です。 *startdate* と *enddate* の年の値は異なるが、カレンダー週の値が同じである場合、`DATEDIFF_BIG` では、*datepart* **week** に対して 0 を返します。

```sql
SELECT DATEDIFF_BIG(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
`DATEDIFF_BIG` は、SELECT <list>、WHERE、HAVING、GROUP BY、および ORDER BY 句で使用します。
  
`DATEDIFF_BIG` は、文字列リテラルを **datetime2** 型として暗黙的にキャストします。 つまり、`DATEDIFF_BIG` では、日付が文字列として渡される場合、YDM 形式がサポートされません。 文字列を明示的にキャストする必要があります、 **datetime** または **smalldatetime** YDM 形式を使用する型。
  
SET DATEFIRST を指定しても `DATEDIFF_BIG` に影響はありません。 `DATEDIFF_BIG` では、週の最初の曜日として常に日曜日を使用し、関数が決定的な方法で動作するようにします。
  
## <a name="examples"></a>使用例 
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>startdate と enddate に列を指定する  
この例では、*startdate* パラメーターと *enddate* パラメーターの引数として、各種の式を使用しています。 テーブルの 2 つの列に日付を格納し、両者の差を日単位で計算しています。
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF_BIG(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  

より密接に関連する例については、「[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)」を参照してください。
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
