---
title: "SYSUTCDATETIME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/01/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSUTCDATETIME
- SYSUTCDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- date and time [SQL Server], SYSUTCDATETIME
- SYSUTCDATETIME function [SQL Server]
- time [SQL Server], system
ms.assetid: f14fc2cd-9ea8-4daf-88f4-418cf523ab55
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b01ce3327bbedb114df93e89fb7c5ee94f5ec58a
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="sysutcdatetime-transact-sql"></a>SYSUTCDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返します、 **datetime2**いるコンピューターの日時を表す値のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 日付と時刻が UTC 時刻 (世界協定時刻) として返されます。 秒の小数部の有効桁数は 1 ～ 7 桁の範囲で指定できます。 既定の有効桁数は 7 桁です。  
  
> [!NOTE]  
>  1 秒未満の有効桁数で比較すると、SYSDATETIME と SYSUTCDATE の方が GETDATE と GETUTCDATE よりも高い精度を得ることができます。 SYSDATETIMEOFFSET には、システムのタイム ゾーン オフセットが含まれます。 SYSDATETIME、SYSUTCDATE、および SYSDATETIMEOFFSET は、日付と時刻型のいずれかの変数に割り当てることができます。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SYSUTCDATETIME ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **datetime2**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを参照できる SYSUTCDATETIME を参照できる任意の場所、 **datetime2**式。  
  
 SYSUTCDATETIME は非決定的関数です。 この関数を列内で参照するビューと式には、インデックスを付けることができません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]GetSystemTimeAsFileTime() Windows API を使用して日付と時刻の値を取得します。 精度は、コンピューターのハードウェアとする Windows のバージョンによって異なります。 のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。 この API の精度は 100 ナノ秒で固定されます。 GetSystemTimeAdjustment() Windows API を使用して、精度を確認できます。  
  
## <a name="examples"></a>使用例  
 次の例は、6 つを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返す現在の日付と時刻を日付、時刻、またはその両方を返すシステム関数です。 値は順番に返されるため、秒の小数部が異なる可能性があります。  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>A. 日付および時刻の関数から返される形式を表示する  
 次の例では、日付と時刻の関数によって返されるさまざまな形式を表示します。  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    ,SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    ,SYSUTCDATETIME() AS SYSUTCDATETIME  
    ,CURRENT_TIMESTAMP AS CURRENT_TIMESTAMP  
    ,GETDATE() AS GETDATE  
    ,GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="b-converting-date-and-time-to-date"></a>B. 日付と時刻を日付に変換する  
 次の例は、日付と時刻の値に変換する方法を示します`date`です。  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="c-converting-date-and-time-values-to-time"></a>C. 日付と時刻の値を時刻に変換する  
 次の例は、日付と時刻の値に変換する方法を示します`time`です。  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [日付および時刻データ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [タイム ゾーンと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



