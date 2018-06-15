---
title: SQLSetParam マッピング |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc9d81b92e83f92bb617e004c85fdbc0766de463
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907227"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam マッピング
**SQLSetParam**の上にマップする引き続き**SQLBindParameter** ODBC 2. と同様 *。x*です。 概念的に似ていますなっても**SQLBindParam**、ドライバー マネージャーがマップされていない**SQLSetParam**に**SQLBindParam**です。 これは、ため特定既存の ODBC 2 です。*x*ドライバーの特殊な値を使用して*BufferLength* (SQL_SETPARAM_VALUE_MAX) に割り当てるときに、ドライバー マネージャーが生成する**SQLSetParam**の上に**SQLBindParameter**を 1 で呼び出されたときを判断します *。x* ODBC アプリケーションです。  
  
 呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次になります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
