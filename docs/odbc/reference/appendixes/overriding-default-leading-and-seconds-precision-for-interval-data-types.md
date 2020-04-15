---
title: 間隔データ型の先頭および秒精度を上書きする |マイクロソフトドキュメント
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
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e60d5d8fc696ad8e2bd4cfb0c082ff214e066d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303603"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Interval データ型での既定の先頭有効桁数と秒小数部分のオーバーライド
ARD のSQL_DESC_TYPE フィールドが **、SQLBindCol**または**SQLSetDescField**を呼び出すことによって、日付時刻型または間隔 C 型に設定されている場合、SQL_DESC_PRECISION フィールド (秒の間隔の精度を含む) は、次の既定値に設定されます。  
  
-   2 番目のコンポーネントを持つタイムスタンプとすべての間隔データ型の場合は 6。  
  
-   その他すべてのデータ型の場合は 0。  
  
 すべての間隔データ・タイプについて、SQL_DESC_DATETIME_INTERVAL_PRECISION記述子フィールドには、間隔先行フィールド精度が入っていますが、デフォルト値 2 が設定されます。  
  
 APD のSQL_DESC_TYPE フィールドが **、SQLBindParameter**または**SQLSetDescField**を呼び出すことによって、日付時刻型または間隔 C 型に設定されている場合、APD のSQL_DESC_PRECISIONフィールドとSQL_DESC_DATETIME_INTERVAL_PRECISION フィールドは、前に指定された既定値に設定されます。 これは入力パラメータに当てはまりますが、入出力パラメータや出力パラメータには当てはまりません。  
  
 **SQLSetDescRec**を呼び出すと、間隔の先行精度がデフォルトに設定されますが、間隔の秒精度 (SQL_DESC_PRECISION フィールド内) は、その*Precision*引数の値に設定されます。  
  
 前に指定した既定値のいずれかがアプリケーションに受け入れられない場合、アプリケーションは**SQLSetDescField**を呼び出してSQL_DESC_PRECISIONまたはSQL_DESC_DATETIME_INTERVAL_PRECISION フィールドを設定する必要があります。  
  
 アプリケーションが**SQLGetData**を呼び出してデータを日付時刻型または間隔 C 型に戻す場合、精度と秒間隔の精度を先頭にしたデフォルトの間隔が使用されます。 いずれかのデフォルトが受け入れられない場合、アプリケーションは**SQLSetDescField**を呼び出して記述子フィールドを設定するか **、SQLSetDescRec**を SQL_DESC_PRECISION設定する必要があります。 **SQLGetData**の呼び出しには、記述子フィールドの値を使用するSQL_ARD_TYPEの*ターゲット型*が必要です。  
  
 **SQLPutData**が呼び出されると、実行時のデータ パラメーターまたは列に対応する記述子レコードのフィールド **(SQLBulkOperations**または**SQLSetPos**への呼び出しの APD フィールドである ) に対応する記述子レコードの**SQLBulkOperations**フィールドから、間隔の先行精度と秒間隔の精度が読み取**られます**。
