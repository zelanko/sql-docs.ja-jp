---
title: SQLSetParam Mapping |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c8d2d567f899c30dfe91cd35445956cd6214da9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125552"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam のマッピング
**SQLSetParam**は、ODBC 2 の場合と同様に、 **SQLBindParameter**の上で引き続きマップされます。*x*。 概念的には**SQLBindParam**と似ていますが、ドライバーマネージャーは**SQLSetParam**を**SQLBindParam**にマップしません。 これは、特定の既存の ODBC 2 が原因です。*x*ドライバーは、 **SQLBindParameter**の上に**SQLSetParam**をマップするときにドライバーマネージャーによって生成される*bufferlength* (SQL_SETPARAM_VALUE_MAX) の特殊な値を使用して、1によっていつ呼び出されるかを判断します。*x* ODBC アプリケーション。  
  
 の呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次のようになります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
