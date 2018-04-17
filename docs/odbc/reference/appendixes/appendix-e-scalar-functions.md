---
title: '「付録 e: スカラー関数は |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ee9e2ab75f22ae3090d87d5c232f88423df9360
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="appendix-e-scalar-functions"></a>スカラー関数は「付録 e:
ODBC では、この付録の対応するセクションで提供されるこれらの関数型のそれぞれに関する詳細情報と共に、スカラー関数の次の種類を指定します。 関数の説明には、関連する構文が含まれます。  
  
 この付録の内容には、次のトピックが含まれています。  
  
-   [文字列関数](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [数値関数](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [時刻、日付、および間隔の関数](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [システム関数](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [データ型の明示的な変換用関数](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [SQL-92 CAST 関数](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC 必須ではない戻り値のデータ型のスカラー関数から関数では多くの場合、データ ソース固有のためです。 アプリケーションでは、データ型の変換を強制的に可能な限り CONVERT のスカラー関数を使用する必要があります。  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>ODBC と sql-92 のスカラー関数  
 この付録の表では、ODBC 3.0 では、sql-92 に合うように追加されている関数があります。 各セクションでは、特定の種類のスカラー関数、ODBC では、定義されている追加これらの関数が示されます。  
  
 ODBC と sql-92、スカラー関数を異なる方法で分類します。 ODBC スカラー関数は引数の型での分類します。SQL 92 戻り値によって分類を実行します。 たとえば、EXTRACT 関数によって分類される timedate 関数として ODBC では、フィールド抽出引数は、datetime キーワード、抽出元の引数が日付時刻または間隔式ためです。 Sql-92 は、戻り値が数値であるためその一方で、抽出と数値のスカラー関数として分類します。  
  
 アプリケーションが呼び出すことによって、ドライバーをサポートするスカラー関数を判断できます**SQLGetInfo**です。 情報の種類が ODBC とスカラー関数の SQL 92 分類の両方に含まれるです。 これらの分類が異なるために、ODBC および sql-92 に対応していない種類の情報でいくつかのスカラー関数のサポートを示す可能性があります。 たとえば、ODBC での抽出用のサポート型により示される、SQL_TIMEDATE_FUNCTIONS 情報です。その一方で、対応しており、sql-92 で抽出は SQL_SQL92_NUMERIC_VALUE_FUNCTIONS 情報の種類で表されます。
