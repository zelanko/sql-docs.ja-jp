---
title: "パラメーター値の設定 |Microsoft ドキュメント"
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
helpviewer_keywords: parameter values [ODBC]
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 726af8b2a7b4e9f0b630c95c45f512201fa1cf3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="setting-parameter-values"></a>パラメーター値の設定
パラメーターの値を設定するには、アプリケーションは単に、パラメーターにバインドされた変数の値を設定します。 重要ではありませんこの値が設定されている場合、ステートメントが実行される前に設定されている限り、します。 変数をバインドする、前後に、アプリケーションは、値を設定でき、必要に応じて何度値を変更することができます。 ステートメントを実行すると、ドライバーは単に、変数の現在の値を取得します。 これは、準備されたステートメントが複数回実行されたときに特に便利です。アプリケーションは、ステートメントが実行されるたびに、変数の一部またはすべての新しい値を設定します。 この例は、次を参照してください。[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)、このセクションで前述しました。  
  
 長さ/インジケーター バッファーが呼び出しでは、バインドされていたかどうか**SQLBindParameter**ステートメントを実行する前に、値は次のいずれかに設定する必要があります。  
  
-   バインドされた変数内のデータのバイト長。 ドライバーは、変数が文字またはバイナリである場合にのみ、この長さをチェック (*ValueType* SQL_C_CHAR または SQL_C_BINARY)。  
  
-   SQL_NTS です。 データは、null で終わる文字列です。  
  
-   SQL_NULL_DATA です。 データ値を NULL に、ドライバーは、バインドされた変数の値を無視します。  
  
-   SQL_DATA_AT_EXEC または SQL_LEN_DATA_AT_EXEC マクロの結果。 パラメーターの値に送信する**SQLPutData**です。 詳細については、次を参照してください。[長い形式のデータを送信する](../../../odbc/reference/develop-app/sending-long-data.md)、このセクションで後述します。  
  
 次の表は、バインドされた変数とパラメーター値のさまざまなアプリケーションで設定された長さ/インジケーター バッファーの値を示します。  
  
|パラメーター<br /><br /> value|パラメーター<br /><br /> (SQL)<br /><br /> データ型 (data type)|Variable (C)<br /><br /> データ型 (data type)|値します。<br /><br /> バインド<br /><br /> 変数 (variable)|値します。<br /><br /> 長さ/インジケーター<br /><br /> バッファー [d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC\0 [a]|SQL_NTS または 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10\0 [a]|SQL_NTS または 2|  
|午後 1|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0 [b]|--|  
|午後 1|SQL_TYPE_TIME|SQL_C_CHAR|{t ' 13: 00:00'} \0 [a]、[c]|SQL_NTS または 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a]「\0」は、null 終端文字を表します。 Null 終了文字が長さ/インジケーター バッファーの値は、SQL_NTS 場合にのみ必要です。  
  
 [この一覧に b] の数値は、TIME_STRUCT 構造体のフィールドに格納されている番号です。  
  
 [c] の文字列は、ODBC の日付のエスケープ句を使用します。 詳細については、次を参照してください。[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)です。  
  
 [d] ドライバーでは、SQL_NULL_DATA などの特殊な値であるかどうかを確認するには、この値を必ず確認する必要があります。  
  
 ドライバーの動作が実行時にパラメーター値は、ドライバーによって異なります。 必要に応じて、ドライバーは、値をバインドされた変数の C データ型とバイト長から SQL データ型、有効桁数、およびパラメーターの小数点以下桁数に変換します。 ほとんどの場合、ドライバーは、データ ソースに値を送信します。 場合によっては、値がテキストとして書式設定し、データ ソースに、ステートメントを送信する前に、SQL ステートメントに挿入します。
