---
title: "月 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- MONTH_TSQL
- MONTH
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], date and time
- dates [SQL Server], functions
- month of year [SQL Server]
- date and time [SQL Server], MONTH
- dateparts [SQL Server], month
- functions [SQL Server], date and time
- dates [SQL Server], MONTH
- MONTH function [SQL Server]
ms.assetid: 9dd8aff7-b0fc-45df-b316-ead14ee9b8b7
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f3f25d694d7d9757b09d834e9844aad2b2defb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="month-transact-sql"></a>MONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した月を表す整数を返します*日付*です。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
MONTH ( date )  
```  
  
## <a name="arguments"></a>引数  
 *date*  
 式に解決されることができるは、**時間**、**日付**、 **smalldatetime**、 **datetime**、 **datetime2**、または**datetimeoffset**値。 *日付*引数は、式、列式、ユーザー定義変数またはリテラル文字列を指定できます。  
  
## <a name="return-type"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 月と同じ値を返します[DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**月**、*日付*)。  
  
 場合*日付*時刻の部分では、戻り値は 1、基本の月だけが含まれています。  
  
## <a name="examples"></a>使用例  
 次のステートメントから`4`です。 これは、月を表す値です。  
  
```  
SELECT MONTH('2007-04-30T01:01:01.1234567 -07:00');  
```  
  
 次のステートメントから`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例を返します`4`です。 これは、月を表す値です。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 MONTH('2007-04-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
 次の例を返します`1900, 1, 1`です。 引数*日付*番号`0`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解釈`0`1900 年 1 月 1 日とします。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


