---
title: "C の間隔の構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 146e16608f0f2f790bf49a84de2ef4610df33d0f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-interval-structure"></a>C の間隔の構造体
表示される C interval データ型の[C データ型](../../../odbc/reference/appendixes/c-data-types.md)セクションでは、同じ構造を使用して、間隔のデータが含まれています。 ときに**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**が呼び出されると、ドライバー SQL_INTERVAL_STRUCT 構造にデータを返します、指定された値を使用して、C データ型のアプリケーション (への呼び出しで**SQLBindCol**、 **SQLGetData**、または**SQLBindParameter**) SQL_INTERVAL_STRUCT の内容を解釈するには、し、追加、 *interval_type*を構造体のフィールド、 *enum* C 型に対応する値。 ドライバーの読み取りを行わないことに注意してください、 *interval_type*間隔の種類を決定するフィールドです。 SQL_DESC_CONCISE_TYPE 記述子フィールドの値を取得します。 パラメーターのデータで構造体を使用すると、ドライバーを使用して APD の SQL_DESC_CONCISE_TYPE フィールドに、アプリケーションによって指定された値 SQL_INTERVAL_STRUCT の内容を解釈するアプリケーションの値を設定する場合でも、 *interval_type*を別の値フィールド。  
  
 この構造体の定義は次のとおりです。  
  
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
  
 *Interval_type*和集合にどのような構造が保持されているアプリケーションに、SQL_INTERVAL_STRUCT のフィールドを示しも構造体のメンバーは、関連します。 *Interval_sign*フィールド値 SQL_FALSE フィールドの先頭の間隔が署名されていない場合は SQL_TRUE の場合、先頭のフィールドが負の値。 先頭フィールド自体の値は、常の値に関係なく、署名付き*interval_sign*です。 *Interval_sign*フィールドは符号ビットとして機能します。

