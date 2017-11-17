---
title: "年 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- YEAR
- YEAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server], years
- date and time [SQL Server], YEAR
- functions [SQL Server], date and time
- YEAR function [SQL Server]
- dateparts [SQL Server], year
ms.assetid: 74aa7ccc-8575-4018-80cf-14aeca379687
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 80a38599ae04209d0f8e479b8cbad16d39bef31a
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="year-transact-sql"></a>YEAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した年を表す整数を返します*日付*です。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
YEAR ( date )  
```  
  
## <a name="arguments"></a>引数  
 *date*  
 式に解決されることができるは、**時間**、**日付**、 **smalldatetime**、 **datetime**、 **datetime2**、または**datetimeoffset**値。 *日付*引数は、式、列式、ユーザー定義変数またはリテラル文字列を指定できます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 年と同じ値を返します[DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**年**、*日付*)。  
  
 場合*日付*のみに時刻部分が含まれています、戻り値は基準年を 1900 年です。  
  
## <a name="examples"></a>使用例  
 次のステートメントから`2010`です。 これは、年を表す値です。  
  
```  
SELECT YEAR('2010-04-30T01:01:01.1234567-07:00');  
```  
  
 次のステートメントから`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次のステートメントから`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。  
  
```  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


