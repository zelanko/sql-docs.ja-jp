---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/29/2017
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
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1c8a5f8bea3bf6ca97e0f7b4a35f8f78315716df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

返します、 **datetimeoffset** 指定されたオフセットおよび有効桁数と指定した日付と時刻の値です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
```  
  
## <a name="arguments"></a>引数  
*year*  
年を指定する整数式。
  
*month*  
月を指定する整数式。
  
*day*  
日を指定する整数式。
  
*hour*  
時間を指定する整数式。
  
*minute*  
分を指定する整数式。
  
*seconds*  
秒を指定する整数式。
  
*fractions*  
小数部分を指定する整数式。
  
*hour_offset*  
タイム ゾーン オフセットの時間部分を指定する整数式。
  
*minute_offset*  
タイム ゾーン オフセットの分部分を指定する整数式。
  
*有効桁数 (precision)*  
返される **datetimeoffset** 値の有効桁数を指定する整数リテラル。
  
## <a name="return-types"></a>戻り値の型
**datetimeoffset(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
**DATETIMEOFFSETFROMPARTS** 返しますが、完全に初期化された **datetimeoffset** データ型。 オフセットの引数は、タイム ゾーン オフセットを表すために使用します。 オフセット引数を省略した場合、タイム ゾーン オフセットは 00:00 と見なされ、タイム ゾーン オフセットはありません。 オフセット引数を指定する場合、両方の引数が存在し、両方とも正または負である必要があります。 場合 *minute_offset* なしで指定された *hour_offset*, 、エラーが発生します。 他の引数が有効でない場合は、エラーが発生します。 必要な引数が NULL の場合は、NULL が返されます。 ただし場合、 *有効桁数* 引数が null の場合、エラーが発生します。
  
*分数* 引数によって異なります、 *有効桁数 引数*。 たとえば、*precision* が 7 の場合、小数部分はそれぞれ 100 ナノ秒を表します。*precision* が 3 の場合、小数部分はそれぞれ 1 ミリ秒を表します。 場合の値 *有効桁数* が 0 の場合、値の *分数* もする必要があります。 0 にするそれ以外の場合、エラーが発生します。
  
この関数は、リモート処理は実行することのできる [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバー上とします。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前のバージョンをインストールしているサーバーには、リモート処理が行われません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. 秒の小数部を使用しない場合の簡単な例  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. 秒の小数部を使用する場合の例  
以下の例は、*fractions* パラメーターと *precision* パラメーターの使用方法を示しています。
1.   ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
1.   ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
1.   ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


