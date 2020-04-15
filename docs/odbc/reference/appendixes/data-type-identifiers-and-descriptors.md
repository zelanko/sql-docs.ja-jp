---
title: データ型識別子と記述子 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f65bc86213f99112daf17c67a4ca522490d32149
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284485"
---
# <a name="data-type-identifiers-and-descriptors"></a>データ型識別子と記述子
この付録の[「SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」および[「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」のセクションに記載されているデータ型は「簡潔」なデータ型です。 識別子とデータ型の間には 1 対 1 の対応があります。 ただし、記述子では、データ型を識別するために単一の値を使用するわけではありません。 場合によっては、"詳細" データ型と型サブコードを使用します。 日時型と間隔データ型を除くすべてのデータ型の詳細型識別子は簡潔な型識別子と同じで、SQL_DESC_DATETIME_INTERVAL_CODEの値は 0 です。 ただし、日時型と間隔データ型の場合は、冗長型 (SQL_DATETIME またはSQL_INTERVAL) が SQL_DESC_TYPE に格納され、簡潔な型がSQL_DESC_CONCISE_TYPEに格納され、各簡潔な型のサブコードがSQL_DESC_DATETIME_INTERVAL_CODEに格納されます。 これらのフィールドの 1 つを設定すると、他のフィールドに影響が及びます。 これらのフィールドの詳細については[、SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)関数の説明を参照してください。  
  
 一部のデータ型に対してSQL_DESC_TYPE または SQL_DESC_CONCISE_TYPE フィールドを設定すると、SQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_LENGTH、SQL_DESC_PRECISION、およびSQL_DESC_SCALEフィールドは、データ型に応じて自動的に既定値に設定されます。 詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の SQL_DESC_TYPE フィールドの説明を参照してください。 設定されたデフォルト値のいずれかが適切でない場合、アプリケーションは**SQLSetDescField**の呼び出しを通じて記述子フィールドを明示的に設定する必要があります。  
  
 次の表は、日付と間隔の SQL 型と C 型の識別子の簡潔な型識別子、詳細な型識別子、および型サブコードを示しています。 この表が示すように、日時データ・タイプと間隔データ・タイプの場合、SQL_DESC_TYPEフィールドとSQL_DESC_DATETIME_INTERVAL_CODEフィールドは、SQL データ・タイプ (実装記述子内) と C データ・タイプ (アプリケーション記述子内) の両方に対して同じマニフェスト定数を持っています。  
  
|簡潔な SQL タイプ|簡潔なC型|詳細タイプ|DATETIME_INTERVAL_CODE|  
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
