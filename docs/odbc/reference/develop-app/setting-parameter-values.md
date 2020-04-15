---
title: パラメータ値の設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter values [ODBC]
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 923fd57f4308fb72aca2f829ccb9d7b884c12546
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299832"
---
# <a name="setting-parameter-values"></a>パラメーターの値の設定
パラメーターの値を設定するために、アプリケーションは、パラメーターにバインドされた変数の値を設定するだけです。 この値を設定する場合、ステートメントが実行される前に設定されている限り、重要ではありません。 アプリケーションは、変数をバインドする前または後に値を設定でき、必要な回数だけ値を変更できます。 ステートメントが実行されると、ドライバーは、変数の現在の値を取得するだけです。 これは、準備済みステートメントが複数回実行される場合に特に便利です。アプリケーションは、ステートメントが実行されるたびに、一部またはすべての変数に新しい値を設定します。 この例については、このセクションの前の「[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)」を参照してください。  
  
 **SQLBindParameter**の呼び出しで長さ/インジケーター バッファーがバインドされている場合は、ステートメントを実行する前に、次のいずれかの値に設定する必要があります。  
  
-   バインドされた変数のデータのバイト長。 ドライバーは、変数が文字またはバイナリ *(ValueType*がSQL_C_CHARまたはSQL_C_BINARY) の場合にのみ、この長さをチェックします。  
  
-   SQL_NTS。 データは NULL で終わる文字列です。  
  
-   SQL_NULL_DATA。 データ値は NULL であり、ドライバーはバインドされた変数の値を無視します。  
  
-   SQL_LEN_DATA_AT_EXEC マクロのSQL_DATA_AT_EXECまたは結果。 パラメータの値は**SQLPutData**と共に送信されます。 詳細については、このセクションの後半の「[長いデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)」を参照してください。  
  
 次の表は、バインドされた変数の値と、アプリケーションがさまざまなパラメーター値に設定する長さ/インジケーター バッファーを示しています。  
  
|パラメーター<br /><br /> value|パラメーター<br /><br /> (SQL)<br /><br /> データ型 (data type)|変数 (C)<br /><br /> データ型 (data type)| の値<br /><br /> バインド<br /><br /> 可変| の値<br /><br /> 長さ/インジケータ<br /><br /> バッファ[d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC\0[a]|SQL_NTSまたは3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10\0[a]|SQL_NTSまたは2|  
|午後1時|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0[b]|--|  
|午後1時|SQL_TYPE_TIME|SQL_C_CHAR|{t '13:00:00'}\0[a]、[c]|SQL_NTSまたは14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] "\0" は、NULL 終端文字を表します。 ヌル終了文字は、長さ/標識バッファー内の値がSQL_NTS場合にのみ必要です。  
  
 [b] このリストの数字は、TIME_STRUCT構造のフィールドに格納されている数値です。  
  
 [c] 文字列は ODBC 日付エスケープ句を使用します。 詳細については、「[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)」を参照してください。  
  
 [d] ドライバーは、SQL_NULL_DATAなどの特別な値であるかどうかを確認するには、常にこの値をチェックする必要があります。  
  
 実行時にドライバーがパラメーター値を使用して行うことは、ドライバーに依存します。 必要に応じて、ドライバーは、C データ型とバインドされた変数のバイト長から SQL データ型、精度、およびパラメーターのスケールに値を変換します。 ほとんどの場合、ドライバーは、データ ソースに値を送信します。 場合によっては、値をテキストとしてフォーマットし、SQL ステートメントに挿入してから、データ ソースにステートメントを送信します。
