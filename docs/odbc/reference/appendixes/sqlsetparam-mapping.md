---
title: "SQLSetParam マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: adebe26728690a6d631ca94e8ce11040ebc08a0f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam マッピング
**SQLSetParam**の上にマップする引き続き**SQLBindParameter** ODBC 2. と同様*。x*です。 概念的に似ていますなっても**SQLBindParam**、ドライバー マネージャーがマップされていない**SQLSetParam**に**SQLBindParam**です。 これは、ため特定既存の ODBC 2 です。*x*ドライバーの特殊な値を使用して*BufferLength* (SQL_SETPARAM_VALUE_MAX) に割り当てるときに、ドライバー マネージャーが生成する**SQLSetParam**の上に**SQLBindParameter**を 1 で呼び出されたときを判断します*。x* ODBC アプリケーションです。  
  
 呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次になります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
