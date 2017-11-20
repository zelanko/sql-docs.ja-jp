---
title: "記述子フィールドへの準拠 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 049208450144fdd1c1d3b902093517627486ccf9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-field-conformance"></a>記述子フィールドへの準拠
次の表では、各 ODBC 記述子のヘッダー フィールド、これは、定義済みの準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|コア|  
|SQL_DESC_ARRAY_SIZE|コア|  
|SQL_DESC_ARRAY_STATUS_PTR|コア (APD、IPR、および IRD) です。レベル 1 (ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|コア|  
|SQL_DESC_BIND_TYPE|コア|  
|SQL_DESC_COUNT|コア|  
|SQL_DESC_ROWS_PROCESSED_PTR|コア|  
  
 次の表では、各 ODBC 記述子レコード フィールドのこれは適切に定義された準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|[レベル 2]|  
|SQL_DESC_BASE_COLUMN_NAME|コア|  
|SQL_DESC_BASE_TABLE_NAME|[レベル 1]|  
|SQL_DESC_CASE_SENSITIVE|コア|  
|SQL_DESC_CATALOG_NAME|[レベル 2]|  
|SQL_DESC_CONCISE_TYPE|コア|  
|SQL_DESC_DATA_PTR|コア|  
|SQL_DESC_DATETIME_INTERVAL_ コード|コア [1]|  
|SQL_DESC_DATETIME_INTERVAL_ 精度|コア [1]|  
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
  
 [これらのレコードのフィールドのサポート 1] が、ドライバーは、該当するデータ型をサポートしている場合にのみ必要です。  
  
 [2] のコア レベルへの準拠、ドライバーは SQL_PARAM_INPUT をサポートする必要があります。 レベル 2 インターフェイスへの準拠のドライバーを SQL_PARAM_INPUT_OUTPUT と SQL_PARAM_OUTPUT もサポートする必要があります。

