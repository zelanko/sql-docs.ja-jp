---
title: SQLGet タイプ情報の結果セットの例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], examples
- SQLGetTypeInfo function [ODBC], examples
- data types [ODBC], SQL data types
ms.assetid: dc1952cc-7581-4d69-9c72-7dc1cd370836
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5cf62f8a95f4c91095c21a6d603317fe1f73500
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307013"
---
# <a name="example-sqlgettypeinfo-result-set"></a>SQLGetTypeInfo 結果セットの例
アプリケーションは **、SQLGetTypeInfo**を呼び出して、データ ソースでサポートされているデータ型とそれらのデータ型の特性を判断します。 次の表は、SQL_CHAR、SQL_LONGVARCHAR、SQL_DECIMAL、SQL_REAL、SQL_DATETIME、SQL_INTERVAL_YEAR、およびSQL_INTERVAL_DAY_TO_SECONDをサポートするデータ ソースに対して**SQLGetTypeInfo**によって返される結果セットのサンプルを示しています。  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|"char"|SQL_CHAR|255|"'"|"'"|「長さ」|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<ヌル>|SQL_TRUE|  
|"decimal"|SQL_DECIMAL|28|\<ヌル>|\<ヌル>|「精度、<br />スケール"|SQL_TRUE|  
|「本物」|SQL_REAL|7|\<ヌル>|\<ヌル>|\<ヌル>|SQL_TRUE|  
|「日時」|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<ヌル>|SQL_TRUE|  
|"区間年()から年まで"|SQL_INTERVAL_YEAR|9|"'"|"'"|「精度」|SQL_TRUE|  
|"間隔日() から分数(5))|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|「精度」|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<ヌル>|SQL_FALSE|\<ヌル>|"char"|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<ヌル>|SQL_FALSE|\<ヌル>|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"decimal"|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|「本物」|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<ヌル>|SQL_FALSE|\<ヌル>|「日時」|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<ヌル>|SQL_FALSE|\<ヌル>|"区間年()から年まで"|  
|**SQL_INTERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<ヌル>|SQL_FALSE|\<ヌル>|"間隔日() から分数(5))|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<ヌル>|\<ヌル>|SQL_CHAR|\<ヌル>|\<ヌル>|\<ヌル>|  
|**SQL_LONGVARCHAR**|\<ヌル>|\<ヌル>|SQL_LONGVARCHAR|\<ヌル>|\<ヌル>|\<ヌル>|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<ヌル>|10|\<ヌル>|  
|**SQL_REAL**|\<ヌル>|\<ヌル>|SQL_REAL|\<ヌル>|10|\<ヌル>|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<ヌル>|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<ヌル>|9|  
|**SQL_INTERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<ヌル>|9|
