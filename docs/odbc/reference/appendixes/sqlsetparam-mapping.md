---
title: マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d8e632412965664e5cdd9c87dc1e26787dcdab2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300532"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam のマッピング
**SQLSetParam**は、ODBC 2 のように **、SQLBind パラメータ**の上にマップされ続けます。*x .* 概念的には**SQLBind パラム**に似ていますが、ドライバー マネージャーは**SQLSetParam を SQLBindParam**にマップしません。 **SQLBindParam** これは、ある既存の ODBC 2 が原因です。*x*ドライバーは、ドライバー マネージャーが**SQLBindParameter**の上に**SQLSetParam**をマップするときに生成する*バッファー長*(SQL_SETPARAM_VALUE_MAX) の特別な値を使用して、それが呼び出されたときに決定する、 1。*x* ODBC アプリケーション。  
  
 への呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次のような結果になります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
