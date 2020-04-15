---
title: ロングデータの送信 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- sending long data [ODBC]
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aeeeb716aa2f9a72338f3aeb586dffce86f84069
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304183"
---
# <a name="sending-long-data"></a>長い形式のデータの送信
DBMS は、*長いデータ*を、254 文字など、特定のサイズを超える任意の文字またはバイナリ データとして定義します。 項目が長いテキスト ドキュメントやビットマップを表す場合など、長いデータの項目全体をメモリに格納できない場合があります。 このようなデータは 1 つのバッファーに格納できないため、ステートメントの実行時に、データ ソースは**SQLPutData**を使用してドライバーに送信します。 実行時にデータが送信されるパラメータは、*実行時データパラメータ*と呼ばれます。  
  
> [!NOTE]  
>  アプリケーションは、実際には**SQLPutData**を使用して実行時に任意の種類のデータを送信できますが、文字データとバイナリ データのみを一部で送信できます。 ただし、データが 1 つのバッファーに収まるほど小さい場合は、 **SQLPutData**を使用する理由が一般的にありません。 バッファーをバインドし、ドライバーがバッファーからデータを取得する方がはるかに簡単です。  
  
 実行時にデータを送信するために、アプリケーションは次のアクションを実行します。  
  
1.  バッファーのアドレスを渡すのではなく **、SQLBindParameter**の*引数でパラメーター*を識別する 32 ビット値を渡します。 この値は、ドライバーによって分析されません。 後でアプリケーションに戻されるので、アプリケーションにとって何かを意味するはずです。 たとえば、パラメーターの数や、データを含むファイルのハンドルなどです。  
  
2.  **sqlBindParameter**の*StrLen_or_IndPtr*引数に長さ/インジケーター バッファーのアドレスを渡します。  
  
3.  SQL_DATA_AT_EXEC、または*SQL_LEN_DATA_AT_EXEC(length)* マクロの結果を、長さ/インジケーター バッファーに格納します。 これらの値はどちらも、パラメータのデータが**SQLPutData**と共に送信されることをドライバに示します。 SQL_LEN_DATA_AT_EXEC(*length*) は、長いデータをデータ ソースに送信するときに使用され、そのデータが領域を事前に割り当てることができるように、送信される長いデータのバイト数を知る必要があります。 データ ソースがこの値を必要とするかどうかを判断するには、アプリケーションは SQL_NEED_LONG_DATA_LEN オプションを指定して**SQLGetInfo**を呼び出します。 すべてのドライバーは、このマクロをサポートする必要があります。データ ソースがバイト長を必要としない場合、ドライバーはそれを無視できます。  
  
4.  **を**呼び出**します。** ドライバーは、長さ/インジケーター バッファーがSQL_DATA_AT_EXEC値または*SQL_LEN_DATA_AT_EXEC(length)* マクロの結果を含むを検出し、関数の戻り値としてSQL_NEED_DATAを返します。  
  
5.  SQL_NEED_DATA戻り値に応答して**SQLParamData**を呼び出します。 長いデータを送信する必要がある場合は **、SQLParamData は**SQL_NEED_DATAを返します。 *ValuePtrPtr*引数によって指されるバッファーでは、ドライバーは実行時のデータ パラメーターを識別する値を返します。 実行時のデータパラメーターが複数ある場合、アプリケーションはこの値を使用して、データを送信するパラメーターを決定する必要があります。ドライバーは、特定の順序で実行時データ パラメーターのデータを要求する必要はありません。  
  
6.  **SQLPutData**を呼び出して、パラメーター データをドライバーに送信します。 長いデータの場合と同様に、パラメーター データが単一のバッファーに収まらない場合、アプリケーションは**SQLPutData**を繰り返し呼び出してデータを部分的に送信します。データを再構成するのは、ドライバーとデータ ソースによって行われます。 アプリケーションが null で終わる文字列データを渡す場合、ドライバーまたはデータ ソースは、再アセンブリ プロセスの一部として null 終端文字を削除する必要があります。  
  
7.  **SQLParamData を**再度呼び出して、パラメーターのすべてのデータを送信したことを示します。 データが送信されていない実行時データ パラメーターがある場合、ドライバーは、SQL_NEED_DATAと次のパラメーターを識別する値を返します。アプリケーションはステップ 6 に戻ります。 すべての実行時データパラメータに対してデータが送信されている場合、ステートメントが実行されます。 **SQLParamData は**SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返し **、SQLExecute**または**SQLExecDirect**が返すことができる戻り値または診断を返すことができます。  
  
 **SQLExecute**または**SQLExecDirect**がSQL_NEED_DATAを返した後、最後の実行時データ パラメーターのデータが完全に送信される前に、ステートメントは必要なデータ状態になります。 ステートメントが必要なデータ状態にある場合、アプリケーションは SQLPutData **、SQLParamData、SQLCancel、SQLGetDiagField** **SQLPutData**、または**SQLGetDiagRec**のみを呼び出すことができます。 **SQLCancel** **SQLGetDiagField**その他のすべての関数は、SQLSTATE HY010 (関数シーケンスエラー) を返します。 **SQLCancel**を呼び出すと、ステートメントの実行がキャンセルされ、前の状態に戻ります。 詳細については、「[付録 B : ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。  
  
 実行時にデータを送信する例については[、SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)関数の説明を参照してください。
