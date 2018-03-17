---
title: DAY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/30/2017
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
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 444df60a2cfe3adae045020b3db8d673946dccb1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定した日 (月の日) を表す整数を返します *日付*です。
  
すべての概要については [!INCLUDE[tsql](../../includes/tsql-md.md)] [日付と時刻のデータ型および関数、を参照してください。 日付と時刻のデータ型および関数と #40 です。TRANSACT-SQL と #41;.](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>引数  
*date*  
**time**、**date**、**smalldatetime**、**datetime**、**datetime2**、または **datetimeoffset** の値に解決できる式です。  *日付* 引数は、式、列式、ユーザー定義変数、または文字列リテラルを指定できます。
  
## <a name="return-type"></a>戻り値の型  
**int**
  
## <a name="return-value"></a>戻り値  
* * 1 日には、同じの値が返されます [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**日**、*日付*など)。 * *。
  
*日付*に時刻部分のみが含まれている場合、戻り値は 1、基本の日です。
  
## <a name="examples"></a>使用例  
次のステートメントでは、`30` が返されます。 これは、日を表す値です。
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
次のステートメントでは、`1900, 1, 1` が返されます。 引数 *日付* 番号 0です`0`。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、`0` を 1900 年 1 月 1 日と解釈します。
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


