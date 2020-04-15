---
title: C 間隔構造 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c86ebe24a0e12531e355f95185b01f3089a31b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292154"
---
# <a name="c-interval-structure"></a>C Interval 構造体
「C データ・タイプ」セクションにリストされている各 C インターバル[・データ・タイプ](../../../odbc/reference/appendixes/c-data-types.md)は、同じ構造を使用して間隔データを格納します。 **SQLFetch** **、SQLFetchScroll、** または**SQLGetData**が呼び出されると、ドライバーはSQL_INTERVAL_STRUCT構造体にデータを返し、アプリケーションで指定された値を使用して C データ型 **(SQLBindCol、SQLGetData、** または**SQLBindParameter**の呼び出し) を使用して、SQL_INTERVAL_STRUCTの内容を解釈し、構造体の*interval_type*フィールドに C 型に対応する*列挙*型の値を設定します。 **SQLGetData** ドライバーは、間隔の種類を決定する*interval_type*フィールドを読み取りません。SQL_DESC_CONCISE_TYPE記述子フィールドの値を取得します。 構造体をパラメーター データに使用する場合、ドライバーは、アプリケーションが別の値*にinterval_type*フィールドの値を設定する場合でも、SQL_INTERVAL_STRUCTの内容を解釈するのに、APD のSQL_DESC_CONCISE_TYPEフィールドでアプリケーションによって指定された値を使用します。  
  
 この構造体は、次のように定義されます。  
  
```  
typedef struct tagSQL_INTERVAL_STRUCT  
{  
   SQLINTERVAL interval_type;   
   SQLSMALLINT interval_sign;  
   union {  
         SQL_YEAR_MONTH_STRUCT   year_month;  
         SQL_DAY_SECOND_STRUCT   day_second;  
         } intval;  
} SQL_INTERVAL_STRUCT;  
typedef enum   
{  
   SQL_IS_YEAR = 1,  
   SQL_IS_MONTH = 2,  
   SQL_IS_DAY = 3,  
   SQL_IS_HOUR = 4,  
   SQL_IS_MINUTE = 5,  
   SQL_IS_SECOND = 6,  
   SQL_IS_YEAR_TO_MONTH = 7,  
   SQL_IS_DAY_TO_HOUR = 8,  
   SQL_IS_DAY_TO_MINUTE = 9,  
   SQL_IS_DAY_TO_SECOND = 10,  
   SQL_IS_HOUR_TO_MINUTE = 11,  
   SQL_IS_HOUR_TO_SECOND = 12,  
   SQL_IS_MINUTE_TO_SECOND = 13  
} SQLINTERVAL;  
  
typedef struct tagSQL_YEAR_MONTH  
{  
   SQLUINTEGER year;  
   SQLUINTEGER month;   
} SQL_YEAR_MONTH_STRUCT;  
  
typedef struct tagSQL_DAY_SECOND  
{  
   SQLUINTEGER day;  
   SQLUINTEGER hour;  
   SQLUINTEGER minute;  
   SQLUINTEGER second;  
   SQLUINTEGER fraction;  
} SQL_DAY_SECOND_STRUCT;  
```  
  
 SQL_INTERVAL_STRUCTの*interval_type*フィールドは、共用体に保持されている構造と、その構造体のメンバーが関連付けされているかをアプリケーションに示します。 *interval_sign*フィールドは、間隔の先行フィールドが符号なしの場合にSQL_FALSE値を持ちます。SQL_TRUE場合、先頭フィールドは負の値になります。 先行フィールド自体の値は *、interval_sign*の値に関係なく、常に符号なしです。 *interval_sign*フィールドは符号ビットとして機能します。
