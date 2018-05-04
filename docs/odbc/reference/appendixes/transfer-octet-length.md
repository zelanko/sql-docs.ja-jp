---
title: 転送オクテット長 |Microsoft ドキュメント
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
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- data types [ODBC], transfer octet length
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59b790845ee6360edcb5c5ea796e9ad910c397a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="transfer-octet-length"></a>転送のオクテットの長さ
転送オクテット長の列は、既定の C データ型にデータが転送されるときに、アプリケーションに返されるバイトの最大数です。 文字データの転送オクテット長に null 終端文字のための領域は含まれません。 列の転送のオクテットの長さは、データ ソースのデータの格納に必要なバイト数よりも異なる可能性があります。  
  
 各 ODBC SQL データ型に対して定義された転送のオクテットの長さは、次の表に表示されます。  
  
|SQL 型の識別子|長さ|  
|-------------------------|------------|  
|すべての文字の種類 [a]|定義されたまたは、(変数の型) 列の最大長、(バイト単位)。 これは、記述子フィールド SQL_DESC_OCTET_LENGTH と同じ値です。|  
|SQL_DECIMAL<br />SQL_NUMERIC|文字セットが、ANSI の場合、このデータの文字の表現を保持するために必要なバイト数と文字セットが UNICODE の場合この番号 2 回クリックします。 これは、データが文字の文字列として返され、文字、数字、符号および小数点に必要なために、数字と、2 つの最大数です。 たとえば、NUMERIC(10,3) として定義されている列の転送の長さは 12 です。|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT|文字セットが、ANSI の場合、このデータの文字の表現を保持するために必要なバイト数と文字セットは、このデータ型が既定では、文字の文字列として返されるために、UNICODE が場合この番号 2 回クリックします。 文字形式を 20 文字から成る: 19。 数字、記号、署名されている場合または署名されていない場合、20 桁の数字です。 したがって、長さは 20 です。|  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|[A] すべてのバイナリ型|押したまま、定義されている (固定の型) に必要なバイトまたは (変数の型) の最大文字数の数。|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (SQL_DATE_STRUCT または SQL_TIME_STRUCT 構造体のサイズ)。|  
|SQL_TYPE_TIMESTAMP|16 (SQL_TIMESTAMP_STRUCT 構造体のサイズ)。|  
|すべての interval データ型|34 (間隔構造体のサイズ)。|  
|SQL_GUID|16 (GUID 構造体のサイズ)。|  
  
 [a] の変数の型の列またはパラメーターの長さを判断できないのは、ドライバー場合、SQL_NO_TOTAL が返されます。
