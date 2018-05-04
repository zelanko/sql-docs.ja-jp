---
title: 間隔のデータ型の有効桁数 |Microsoft ドキュメント
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
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73acf5a46768b11b0eb223327c1fa1bcf0e49f68
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="interval-data-type-precision"></a>Interval データ型の精度
Interval データ型の有効桁数には、有効桁数、間隔の有効桁数、および秒の有効桁数を先頭の間隔が含まれています。  
  
 間隔の先頭のフィールドは、符号付きの型です。 先頭のフィールドの桁の数字の最大数と呼ばれる数量によって決まります*先頭の有効桁数、間隔*データ型の宣言の一部であります。 たとえば、宣言: 間隔 HOUR(5) 分に 5; の有効桁数を先頭間隔時刻フィールドには、99999 を通じて –99999 から値を取得できます。 有効桁数を先頭の間隔は、記述子レコードの SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドに含まれます。  
  
 Interval データ型で構成されたフィールドの一覧と呼びます*間隔精度*です。 "Precision"という用語が示すように、数値の値はありません。 2 番目の interval 型の有効桁数、間隔を日、時、リストはたとえば、分、秒です。 この値を保持する記述子フィールドはありません。間隔の有効桁数は、interval データ型で常に決定できます。  
  
 2 番目のフィールドを持つ任意の間隔データ型が、*秒の有効桁数*です。 これは、秒の値の小数部では許可の 10 進数です。 これは、有効桁数が小数点の前に数字の数を示す他のデータ型と異なる。 Interval データ型の秒の有効桁数が、小数点の数字の数。 たとえば、秒の有効桁数は 6 に設定されている場合番号 123456 小数フィールドでは解釈.123456 と番号 1230.001230 として解釈されるようです。 他のデータ型のこの呼びますスケールします。 間隔の秒の有効桁数は、記述子の SQL_DESC_PRECISION フィールドに含まれます。 SQL 間隔の値の秒の小数部のコンポーネントの有効桁数がどのような C 間隔の構造体に格納できるよりも大きい場合はドライバーで定義されている SQL の間隔の秒の小数部の値が丸められますまたは C に変換すると切り捨てかどうか間隔の構造体。  
  
 SQL_DESC_TYPE フィールドが SQL_INTERVAL に設定されている SQL_DESC_CONCISE_TYPE フィールドは、interval データ型に設定されているときに、SQL_DESC_DATETIME_INTERVAL_CODE が interval データ型のコードに設定されているとします。 SQL_DESC_DATETIME_INTERVAL_PRECISION フィールドは自動的に第 2 の既定の間隔先頭の精度に設定し、SQL_DESC_PRECISION フィールドは自動的に 6 の既定の間隔 (秒) の有効桁数に設定します。 これらの値のいずれかの情報が適切でない場合、アプリケーションを呼び出すことによって、記述子フィールドに明示的に設定する必要があります**SQLSetDescField**です。
