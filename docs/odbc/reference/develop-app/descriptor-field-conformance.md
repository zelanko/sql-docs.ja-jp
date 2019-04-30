---
title: 記述子フィールドの適合性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 193bdadaf36e975b1f79327bfef161daaaed427b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049853"
---
# <a name="descriptor-field-conformance"></a>記述子フィールドの適合性
次の表では、各 ODBC 記述子のヘッダー フィールド、これは適切に定義されたの準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|コア|  
|SQL_DESC_ARRAY_SIZE|コア|  
|SQL_DESC_ARRAY_STATUS_PTR|(APD、IPR とコア IRD)。レベル 1 (ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|コア|  
|SQL_DESC_BIND_TYPE|コア|  
|SQL_DESC_COUNT|コア|  
|SQL_DESC_ROWS_PROCESSED_PTR|コア|  
  
 次の表では、各 ODBC 記述子レコード フィールド、これは適切に定義されたの準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|[レベル 2]|  
|SQL_DESC_BASE_COLUMN_NAME|コア|  
|SQL_DESC_BASE_TABLE_NAME|[レベル 1]|  
|SQL_DESC_CASE_SENSITIVE|コア|  
|SQL_DESC_CATALOG_NAME|[レベル 2]|  
|SQL_DESC_CONCISE_TYPE|コア|  
|SQL_DESC_DATA_PTR|コア|  
|SQL_DESC_DATETIME_INTERVAL_ コード|Core[1]|  
|SQL_DESC_DATETIME_INTERVAL_ 精度|Core[1]|  
|SQL_DESC_DISPLAY_SIZE|コア|  
|SQL_DESC_FIXED_PREC_SCALE|コア|  
|SQL_DESC_INDICATOR_PTR|コア|  
|SQL_DESC_LABEL|[レベル 2]|  
|SQL_DESC_LENGTH|コア|  
|SQL_DESC_LITERAL_PREFIX|コア|  
|SQL_DESC_LITERAL_SUFFIX|コア|  
|SQL_DESC_LOCAL_TYPE_NAME|コア|  
|SQL_DESC_NAME|コア|  
|SQL_DESC_NULLABLE|コア|  
|SQL_DESC_OCTET_LENGTH|コア|  
|SQL_DESC_OCTET_LENGTH_PTR|コア|  
|SQL_DESC_PARAMETER_TYPE|コア/レベル 2 [2]|  
|SQL_DESC_PRECISION|コア|  
|SQL_DESC_ROWVER|[レベル 1]|  
|SQL_DESC_SCALE|コア|  
|SQL_DESC_SCHEMA_NAME|[レベル 1]|  
|SQL_DESC_SEARCHABLE|コア|  
|SQL_DESC_TABLE_NAME|[レベル 1]|  
|SQL_DESC_TYPE|コア|  
|SQL_DESC_TYPE_NAME|コア|  
|SQL_DESC_UNNAMED|コア|  
|SQL_DESC_UNSIGNED|コア|  
|SQL_DESC_UPDATABLE|コア|  
  
 [これらのレコードのフィールドのサポート 1] は、ドライバーは、該当するデータ型をサポートしている場合にのみ必要です。  
  
 [2] のコア レベルへの準拠、ドライバーは SQL_PARAM_INPUT をサポートする必要があります。 レベル 2 インターフェイスの適合性のドライバーで SQL_PARAM_INPUT_OUTPUT と SQL_PARAM_OUTPUT もサポートする必要があります。
