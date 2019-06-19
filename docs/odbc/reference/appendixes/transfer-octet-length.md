---
title: 転送オクテット長 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- data types [ODBC], transfer octet length
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8f64172685c42a5dde8de9027c8c7e621ddd9f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735068"
---
# <a name="transfer-octet-length"></a>転送オクテット長
列の転送オクテット長は、その既定の C データ型にデータが転送されるときに、アプリケーションに返されるバイトの最大数です。 文字データの転送オクテット長に null 終端文字のための領域は含まれません。 列の転送オクテット長は、データ ソースにデータを格納するために必要なバイト数よりも異なる可能性があります。  
  
 各 ODBC SQL データ型に対して定義されている転送オクテット長は、次の表に示します。  
  
|SQL 型識別子|長さ|  
|-------------------------|------------|  
|すべての文字の種類 [a]|定義済みまたは (変数の型) の最大長 (バイト単位) 列のします。 これは、記述子フィールド SQL_DESC_OCTET_LENGTH と同じ値です。|  
|SQL_DECIMAL<br />SQL_NUMERIC|文字セットが、ANSI の場合、このデータの文字表現を保持するために必要なバイト数と文字セットが UNICODE の場合この番号 2 回です。 これは、データが文字の文字列として返され、数字、符号および小数点 10 進数の文字が必要なため、数字と、2 つの最大数です。 たとえば、NUMERIC(10,3) として定義されている列の転送の長さは 12 です。|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT|文字セットが、ANSI の場合、このデータの文字表現を保持するために必要なバイト数と、既定でこのデータ型が文字列として返されるために、文字セットが、UNICODE の場合この番号 2 回。 文字の表現は、20 文字で構成されます。19 桁の数字、記号、署名されている場合、または署名されていない場合、20 桁の数字。 そのため、長さは 20 です。|  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|[A] すべてのバイナリ型|(固定型) の定義された保持するために必要なバイトまたは (変数の型) の最大文字数の数。|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (SQL_DATE_STRUCT または SQL_TIME_STRUCT 構造体のサイズ)。|  
|SQL_TYPE_TIMESTAMP|16 (SQL_TIMESTAMP_STRUCT 構造体のサイズ)。|  
|間隔のすべてのデータ型|34 (interval 構造体のサイズ)。|  
|SQL_GUID|16 (GUID 構造体のサイズ)。|  
  
 [a] 変数の型の列またはパラメーターの長さを判断できないのは、ドライバー、SQL_NO_TOTAL が返されます。
