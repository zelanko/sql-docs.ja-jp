---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6c0cfefde5609455f53d2afcb33659cd5c1d99bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

*startdate* と *enddate* で指定された 2 つの日付間の差を、指定された *datepart* 境界の数 (符号付き多倍長整数) で返します。
  
すべての概要については [!INCLUDE[tsql](../../includes/tsql-md.md)] 日付と時刻のデータ型および関数、を参照してください。[ 日付と時刻のデータ型および関数と #40 です。TRANSACT-SQL と #41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>引数  
*datepart*  
*startdate* と *enddate* の差を求めるときの単位に使用する要素を指定します。 次の表に一覧のすべての有効な *datepart* 引数。 ユーザー定義変数に相当するものは無効です。
  
|*datepart*|省略形|  
|---|---|
|**year**|**yy、yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy、y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**mm**|  
|**minute**|**mi、n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
**time**、**date**、**smalldatetime**、**datetime**、**datetime2**、または **datetimeoffset** 値に解決できる式です。 *date* には、式、列式、ユーザー定義変数、または文字列リテラルを指定できます。 *startdate* が *enddate* から減算されます。  
こうしたあいまいさを排除するため、4 桁の西暦を使用してください。 2 桁の年については、「[two digit year cutoff サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)」をご覧ください。
  
*enddate*  
「*startdate*」をご覧ください。
  
## <a name="return-type"></a>戻り値の型  
 署名   
        **bigint**  
  
## <a name="return-value"></a>戻り値  
startdate と enddate で指定された 2 つの日付間の差を、指定された datepart 境界の数 (符号付き多倍長整数) で返します。
-   各 *datepart* とその省略形は、同じ値を返します。  
  
戻り値が **bigint** の範囲 (-9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807) を超えた場合は、エラーが返されます。 **millisecond** の場合、*startdate* と *enddate* の差の最大値は 24 日 20 時間 31 分 23.647 秒です。 **second** の場合、差の最大値は 68 年です。
  
*startdate* と *enddate* の両方に時刻値を指定したにもかかわらず、*datepart* に時刻以外の *datepart* を指定した場合、0 が返されます。
  
*startdate* または *enddate* のタイム ゾーン オフセット要素は、戻り値の計算には使用されません。
  
[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) の精度は分単位までなので、*startdate* または *enddate* に **smalldatetime** 値を使用した場合、戻り値では、秒とミリ秒が常に 0 に設定されます。
  
日付データ型の変数に時刻値だけが割り当てられた場合、欠落している日付要素の値は既定値である 1900-01-01 に設定されます。 時刻データ型または日付データ型の変数に日付値だけが割り当てられた場合、欠落している時刻要素の値は既定値である 00:00:00 に設定されます。 *startdate* または *enddate* のいずれか一方が時刻要素のみで、もう一方が日付要素のみであった場合、欠落している時刻要素と日付要素はそれぞれの既定値に設定されます。
  
*startdate* と *enddate* に対して異なる日付データ型が使用されているとき、一方の時刻要素の数または 1 秒未満の秒の有効桁数が、もう一方のデータ型を超えている場合、欠落している要素は 0 に設定されます。
  
## <a name="datepart-boundaries"></a>datepart の差
次の各ステートメントには、すべて同じ *startdate* と *enddate* が指定されています。 2 つの日付は隣接しており、時間的な差は .0000001 秒です。 各ステートメントにおける *startdate* と *enddate* の差は、どの要素をとっても、*datepart* の 1 単位分となるように配慮されています。 いずれのステートメントも戻り値は 1 です。 この例で異なる年を使用し、*startdate* と *enddate* の両方がカレンダー上の同じ週に存在した場合、**week** の戻り値は 0 になります。

```sql
SELECT DATEDIFF_BIG(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
DATEDIFF_BIG は、選択リストのほか、WHERE 句、HAVING 句、GROUP BY 句、および ORDER BY 句で使用できます。
  
DATEDIFF_BIG は、文字列リテラルを **datetime2** 型として暗黙的にキャストします。 つまり、DATEDIFF_BIG では、日付が文字列として渡される場合、YDM 形式をサポートしません。 YDM 形式を使用するには、文字列を **datetime** 型または **smalldatetime** 型に明示的にキャストする必要があります。
  
SET DATEFIRST を指定しても DATEDIFF_BIG に影響はありません。 DATEDIFF_BIG では、週の最初の曜日として常に日曜日を使用し、関数が決定的であることを確認します。
  
## <a name="examples"></a>使用例  
次の例では、*startdate* パラメーターと *enddate* パラメーターの引数として各種の式を使用しています。
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>startdate と enddate に列を指定する  
次の例では、テーブルの 2 つの列に日付を格納し、両者の差を日単位で計算しています。
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF_BIG(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
その他のれいについては、「[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)」の密接に関連する例をご覧ください。
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
