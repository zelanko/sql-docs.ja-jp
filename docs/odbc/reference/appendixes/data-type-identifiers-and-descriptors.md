---
title: データ型識別子と記述子 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 748f2452d20b618ae0011e2e1ac4e24af098ac06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019048"
---
# <a name="data-type-identifiers-and-descriptors"></a>データ型識別子と記述子
この付録の「 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」および「 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)」のセクションに記載されているデータ型は、"簡潔な" データ型です。各識別子は1つのデータ型を参照します。 識別子とデータ型の間には一対一の対応があります。 ただし、記述子では、いずれの場合も、1つの値を使用してデータ型を識別します。 場合によっては、"verbose" データ型と型のサブコードを使用します。 Datetime データ型および interval データ型を除くすべてのデータ型では、詳細な型識別子は簡潔な型識別子と同じであり、SQL_DESC_DATETIME_INTERVAL_CODE の値は0に等しくなります。 ただし、datetime および interval データ型の場合、verbose 型 (SQL_DATETIME または SQL_INTERVAL) は SQL_DESC_TYPE に格納され、簡潔な型は SQL_DESC_CONCISE_TYPE に格納され、各簡潔な型のサブコードは SQL_DESC_DATETIME_INTERVAL_CODE に格納されます。 これらのフィールドのいずれかを設定すると、他のフィールドに影響します。 これらのフィールドの詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)関数の説明を参照してください。  
  
 SQL_DESC_TYPE または SQL_DESC_CONCISE_TYPE フィールドが一部のデータ型に対して設定されている場合、データに適用されるように、SQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_LENGTH、SQL_DESC_PRECISION、および SQL_DESC_SCALE の各フィールドが既定値に自動的に設定されます。各種. 詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の SQL_DESC_TYPE フィールドの説明を参照してください。 既定値が適切に設定されていない場合は、アプリケーションで**SQLSetDescField**の呼び出しを使用して記述子フィールドを明示的に設定する必要があります。  
  
 次の表は、各 datetime および interval SQL および C 型の識別子の簡潔な型識別子、詳細な型識別子、および型サブコードを示しています。 この表に示すように、datetime データ型および interval データ型の場合、SQL_DESC_TYPE フィールドと SQL_DESC_DATETIME_INTERVAL_CODE フィールドのマニフェスト定数は、SQL データ型 (実装記述子内) と C データ型 (アプリケーションの場合) の両方で同じです。記述子)。  
  
|簡潔な SQL 型|簡潔な C 型|詳細な種類|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
|SQL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
