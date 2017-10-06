---
title: "GETDATE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GETDATE_TSQL
- GETDATE
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- GETDATE function [SQL Server]
- current date and time [SQL Server]
- time [SQL Server], current
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- date and time [SQL Server], GETDATE
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: bebe3b65-2b3e-4c73-bf80-ff1132c680a7
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1c0cf660d5240e6a5222c44334f31f0beb94a749
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getdate-transact-sql"></a>GETDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベース システムのタイムスタンプを返します、 **datetime**データベース タイム ゾーン オフセットを持たない値。 この値は、コンピューターのオペレーティング システムから派生したインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されています。  
  
> [!NOTE]  
>  1 秒未満の有効桁数で比較すると、SYSDATETIME と SYSUTCDATETIME の方が GETDATE と GETUTCDATE よりも高い精度を得ることができます。 SYSDATETIMEOFFSET には、システムのタイム ゾーン オフセットが含まれます。 SYSDATETIME、SYSUTCDATETIME、および SYSDATETIMEOFFSET は、date 型と time 型の任意の変数に割り当てることができます。  
  
 すべての概要については[!INCLUDE[tsql](../../includes/tsql-md.md)]日付と時刻のデータ型および関数を参照してください[日付と時刻のデータ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GETDATE ( )  
```  
  
## <a name="return-type"></a>戻り値の型  
 **datetime**  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを参照できる GETDATE を参照できる任意の場所、 **datetime**式。  
  
 GETDATE は、非決定的関数です。 この関数を列内で参照するビューと式には、インデックスを付けることができません。  
  
 GETDATE() 関数で SWITCHOFFSET を使用すると、クエリの実行速度が低下する場合があります。クエリ オプティマイザーでは、GETDATE 値の正確な基数の推定を取得できないためです。 GETDATE 値を事前計算して、次の例に示すように、クエリでその値を指定することをお勧めします。 さらに、OPTION (RECOMPILE) クエリ ヒントを使用して、クエリ オプティマイザーが、次回同じクエリが実行されるクエリ プランを再コンパイルするようにします。 そうすると、オプティマイザーは、GETDATE() の正確な基数の推定を取得し、より効率的なクエリ プランを生成します。  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>使用例  
 次の例は、6 つを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返す現在の日付と時刻を日付、時刻、またはその両方を返すシステム関数です。 値は順番に返されるため、秒の小数部が異なる可能性があります。  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. 現在のシステム日付と時刻を取得する  
  
```  
SELECT SYSDATETIME()  
    ,SYSDATETIMEOFFSET()  
    ,SYSUTCDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE()  
    ,GETUTCDATE();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `SYSDATETIME()      2007-04-30 13:10:02.0474381`  
  
 `SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00`  
  
 `SYSUTCDATETIME()   2007-04-30 20:10:02.0474381`  
  
 `CURRENT_TIMESTAMP  2007-04-30 13:10:02.047`  
  
 `GETDATE()          2007-04-30 13:10:02.047`  
  
 `GETUTCDATE()       2007-04-30 20:10:02.047`  
  
### <a name="b-getting-the-current-system-date"></a>B. 現在のシステム日付を取得する  
  
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
SYSDATETIME()          2007-05-03  
SYSDATETIMEOFFSET()    2007-05-03  
SYSUTCDATETIME()       2007-05-04  
CURRENT_TIMESTAMP      2007-05-03  
GETDATE()              2007-05-03  
GETUTCDATE()           2007-05-04
``` 
  
### <a name="c-getting-the-current-system-time"></a>C. 現在のシステム時刻を取得する  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, SYSDATETIMEOFFSET())  
    ,CONVERT (time, SYSUTCDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE())  
    ,CONVERT (time, GETUTCDATE());  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
SYSDATETIME()      13:18:45.3490361  
SYSDATETIMEOFFSET()13:18:45.3490361  
SYSUTCDATETIME()   20:18:45.3490361  
CURRENT_TIMESTAMP  13:18:45.3470000  
GETDATE()          13:18:45.3470000  
GETUTCDATE()       20:18:45.3470000  
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、3 つを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返す現在の日付と時刻を日付、時刻、またはその両方を返すシステム関数です。 値は順番に返されるため、秒の小数部が異なる可能性があります。  
  
### <a name="d-getting-the-current-system-date-and-time"></a>D. 現在のシステム日付と時刻を取得する  
  
```  
SELECT SYSDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE();  
```  
  
### <a name="e-getting-the-current-system-date"></a>E. 現在のシステム日付を取得する  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE());  
  
```  
  
### <a name="f-getting-the-current-system-time"></a>F. 現在のシステム時刻を取得する  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE());  
  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


