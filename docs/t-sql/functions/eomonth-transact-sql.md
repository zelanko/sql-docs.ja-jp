---
title: "EOMONTH (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EOMONTH
- EOMONTH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EOMONTH function
ms.assetid: 1d060d8e-3297-4244-afef-57df2f8f92e2
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: a4356c6472b5757374909ae0350d597a91e4252d
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="eomonth-transact-sql"></a>EOMONTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  オプションのオフセットを使用して、指定された日付を含んでいる月の最後の日付を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
EOMONTH ( start_date [, month_to_add ] )  
```  
  
## <a name="arguments"></a>引数  
 *start_date*  
 月の最終日を返す日付を指定する日付の式。  
  
 *month_to_add*  
 追加する月数を指定する省略可能な整数式*start_date*です。  
  
 この引数が指定されている場合、し**EOMONTH**に指定された月数を追加*start_date*、し、結果として得られる日付の月の最終日を返します。 この整数式を追加したことによって有効な日付範囲をオーバーフローすると、エラーが発生します。  
  
## <a name="return-type"></a>戻り値の型  
 **date**  
  
## <a name="remarks"></a>解説  
 この関数は、リモート処理は実行[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]サーバー以上です。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] より前のバージョンのサーバーには、リモート処理は実行できません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-eomonth-with-explicit-datetime-type"></a>A. 明示的な datetime 型を使用する EOMONTH  
  
```  
DECLARE @date DATETIME = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  
  
### <a name="b-eomonth-with-string-parameter-and-implicit-conversion"></a>B. 文字列パラメーターと暗黙的な変換を使用する EOMONTH  
  
```  
DECLARE @date VARCHAR(255) = '12/1/2011';  
SELECT EOMONTH ( @date ) AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
2011-12-31  
  
(1 row(s) affected)  
```  
  
### <a name="c-eomonth-with-and-without-the-monthtoadd-parameter"></a>C. month_to_add パラメーターを使用する EOMONTH と使用しない EOMONTH  
  
```tsql  
DECLARE @date DATETIME = GETDATE();  
SELECT EOMONTH ( @date ) AS 'This Month';  
SELECT EOMONTH ( @date, 1 ) AS 'Next Month';  
SELECT EOMONTH ( @date, -1 ) AS 'Last Month';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
This Month  
-----------------------  
2011-12-31  
  
(1 row(s) affected)  
  
Next Month  
-----------------------  
2012-01-31  
  
(1 row(s) affected)  
  
Last Month  
-----------------------  
2011-11-30  
  
(1 row(s) affected)  
```  
  
  


