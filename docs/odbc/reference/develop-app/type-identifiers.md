---
title: 型識別子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a274a19eaa0a2fdf98bcaa9ef42406ee8a6b6461
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306433"
---
# <a name="type-identifiers"></a>型識別子
SQL および C のデータ型を記述するために、ODBC は 2 組の*型識別子 を定義します*。 型識別子は、SQL 列または C バッファーの型を表します。 これは **#define**値であり、通常は関数引数として渡されるか、メタデータに返されます。  
  
 たとえば、次の**SQLBindParameter**呼び出しでは、SQL_DATE_STRUCT型の変数を SQL ステートメントの日付パラメーターにバインドします。 日付型の型識別子SQL_C_TYPE_DATE *Date*変数の型を指定し、動的パラメーターの型を指定SQL_TYPE_DATE SQL 型識別子を指定します。  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
