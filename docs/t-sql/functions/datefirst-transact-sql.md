---
title: "@@DATEFIRST (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATE_FORMAT_TSQL
- DATE FORMAT
- '@@DATEFIRST_TSQL'
- '@@DATEFIRST'
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SET DATEFIRST
- first day of week [SQL Server]
- dates [SQL Server], first day of week
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- date and time [SQL Server], DATEFIRST
- DATEFIRST option [SQL Server]
- date and time [SQL Server], @@DATEFIRST
- weekdays [SQL Server]
- '@@DATEFIRST function [SQL Server]'
- functions [SQL Server], date and time
- options [SQL Server], date
ms.assetid: a178868e-49d5-4bd5-a5e2-1283409c8ce6
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 951628293157784f522a262a1017b5b8b7f4bd83
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="datefirst-transact-sql"></a>@@DATEFIRST (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

セッションは、現在の値を返します[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)です。
  
すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@DATEFIRST  
```  
  
## <a name="return-type"></a>戻り値の型  
**tinyint**
  
## <a name="remarks"></a>解説  
SET DATEFIRST は、週の最初の曜日を指定します。 言語設定がは 7 の日曜日です。
  
この言語設定は、文字列をデータベース格納用の日付値に変換する際の解釈のほか、データベースに格納される日付値の表示に影響します。 この設定は、日付データのストレージ形式には影響しません。 次の例では、最初に言語を `Italian` に設定します。 ステートメント`SELECT @@DATEFIRST;`返します`1`です。 言語に設定し、`us_english`です。 ステートメント`SELECT @@DATEFIRST;`返します`7`です。
  
```sql
SET LANGUAGE Italian;  
GO  
SELECT @@DATEFIRST;  
GO  
SET LANGUAGE us_english;  
GO  
SELECT @@DATEFIRST;  
```  
  
## <a name="examples"></a>使用例  
次の例を週の最初の日を設定する`5`(金曜)、現在の日付を前提としています`Today`, は土曜します。 `SELECT` ステートメントでは、`DATEFIRST` の値と現在の曜日を示す数値が返されます。
  
```sql
SET DATEFIRST 5;  
SELECT @@DATEFIRST AS 'First Day'  
    ,DATEPART(dw, SYSDATETIME()) AS 'Today';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
First Day         Today  
----------------  --------------  
5                 2  
```  
  
## <a name="example"></a>例
 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]そして[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT @@DATEFIRST;  
```  
  
## <a name="see-also"></a>参照
[構成関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/configuration-functions-transact-sql.md)
  
  


