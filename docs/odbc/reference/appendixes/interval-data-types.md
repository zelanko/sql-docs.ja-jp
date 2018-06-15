---
title: Interval データ型 |Microsoft ドキュメント
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
- second intervals [ODBC]
- data types [ODBC], interval data types
- interval data type [ODBC]
- day-time intervals [ODBC]
- intervals [ODBC], about intervals
- minute intervals [ODBC]
- day intervals [ODBC]
- year intervals [ODBC]
- month intervals [ODBC]
- interval data type [ODBC], about interval data types
- SQL data types [ODBC], interval
- year-month intervals [ODBC]
- C data types [ODBC], interval
- interval fields [ODBC]
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebc6b5d2a8e2277c3bb427053f43ebed4983e0b9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909567"
---
# <a name="interval-data-types"></a>Interval データ型
間隔は 2 つの日付と時刻の差として定義されます。 間隔は 2 つの方法のいずれかで表されます。 1 つは、*年-月*年と月の整数単位の間隔を表す間隔。 もう 1 つは、*日時間*日間、分、および秒単位の間隔を表す間隔。 これら 2 種類の間隔は、distinct か月間で異なる数の日数があるため、混在させることはできません。  
  
 間隔は、一連のフィールドで構成されます。 フィールドの間で暗黙的な順序付けがあります。 たとえば、年-月間隔で年は最初に、月単位での後にできます。 同様に、1 日 ~ 分間隔では、フィールドは、注文日、時間と分でです。 間隔の種類の最初のフィールドと呼ばれる、*先頭*フィールド、または*上位*フィールド。 最後のフィールドと呼ばれる、*末尾*フィールドです。  
  
 すべての間隔で、先頭のフィールドはグレゴリオ暦のルールによって制限されません。 たとえば、時間、分間隔の時間フィールドに制限されていませんは通常、0 ~ 23 (包括) で指定します。 その後、その先頭フィールドの後続のフィールドには、グレゴリオ暦の通常の制約に従ってください。 詳細については、次を参照してください。[グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)、後の「します。  
  
 13 interval SQL データ型と 13 interval C データ型があります。 各間隔 C データ型は、同じ構造、SQL_INTERVAL_STRUCT を使用して、間隔データが含まれます。 (詳細については、次のセクションを参照してください[C 間隔構造](../../../odbc/reference/appendixes/c-interval-structure.md)。)。SQL データ型の詳細については、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)C データ型の詳細についてを参照してください。 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)です。  
  
|型識別子|クラス|Description|  
|---------------------|-----------|-----------------|  
|[MONTH]|年-月|2 つの日付の月の数です。|  
|[YEAR]|年-月|2 つの日付間の年の数。|  
|YEAR_TO_MONTH|年-月|年と 2 つの日付の月の数です。|  
|[DAY]|-時刻|2 つの日付間の日数を指定します。|  
|[HOUR]|-時刻|2 つの間の時間数の日付/時刻です。|  
|[MINUTE]|-時刻|2 つの間隔を分単位の数の日付/時刻です。|  
|[SECOND]|-時刻|2 つの間の秒数の日付/時刻です。|  
|DAY_TO_HOUR|-時刻|2 つの間の日数/時間数の日付/時刻です。|  
|DAY_TO_MINUTE|-時刻|日数/時間/間隔 (分) 2 つの日付/時刻です。|  
|DAY_TO_SECOND|-時刻|日数/時間/分/秒数 2 つの日付/時刻です。|  
|HOUR_TO_MINUTE|-時刻|2 つの分単位の時間数日付/時刻です。|  
|HOUR_TO_SECOND|-時刻|2 つの時間、分/秒の数の日付/時刻です。|  
|MINUTE_TO_SECOND|-時刻|2 つ分/秒の数の日付/時刻です。|  
  
 このセクションでは、次のトピックを扱います。  
  
-   [C Interval 構造体](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Interval データ型の精度](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Interval のリテラル](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Interval データ型での既定の先頭有効桁数と秒小数部分の上書き](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
