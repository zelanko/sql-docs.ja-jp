---
title: "TRY_CONVERT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs: TSQL
helpviewer_keywords: TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 98f60a6a46fbbce2bd4b1bac16d0a7c8edc69361
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  キャストが成功した場合は、指定したデータ型にキャストされた値を返します。それ以外の場合は null を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>引数  
 *data_type [(長さ)]*  
 データ型をキャストする*式*です。  
  
 *式 (expression)*  
 キャストされる値。  
  
 *スタイル*  
 省略可能な整数式を指定する方法、 **TRY_CONVERT**関数は、変換する*式*です。  
  
 *スタイル*として同じ値を受け取り、*スタイル*のパラメーター、**変換**関数。 詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)」を参照してください。  
  
 値の許容範囲の値によって決まります*data_type*です。 場合*スタイル*が null の場合、 **TRY_CONVERT**は null を返します。  
  
## <a name="return-types"></a>戻り値の型  
 キャストが成功した場合は、指定したデータ型にキャストされた値を返します。それ以外の場合は null を返します。  
  
## <a name="remarks"></a>解説  
 **TRY_CONVERT**に渡される値を取得し、指定された変換しようとしています。 *data_type*です。 キャストが成功すると、 **TRY_CONVERT** 、指定された値を返します*data_type*以外の場合はエラーが発生する場合は null が返されます。 ただしかどうかは、明示的に許可されていない、変換を要求する**TRY_CONVERT**はエラーで失敗します。  
  
 **TRY_CONVERT**は予約されたキーワードで互換性レベル 110 以上です。  
  
 この関数は、のバージョンがサーバーに対してリモート処理することのできる[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] より前のバージョンをインストールしているサーバーには、リモート処理が行われません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT は null を返します。  
 次の例では、キャストに失敗すると TRY_CONVERT は null を返します。  
  
```tsql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 次の例は、式を求められている形式にする必要があることを示しています。  
  
```tsql  
SET DATEFORMAT dmy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>B. TRY_CONVERT でエラーが発生して失敗する  
 次の例では、キャストが明示的に許可されていない場合に TRY_CONVERT がエラーを返すことを示します。  
  
```tsql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 このステートメントの結果はエラーです。整数を xml データ型にキャストすることはできないからです。  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>C. TRY_CONVERT が成功する  
 この例では、式が必要な形式にする必要がありますを示します。  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
