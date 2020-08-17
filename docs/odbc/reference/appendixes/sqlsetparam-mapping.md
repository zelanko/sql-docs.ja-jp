---
description: SQLSetParam のマッピング
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c16f942920b5fefff664cc647f4edfc9ab6d13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339298"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam のマッピング
**SQLSetParam** は、ODBC 2 の場合と同様に、 **SQLBindParameter** の上で引き続きマップされます。*x*。 概念的には **SQLBindParam**と似ていますが、ドライバーマネージャーは **SQLSetParam** を **SQLBindParam**にマップしません。 これは、特定の既存の ODBC 2 が原因です。*x*ドライバーは、 **SQLBindParameter**の上に**SQLSetParam**をマップするときにドライバーマネージャーによって生成される*bufferlength* (SQL_SETPARAM_VALUE_MAX) の特殊な値を使用して、1によっていつ呼び出されるかを判断します。*x* ODBC アプリケーション。  
  
 の呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次のようになります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
