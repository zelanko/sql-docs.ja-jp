---
title: オクテットの長さを転送 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 10/28/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4204b47816747506a5672241eeeef736eca54856
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302813"
---
# <a name="transfer-octet-length"></a>転送オクテット長
列の転送オクテット長は、データがデフォルトの C データ・タイプに転送されるときにアプリケーションに戻される最大バイト数です。 文字データの場合、転送オクテットの長さには、ヌル終了文字用のスペースは含まれません。 列の転送オクテットの長さは、データ ソースにデータを格納するために必要なバイト数と異なる場合があります。  
  
 次の表に、各 ODBC SQL データ型に定義された転送オクテット長を示します。  
  
|SQL タイプ識別子|長さ|  
|-------------------------|------------|  
|すべての文字タイプ[a]|列の定義された長さ、または (可変型の場合) の最大長 (バイト単位)。 これは、記述子フィールドSQL_DESC_OCTET_LENGTHと同じ値です。|  
|SQL_DECIMAL<br />SQL_NUMERIC|文字セットが ANSI の場合、このデータの文字表現を保持するために必要なバイト数。 データは文字ストリングとして戻され、数字、符号、および小数点に必要なため、これは最大桁数に 2 を加えた値です。 例えば、NUMERIC(10,3) として定義された列の転送長は 12 です。|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT| 8 |  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|すべてのバイナリ型[a]|定義された (固定型の場合) または最大 (変数型の場合) 文字数を保持するために必要なバイト数。|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (SQL_DATE_STRUCTまたはSQL_TIME_STRUCT構造のサイズ)。|  
|SQL_TYPE_TIMESTAMP|16(SQL_TIMESTAMP_STRUCT構造の大きさ)。|  
|すべての間隔データ型|34(間隔構造のサイズ)。|  
|SQL_GUID|16 (GUID 構造体のサイズ)。|  
| &nbsp; | &nbsp; |

 [a] ドライバーが可変型の列またはパラメーターの長さを決定できない場合、SQL_NO_TOTAL返します。
