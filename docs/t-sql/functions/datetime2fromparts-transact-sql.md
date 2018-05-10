---
title: DATETIME2FROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1a6cee0f40ba7cd92024fd11b82a32c3de99d0e7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

返します、 **datetime2** 値で指定した日付と時刻の指定された有効桁数を使用します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
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
  
*minute* 分を指定する整数式。
  
*seconds*  
秒を指定する整数式。
  
*fractions*  
小数部分を指定する整数式。
  
*有効桁数 (precision)*  
返される **datetime2** 値の精度を指定する整数リテラル。
  
## <a name="return-types"></a>戻り値の型
**datetime2(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
**DATETIME2FROMPARTS** 返しますが、完全に初期化された **datetime2** 値。 引数が有効でない場合は、エラーが発生します。 必要な引数が NULL の場合は、NULL が返されます。 ただし場合、 *有効桁数* 引数が null の場合、エラーが発生します。
  
*分数* 引数によって異なります、 *有効桁数* 引数。 たとえば、*precision* が 7 の場合、小数部分はそれぞれ 100 ナノ秒を表します。*precision* が 3 の場合、小数部分はそれぞれ 1 ミリ秒を表します。 場合の値 *有効桁数* が 0 の場合、値の *分数* もする必要があります。 0 にするそれ以外の場合、エラーが発生します。
  
この関数は、リモート処理は実行することのできる [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバー上とします。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前のバージョンをインストールしているサーバーには、リモート処理が行われません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. 秒の小数部を使用しない場合の簡単な例  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. 秒の小数部を使用する場合の例  
以下の例は、*fractions* パラメーターと *precision* パラメーターの使用方法を示しています。
  
1.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
  
2.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
  
3.  ときに *分数* 5 の値を持つと *有効桁数* しの値の 1 の値を持つ *分数* 5/10 秒を表します。  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  

