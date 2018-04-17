---
title: 長い形式のデータを送信する |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- long data [ODBC]
- sending long data [ODBC]
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3dd5ec4edf58bb29772ca565109e5d9c79a3304
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sending-long-data"></a>長い形式のデータを送信します。
Dbms 定義*長いデータ*任意の文字または文字で 254 文字などの特定のサイズ以上のバイナリ データとして。 項目が、長いテキスト ドキュメントまたはビットマップを表す場合など、メモリ内の長い形式のデータ項目全体を格納できない可能性があります。 このようなデータは、1 つのバッファーに格納されることはできません、ので、データ ソースに送信ドライバーを使用してパーツに**SQLPutData**ステートメントが実行されるとします。 実行時にデータを送信するパラメーターと呼ばれる*実行時データ パラメーター*です。  
  
> [!NOTE]  
>  アプリケーションが実行時に任意のデータ型を実際に送信できる**SQLPutData**部分の文字とバイナリ データのみを送信できますが、します。 ただし、データがそれほど 1 つのバッファーに収まらない場合は通常を使用する理由**SQLPutData**です。 バッファーをバインドし、バッファーからデータを取得するドライバーをはるかに簡単です。  
  
 実行時にデータを送信するには、アプリケーションには、次の操作を実行します。  
  
1.  パラメーターを識別する 32 ビット値を渡す、 *ParameterValuePtr*引数**SQLBindParameter**バッファーのアドレスを渡すのではなくです。 この値は、ドライバーでは分析されません。 アプリケーションが意味する必要があります、後で、アプリケーションに返されるされます。 たとえば、パラメーターの数やデータを含むファイルのハンドルがあることがあります。  
  
2.  長さ/インジケーター バッファーのアドレスを渡す、 *StrLen_or_IndPtr*の引数**SQLBindParameter**です。  
  
3.  生成される場合や、SQL_LEN_DATA_AT_EXEC の結果を格納 (*長さ*) 長さ/インジケーター バッファー内のマクロです。 ドライバーに送信されるパラメーターのデータにこれらの値の両方を示す**SQLPutData**です。 SQL_LEN_DATA_AT_EXEC (*長さ*) 長い形式のデータを長い形式のデータのバイト数が送信されるため、領域をあらかじめ割り当てるには知っている必要があるデータ ソースに送信するときに使用します。 データ ソースは、この値を必要とする場合、アプリケーションは呼び出しを決定する**SQLGetInfo** SQL_NEED_LONG_DATA_LEN オプションを使用します。 すべてのドライバーは、このマクロをサポートする必要があります。データ ソースにバイトの長さが必要としない場合、ドライバーによって無視できます。  
  
4.  呼び出し**SQLExecute**または**SQLExecDirect**です。 長さ/インジケーター バッファーには、SQL_DATA_AT_EXEC 値や、SQL_LEN_DATA_AT_EXEC の結果が含まれているドライバーの検出 (*長さ*) マクロと関数の戻り値として SQL_NEED_DATA を返します。  
  
5.  呼び出し**SQLParamData** SQL_NEED_DATA への応答には、値を返します。 長い形式のデータを送信する必要がある場合**SQLParamData** SQL_NEED_DATA を返します。 指すバッファーに、 *ValuePtrPtr*引数、ドライバーは、実行時データ パラメーターを識別する値を返します。 のデータを送信するのにを識別するのに、アプリケーションがこの値を使用する必要があります 1 つ以上の実行時データ パラメーターがある場合ドライバーは、特定の順序で実行時データ パラメーターのデータを要求する必要はありません。  
  
6.  呼び出し**SQLPutData**ドライバーに、パラメーターのデータを送信します。 アプリケーションを呼び出す場合は、パラメーターのデータは、長い形式のデータの場合は、多くの場合とに 1 つのバッファーに収まらない、 **SQLPutData**パーツ; でデータを送信するには、繰り返し、ドライバーとデータ ソース、データを再構成するための責任です。 アプリケーションでは、null で終わる文字列データを渡す、ドライバーまたはデータ ソースは、再構築プロセスの一部として null 終端文字を削除する必要があります。  
  
7.  呼び出し**SQLParamData**のすべてのパラメーターのデータ、送信されたことを示すためにもう一度です。 データが送信されていない任意の実行時データ パラメーターがある、ドライバーは SQL_NEED_DATA と次のパラメーターを識別する値を返しますアプリケーションは、手順 6 を返します。 すべての実行時データ パラメーターのデータが送信された場合、ステートメントが実行されます。 **SQLParamData**返し SQL_SUCCESS または SQL_SUCCESS_WITH_INFO を返す任意の戻り値または診断を**SQLExecute**または**SQLExecDirect**返すことができます。  
  
 後に**SQLExecute**または**SQLExecDirect** SQL_NEED_DATA を返しますあり、データが最後の実行時データ パラメーターに完全に送信される前に、ステートメントで状態のデータの必要があります。 アプリケーションがのみ呼び出すことができます、ステートメントは、データの必要がある状態では、 **SQLPutData**、 **SQLParamData**、 **SQLCancel**、 **SQLGetDiagField**、または**SQLGetDiagRec**; 他のすべての関数を返す SQLSTATE HY010 (関数のシーケンス エラーです)。 呼び出す**SQLCancel**ステートメントの実行をキャンセルし、以前の状態を返します。 詳細については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
 実行時にデータを送信するの例は、次を参照してください。、 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)関数の説明。
