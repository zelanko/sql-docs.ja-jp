---
title: 数値データ型の既定の有効桁数と小数点以下桁数を上書きする |Microsoft ドキュメント
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
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cfe7bcedb96f5a7ff311d90b5dcdc28fc77b79f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>数値データ型の既定の有効桁数と小数点以下桁数を上書きします。
ARD の SQL_DESC_TYPE フィールド設定されている場合、SQL_C_NUMERIC を呼び出して、 **SQLBindCol**または**SQLSetDescField**ARD SQL_DESC_SCALE フィールドが 0 に設定されている、および SQL_DESC_PRECISION フィールドが設定されています。ドライバーの定義済みの既定の有効桁数です。 これは true にも、APD の SQL_DESC_TYPE フィールドを呼び出して、SQL_C_NUMERIC に設定されている**SQLBindParameter**または**SQLSetDescField**です。 これは、入力、入力/出力、または出力パラメーターの場合は true です。  
  
 アプリケーションが呼び出すことによって、SQL_DESC_SCALE または SQL_DESC_PRECISION のフィールドを設定する必要があります説明されている既定値のいずれかの前でない場合、アプリケーションで受け入れ**SQLSetDescField**または**SQLSetDescRec**.  
  
 アプリケーションを呼び出す場合**SQLGetData** SQL_C_NUMERIC 構造にデータを返す、既定の SQL_DESC_SCALE と SQL_DESC_PRECISION フィールドが使用されます。 既定値が許容できない場合は、アプリケーションを呼び出す必要があります**SQLSetDescRec**または**SQLSetDescField** 、フィールドを設定し、呼び出す**SQLGetData** で*TargetType* SQL_ARD_TYPE の記述子フィールドの値を使用するのです。  
  
 ときに**SQLPutData**が呼び出されると、呼び出しを使用して、実行時データ パラメーターまたは列に対応する記述子レコードの SQL_DESC_SCALE および SQL_DESC_PRECISION フィールドへの呼び出しに APD フィールドは**SQLExecute**または**SQLExecDirect**、または呼び出しのために ARD フィールド**SQLBulkOperations**または**SQLSetPos**です。
