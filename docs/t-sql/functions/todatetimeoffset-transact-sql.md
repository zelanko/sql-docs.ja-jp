---
title: "TODATETIMEOFFSET (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77d42b2484563d162d78e1caad28389cc26f6cee
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返します、 **datetimeoffset**から変換された値、 **datetime2**式。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)に解決される、 [datetime2](../../t-sql/data-types/datetime2-transact-sql.md)値。  
  
> [!NOTE]  
>  式を型にすることはできません**テキスト**、 **ntext**、または**イメージ**に、これらの型を暗黙的に変換できないため**varchar**または**nvarchar**です。  
  
 *time_zone*  
 タイム ゾーン オフセットを表す式です。たとえば、分単位で表す式 (整数の場合) は -120、時間と分単位で表す式 (文字列の場合) は '+13.00' です。 範囲は +14 ～ -14 (時間) です。 式は、指定された time_zone のローカル時刻で解釈されます。  
  
> [!NOTE]  
>  式が文字列の場合、{+|-}TZH:THM の形式にする必要があります。  
  
## <a name="return-type"></a>戻り値の型  
 **datetimeoffset**です。 小数部の有効桁数が同じ、 *datetime*引数。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. 現在の日付と時刻のタイム ゾーン オフセットを変更する  
 次の例は、現在の日付と時刻にタイム ゾーンのゾーン オフセットを変更`-07:00`です。  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>B. タイム ゾーン オフセットを分単位で変更する  
 次の例には、現在のタイム ゾーンを変更する`-120`分です。  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>C. 13 時間のタイム ゾーン オフセットを追加する  
 次の例では、日付と時刻に 13 時間のタイム ゾーン オフセットを追加します。  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-changing-the-time-zone-offset-of-the-current-date-and-time"></a>D. 現在の日付と時刻のタイム ゾーン オフセットを変更する  
 次の例は、現在の日付と時刻にタイム ゾーンのゾーン オフセットを変更`-07:00`です。  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="e-changing-the-time-zone-offset-in-minutes"></a>E. タイム ゾーン オフセットを分単位で変更する  
 次の例には、現在のタイム ゾーンを変更する`-120`分です。  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="f-adding-a-13-hour-time-zone-offset"></a>F. 13 時間のタイム ゾーン オフセットを追加する  
 次の例では、日付と時刻に 13 時間のタイム ゾーン オフセットを追加します。  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [日付および時刻データ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [タイム ゾーンと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


