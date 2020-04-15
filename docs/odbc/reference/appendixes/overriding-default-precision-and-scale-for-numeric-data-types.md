---
title: 数値データ型の既定の精度と小数点以下桁数のオーバーライド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365c5f69d21dd3a4ad8e89805d81f1b3b0c9dcba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303593"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>数値データ型での既定の有効桁数と小数点以下桁数のオーバーライド
ARD のSQL_DESC_TYPE フィールドが SQL_C_NUMERIC に設定されている場合 **、SQLBindCol**または**SQLSetDescField**を呼び出すことによって、ARD のSQL_DESC_SCALE フィールドは 0 に設定され、SQL_DESC_PRECISION フィールドはドライバー定義の既定の精度に設定されます。 これは、APD のSQL_DESC_TYPE フィールドが**SQL_C_NUMERIC**に設定されている場合にも当**てはまります。** これは、入力、入出力、または出力パラメーターに当てはまります。  
  
 前述のデフォルトのいずれかがアプリケーションで許容できない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**を呼び出して SQL_DESC_SCALE またはSQL_DESC_PRECISIONフィールドを設定する必要があります。  
  
 アプリケーションが**SQLGetData**を呼び出してデータをSQL_C_NUMERIC構造体に返す場合、既定のSQL_DESC_SCALEおよびSQL_DESC_PRECISIONフィールドが使用されます。 デフォルトが許容されない場合、アプリケーションは**SQLSetDescRec**または**SQLSetDescField**を呼び出してフィールドを設定し、記述子フィールドの値を使用する*SQL_ARD_TYPEのターゲットタイプ*を指定して**SQLGetData**を呼び出す必要があります。  
  
 **SQLPutData**が呼び出されると、呼び出しは **、SQLBulkOperations****または****SQLSetPos**への呼び出しの呼び出しの APD**SQLExecute**フィールドである、実行時のデータ パラメーターまたは列に対応する記述子レコードのSQL_DESC_SCALEおよびSQL_DESC_PRECISION フィールドを使用します。
