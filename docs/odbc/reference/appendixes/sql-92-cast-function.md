---
title: SQL-92 キャスト機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d2a2de710dafd4e744166c4219f4c903fd3321
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305063"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST 関数
SQL-92 で定義された**CAST**関数は、ODBC で定義されている**変換**関数と同じです。 同等の関数の構文は次のとおりです。  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 SQL-92 **CAST**関数は、どのデータ型を他のデータ型に変換できるかを指定します。 (詳細については、SQL-92 仕様を参照してください。**CAST**関数は、FIPS 移行レベルでサポートされています。  
  
 アプリケーションは、次のように**CAST**関数のサポートを決定できます。  
  
1.  SQL_SQL_CONFORMANCE情報の種類を指定して**SQLGetInfo**を呼び出します。 情報型の戻り値がSQL_SC_FIPS127_2_TRANSITIONAL、SQL_SC_SQL92_INTERMEDIATE、またはSQL_SC_SQL92_FULLの場合 **、CAST**関数がサポートされます。  
  
2.  SQL_SQL_CONFORMANCE情報の型の戻り値がSQL_SC_ENTRY_LEVELまたは 0 の場合は、SQL_SQL92_VALUE_EXPRESSIONS情報の種類を指定して**SQLGetInfo**を呼び出します。 SQL_SVE_CASTビットが設定されている場合 **、CAST**関数がサポートされます。
