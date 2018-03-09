---
title: "Interval データ型の先頭と秒の有効桁数を上書き |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 70ae232ed09ab7bd04a2474b5798dd4ed581df39
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Interval データ型のトップ レベルの既定値と秒の有効桁数を上書きします。
ARD の SQL_DESC_TYPE フィールド設定されている場合に、datetime 型または interval C 型を呼び出して、 **SQLBindCol**または**SQLSetDescField**、SQL_DESC_PRECISION フィールド (が間隔 (秒) が含まれています有効桁数) は、次の既定値に設定されます。  
  
-   タイムスタンプと 2 番目のコンポーネントの interval データ型をすべて 6。  
  
-   その他のすべてのデータ型は 0 です。  
  
 すべての interval データ型の間隔の先頭フィールドの精度を含む SQL_DESC_DATETIME_INTERVAL_PRECISION 記述子フィールドは、既定値は 2 に設定されます。  
  
 APD の SQL_DESC_TYPE フィールド設定されている場合に、datetime 型または interval C 型を呼び出して、 **SQLBindParameter**または**SQLSetDescField**、SQL_DESC_PRECISION および SQL_DESC_DATETIME_INTERVAL_APD の有効桁数のフィールドは、以前に指定された既定値に設定されます。 これは true、入力パラメーターは入力/出力または出力パラメーターです。  
  
 呼び出し**SQLSetDescRec**有効桁数を既定値に先行する間隔を設定しますが、(SQL_DESC_PRECISION フィールド) の間隔の秒の有効桁数の値に設定の*精度*引数。  
  
 アプリケーションが呼び出すことによって、SQL_DESC_PRECISION または SQL_DESC_DATETIME_INTERVAL_PRECISION のフィールドを設定する必要がありますの既定の設定のいずれかの以前が許容されない場合、アプリケーションに、 **SQLSetDescField**です。  
  
 アプリケーションを呼び出す場合**SQLGetData** datetime または C 型の間隔にデータを返す、既定の間隔の主要な有効桁数と間隔の秒の有効桁数を使用します。 いずれかの既定値が許容されない場合、アプリケーションを呼び出す必要があります**SQLSetDescField**いずれかの記述子フィールドを設定または**SQLSetDescRec** SQL_DESC_PRECISION を設定します。 呼び出し**SQLGetData**が必要な*TargetType* SQL_ARD_TYPE の記述子フィールドの値を使用するのです。  
  
 ときに**SQLPutData**が呼び出されると、先頭の有効桁数と間隔 (秒) 有効桁数は、実行時データ パラメーターまたは列に対応する記述子レコードのフィールドから読み取ら APD のフィールドの呼び出しのためには、間隔**SQLExecute**または**SQLExecDirect**、または呼び出しのために ARD フィールド**SQLBulkOperations**または**SQLSetPos**です。
