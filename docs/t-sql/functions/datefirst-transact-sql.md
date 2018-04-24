---
title: '@@DATEFIRST (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9cfe88d34f7a193661723b50a8e5870c6365ce77
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="x40x40datefirst-transact-sql"></a>&#x40;&#x40;DATEFIRST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

セッションにおける、[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md) の現在の値を返します。
  
すべての概要については [!INCLUDE[tsql](../../includes/tsql-md.md)] 日付と時刻のデータ型および関数、を参照してください。[ 日付と時刻のデータ型および関数と #40 です。TRANSACT-SQL と #41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
@@DATEFIRST  
```  
  
## <a name="return-type"></a>戻り値の型  
**tinyint**
  
## <a name="remarks"></a>Remarks  
SET DATEFIRST は、週の最初の曜日を指定します。 言語設定がは 7 の日曜日です。
  
この言語設定は、文字列をデータベース格納用の日付値に変換する際の解釈のほか、データベースに格納される日付値の表示に影響します。 この設定は、日付データのストレージ形式には影響しません。 次の例では、最初に言語を `Italian` に設定します。 `SELECT @@DATEFIRST;` ステートメントからは `1` が返されます。 次に、言語を `us_english` に設定します。 `SELECT @@DATEFIRST;` ステートメントからは `7` が返されます。
  
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
次の例では、週の最初の曜日を `5` (金曜) に設定します。現在の曜日 `Today` は土曜と仮定します。 `SELECT` ステートメントでは、`DATEFIRST` の値と現在の曜日を示す数値が返されます。
  
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
 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT @@DATEFIRST;  
```  
  
## <a name="see-also"></a>参照
[構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)
  
  

