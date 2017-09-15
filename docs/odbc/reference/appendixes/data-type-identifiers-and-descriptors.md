---
title: "データ型の識別子と記述子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
- descriptors [ODBC], data types
- verbose data types [ODBC]
- data types [ODBC], descriptors
- concise data types [ODBC]
ms.assetid: f0077c9b-8eb2-4b5f-8c4c-7436fdef37ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 93b813632c3a281e1ae0ba90e95545e28d07ed09
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-identifiers-and-descriptors"></a>データ型識別子と記述子
データの種類の一覧を[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)と[C データ型](../../../odbc/reference/appendixes/c-data-types.md)前述のセクションでは、「簡潔な」のデータ型: 各識別子は、1 つのデータ型を参照します。 識別子と、データ型の間で一対一で対応します。 記述子、ただし、処理を行うされていないすべての場合は、データ型を識別する単一の値を使用します。 場合によっては、"verbose"のデータ型と型サブコード使用します。 Datetime および間隔のデータ型を除くすべてのデータ型の詳細な型識別子は、簡潔なタイプ識別子と同じと SQL_DESC_DATETIME_INTERVAL_CODE の値が 0 にします。 Datetime および間隔のデータ型のただし、(SQL_DATETIME または SQL_INTERVAL) の詳細な型に格納 SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE に簡潔な型が格納されているされ SQL_DESC_DATETIME_INTERVAL_CODE に簡潔な各種のサブコードが格納されています。 これらのフィールドのいずれかを設定すると、その他に影響します。 これらのフィールドの詳細については、次を参照してください。、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)関数の説明。  
  
 一部のデータ型の SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE またはフィールドを設定するとと、SQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_LENGTH、SQL_DESC_PRECISION、および SQL_DESC_SCALE フィールドがデータの該当する場合に、既定値に自動的に設定します。入力します。 詳細については、の SQL_DESC_TYPE フィールドの説明を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。 既定値の設定のいずれかの情報が適切でない場合、アプリケーションを呼び出すことによって、記述子フィールドに明示的に設定する必要があります**SQLSetDescField**です。  
  
 次の表は、簡潔なタイプ識別子、詳細な型の識別子、および各 datetime と SQL の間隔と C 型識別子の型のサブコードを示します。 SQL_DESC_TYPE と SQL_DESC_DATETIME_INTERVAL_CODE フィールドに同じマニフェスト定数 (実装記述子) での SQL データ型と C データ型 (内のアプリケーションの両方がある日時および間隔のデータ型について、この表に示すよう記述子)。  
  
|簡潔な SQL 型|簡潔な C 型|詳細な型|DATETIME_INTERVAL_CODE|  
|----------------------|--------------------|------------------|------------------------------|  
|SQL_TYPE_DATE|SQL_C_TYPE_DATE|SQL_DATETIME|SQL_CODE_DATE|  
|SQL_TYPE_TIME|SQL_C_TYPE_TIME|SQL_DATETIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|SQL_DATETIME|SQL_CODE_TIMESTAMP|  
|SQL_INTERVAL_MONTH|SQL_C_INTERVAL_MONTH|SQL_INTERVAL|SQL_CODE_MONTH|  
|SQL_INTERVAL_YEAR|SQL_C_INTERVAL_YEAR|SQL_INTERVAL|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_INTERVAL|SQL_CODE_YEAR_TO_MONTH|  
QL_INTERVAL_DAY|SQL_C_INTERVAL_DAY|SQL_INTERVAL|SQL_CODE_DAY|  
|SQL_INTERVAL_HOUR|SQL_C_INTERVAL_HOUR|SQL_INTERVAL|SQL_CODE_HOUR|  
|SQL_INTERVAL_MINUTE|SQL_C_INTERVAL_MINUTE|SQL_INTERVAL|SQL_CODE_MINUTE|  
|SQL_INTERVAL_SECOND|SQL_C_INTERVAL_SECOND|SQL_INTERVAL|SQL_CODE_SECOND|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_C_INTERVAL_DAY_TO_HOUR|SQL_INTERVAL|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE|SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_INTERVAL|SQL_CODE_DAY_TO_MINUTE|  
QL_INTERVAL_DAY_TO_SECOND|SQL_C_INTERVAL_DAY_TO_SECOND|SQL_INTERVAL|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR_TO_MINUTE|SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_INTERVAL|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND|SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_INTERVAL|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE_TO_SECOND|SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_INTERVAL|SQL_CODE_MINUTE_TO_SECOND|
