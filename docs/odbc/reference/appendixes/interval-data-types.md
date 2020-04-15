---
title: 間隔データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee4a6e845e0bc0830f514b2e768075dd75bcf6e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304968"
---
# <a name="interval-data-types"></a>Interval データ型
間隔は、2 つの日付と時刻の差として定義されます。 間隔は、2 つの異なる方法のいずれかで表されます。 1 つは *、年単位の*間隔と整数の月数を表す年月間隔です。 もう 1 つは *、日*、分、および秒の間隔を表す日時間間隔です。 月は日数が異なる場合があるため、これらの 2 種類の間隔は明確であり、混在させることはできません。  
  
 間隔は、一連のフィールドで構成されます。 フィールド間には暗黙の順序があります。 たとえば、年から月の間隔では、年が最初に来て、その後に月が続きます。 同様に、1 日から分の間隔で、フィールドは順序の日、時間、分です。 間隔タイプの最初のフィールドは、*先行*フィールドまたは上位フィールドと呼*ばれます*。 最後のフィールドは *、末尾*のフィールドと呼ばれます。  
  
 すべての間隔において、先行フィールドはグレゴリオ暦の規則によって制約されません。 たとえば、時間から分の間隔では、時間フィールドは通常のように 0 ~ 23 (両端を含む) の間に制約されません。 先行フィールドの後にある後続のフィールドは、グレゴリオ暦の通常の制約に従います。 詳細については、後[の「グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)」を参照してください。  
  
 13 の間隔 SQL データ・タイプと 13 のインターバル C データ・タイプがあります。 インターバル C の各データ・タイプは、同じ構造 (SQL_INTERVAL_STRUCT) を使用して、インターバル・データを入れられます。 (詳細については、次のセクション[「C 間隔構造](../../../odbc/reference/appendixes/c-interval-structure.md)」を参照してください)。SQL データ型の詳細については[、SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)を参照してください。C データ型の詳細については[、「C データ](../../../odbc/reference/appendixes/c-data-types.md)型」を参照してください。  
  
|型識別子|クラス|説明|  
|---------------------|-----------|-----------------|  
|MONTH|年月|2 つの日付間の月数。|  
|YEAR|年月|2 つの日付間の年数。|  
|YEAR_TO_MONTH|年月|2 つの日付間の年と月の数。|  
|DAY|デイタイム|2 つの日付間の日数。|  
|HOUR|デイタイム|2 つの日付/時刻の間の時間数。|  
|MINUTE|デイタイム|2 つの日付/時刻の間の分数。|  
|SECOND|デイタイム|2 つの日付/時刻の間の秒数。|  
|DAY_TO_HOUR|デイタイム|2 つの日付/時刻の間の日数/時間数。|  
|DAY_TO_MINUTE|デイタイム|2 つの日付/時刻の間の日数/時間/分数。|  
|DAY_TO_SECOND|デイタイム|2 つの日付/時刻の間の日数/時間/分/秒数。|  
|HOUR_TO_MINUTE|デイタイム|2 つの日付/時刻の間の時間/分数。|  
|HOUR_TO_SECOND|デイタイム|2 つの日付/時刻の間の時間/分/秒数。|  
|MINUTE_TO_SECOND|デイタイム|2 つの日付/時刻の間の分/秒数。|  
  
 このセクションでは、次のトピックを扱います。  
  
-   [C Interval 構造体](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Interval データ型の精度](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Interval のリテラル](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Interval データ型での既定の先頭有効桁数と秒小数部分のオーバーライド](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
