---
title: "ISDATE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISDATETIME
- ISDATE_TSQL
- ISDATE
- ISDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], ISDATE
- validate dates times [SQL Server]
- formats [SQL Server], time
- dates [SQL Server], validate
- verify dates times [SQL Server]
- functions [SQL Server], time
- formats [SQL Server], dates
- functions [SQL Server], date and time
- time [SQL Server], functions
- time [SQL Server], validate
- ISDATE function [SQL Server]
ms.assetid: 8e2c9ee7-388a-432f-b2c9-7b398f26bf85
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e005b11ad15170dcc2f6f45441d62e6ccc29570
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="isdate-transact-sql"></a>ISDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  場合 1 を返します、*式*は有効な**日付**、**時間**、または**datetime**値。 それ以外の場合、0 です。  
  
 ISDATE は 0 を返します、*式*は、 **datetime2**値。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md). datetime データの範囲は 1753-01-01 ～ 9999-12-31、date データの範囲は 0001-01-01 ～ 9999-12-31 です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ISDATE ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 文字の文字列または[式](../../t-sql/language-elements/expressions-transact-sql.md)を文字の文字列に変換できます。 式は 4,000 文字未満にする必要があります。 datetime および smalldatetime を除く日付および時刻データ型は、ISDATE の引数として使用できません。  
  
## <a name="return-type"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 ISDATE はと共に使用する場合にのみ決定的、[変換](../../t-sql/functions/cast-and-convert-transact-sql.md)CONVERT スタイル パラメーターを指定すると、およびスタイルが 0、100、9、または 109 と等しくない場合に機能します。  
  
 ISDATE の戻り値が、設定によって異なります[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)、 [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)と[default language サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md)です。  
  
## <a name="isdate-expression-formats"></a>ISDATE 式の形式  
 ISDATE が 1 を返す有効な形式の例の「サポートされている文字列リテラル形式を datetime」セクションを参照してください、 [datetime](../../t-sql/data-types/datetime-transact-sql.md)と[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)トピックです。 その他の例も列を参照して、入力/出力の「引数」セクションの[CAST および CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md)です。  
  
 次の表は、無効な式の形式をまとめたものです。このような式を入力値として渡すと、0 またはエラーが返されます。  
  
|ISDATE 式|ISDATE 戻り値|  
|-----------------------|-------------------------|  
|NULL|0|  
|データ型の値の一覧[データ型](../../t-sql/data-types/data-types-transact-sql.md)文字の文字列、Unicode 文字列、または日付と時刻以外のデータ型カテゴリにします。|0|  
|値**テキスト**、 **ntext**、または**イメージ**データ型。|0|  
|3 を超える秒の有効桁数のスケールを持つ任意の値 (.0000 ～。 0000000... n)。 ISDATE は 0 を返します、*式*は、 **datetime2**値しますが、場合 1 を返します、*式*は有効な**datetime**値。|0|  
|有効な日付と無効な値を組み合わせた値 (1995-10-1a など)。|0|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-isdate-to-test-for-a-valid-datetime-expression"></a>A. ISDATE を使用して datetime 式が有効かどうかをテストする  
 次の例を使用する方法を示します`ISDATE`文字の文字列が有効かどうかをテストする**datetime**です。  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    PRINT 'VALID'  
ELSE  
    PRINT 'INVALID';  
```  
  
### <a name="b-showing-the-effects-of-the-set-dateformat-and-set-language-settings-on-return-values"></a>B. SET DATEFORMAT と SET LANGUAGE 設定が戻り値に与える影響を確認する  
 次のステートメントでは、`SET DATEFORMAT` および `SET LANGUAGE` の各種設定と、その結果として返される値の関係を示しています。  
  
```  
/* Use these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
/* Expression in mdy dateformat */  
SELECT ISDATE('04/15/2008'); --Returns 1.  
/* Expression in mdy dateformat */  
SELECT ISDATE('04-15-2008'); --Returns 1.   
/* Expression in mdy dateformat */  
SELECT ISDATE('04.15.2008'); --Returns 1.   
/* Expression in myd  dateformat */  
SELECT ISDATE('04/2008/15'); --Returns 1.  
  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET DATEFORMAT dmy;  
SELECT ISDATE('15/04/2008'); --Returns 1.  
SET DATEFORMAT dym;  
SELECT ISDATE('15/2008/04'); --Returns 1.  
SET DATEFORMAT ydm;  
SELECT ISDATE('2008/15/04'); --Returns 1.  
SET DATEFORMAT ymd;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET LANGUAGE English;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET LANGUAGE Hungarian;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET LANGUAGE Swedish;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET LANGUAGE Italian;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
/* Return to these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-isdate-to-test-for-a-valid-datetime-expression"></a>C. ISDATE を使用して datetime 式が有効かどうかをテストする  
 次の例を使用する方法を示します`ISDATE`文字の文字列が有効かどうかをテストする**datetime**です。  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    SELECT 'VALID';  
ELSE  
    SELECT 'INVALID';  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


