---
title: '付録 E: スカラー関数 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea354a7f882bd1a75c5f16fb19350d69ca11d375
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292492"
---
# <a name="appendix-e-scalar-functions"></a>付録 E: スカラー関数
ODBC では、次の種類のスカラー関数を指定し、これらの各関数型に関する詳細については、この付録の対応するセクションで説明します。 関数の説明には、関連する構文が含まれます。  
  
 この付録では、以下のトピックを取り上げます。  
  
-   [文字列関数](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [数値関数](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [時刻、日付、および間隔を扱う関数](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [システム関数](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [データ型の明示的な変換用関数](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [SQL-92 CAST 関数](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC では、多くの場合、関数はデータ ソース固有であるため、スカラー関数からの戻り値のデータ型は必須ではありません。 アプリケーションは、データ型変換を強制するために、可能な限り CONVERT スカラー関数を使用する必要があります。  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>ODBC および SQL-92 スカラー関数  
 この付録の表には、SQL-92 に合わせて ODBC 3.0 で追加された関数が含まれています。 ODBC で定義されている特定のスカラー関数に追加された関数は、各セクションで示されています。  
  
 ODBC と SQL-92 はスカラー関数を異なる方法で分類します。 ODBC は、引数の型でスカラー関数を分類します。SQL-92 は、戻り値で分類します。 例えば、抽出フィールド引数は datetime キーワードで、抽出元引数は日時式または間隔式であるため、EXTRACT 関数は ODBC によって日付日付関数として分類されます。 一方、SQL-92 では、戻り値は数値であるため、EXTRACT を数値スカラー関数として分類します。  
  
 アプリケーションは **、SQLGetInfo**を呼び出すことによって、ドライバーがサポートするスカラー関数を決定できます。 情報型は、ODBC と SQL-92 スカラー関数の分類の両方に含まれています。 これらの分類は異なるため、一部のスカラー関数のサポートは、ODBC および SQL-92 に対応しない情報型で示される場合があります。 たとえば、ODBC での EXTRACT のサポートは、SQL_TIMEDATE_FUNCTIONS情報の種類によって示されます。一方、SQL-92 での EXTRACT のサポートは、SQL_SQL92_NUMERIC_VALUE_FUNCTIONS情報タイプによって示されます。
