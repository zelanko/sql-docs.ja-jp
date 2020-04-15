---
title: 間隔データ型の精度 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- precision [ODBC]
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: eb73bd77-2e7e-4498-a266-4d7c990a0d56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 746293c545c47917abd084ec3eb105051fc2fbcf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290742"
---
# <a name="interval-data-type-precision"></a>Interval データ型の精度
間隔データ型の精度には、間隔をリードする精度、間隔精度、および秒精度が含まれます。  
  
 間隔の先行フィールドは符号付き数値です。 先行フィールドの最大桁数は、データ型宣言の一部である*間隔先行精度*と呼ばれる数量によって決まります。 例えば、INTERVAL HOUR(5) TO MINUTE の宣言には、長さ 5 の間隔が入っています。HOUR フィールドは、-99999 から 99999 までの値を取ることができます。 間隔先行精度は、記述子レコードのSQL_DESC_DATETIME_INTERVAL_PRECISIONフィールドに含まれています。  
  
 間隔データ型が構成されるフィールドのリストは、*間隔精度*と呼ばれます。 "精度" という用語が示すとおり、数値ではありません。 例えば、タイプ間隔日から秒の間隔精度は、リストの日、時、分、秒です。 この値を保持する記述子フィールドはありません。間隔の精度は、常に間隔データ型によって決定できます。  
  
 SECOND フィールドを持つ間隔データ型には *、秒精度*があります。 これは秒値の小数部に許容される小数の桁数です。 これは、精度が小数点の前の桁数を示す他のデータ型とは異なります。 間隔データ型の秒精度は、小数点以下の桁数です。 たとえば、秒精度が 6 に設定されている場合、分数フィールドの数値 123456 は .123456 と解釈され、数値 1230 は .001230 と解釈されます。 その他のデータ型の場合は、これをスケールと呼びます。 間隔の秒精度は、記述子のSQL_DESC_PRECISIONフィールドに含まれています。 SQL 間隔値の秒の小数秒の精度が、C 間隔構造体で保持できる値よりも大きい場合、C 間隔構造体に変換するときに、SQL 間隔の小数秒値を丸めるか切り捨てるかは、ドライバー定義です。  
  
 SQL_DESC_CONCISE_TYPEフィールドが間隔データ型に設定されている場合、SQL_DESC_TYPEフィールドはSQL_INTERVALに設定され、SQL_DESC_DATETIME_INTERVAL_CODEは間隔データ型のコードに設定されます。 SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドは、デフォルトの間隔の先行精度 2 に自動的に設定され、SQL_DESC_PRECISION フィールドは自動的にデフォルトの間隔の秒精度 6 に設定されます。 これらの値のいずれかが適切でない場合、アプリケーションは**SQLSetDescField**の呼び出しを通じて記述子フィールドを明示的に設定する必要があります。
