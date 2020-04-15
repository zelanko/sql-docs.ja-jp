---
title: 長いデータと SQL セットポスと SQL 一括操作 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4bc6c5d2da2f796a7c312971635fc36bc2fae8af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287866"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>長い形式のデータ、SQLSetPos および SQLBulkOperations
SQL ステートメントのパラメーターの場合と同様に **、SQLBulkOperations**または**SQLSetPos**を使用して行を更新するとき、または**SQLBulkOperations**を使用して行を挿入するときに長いデータを送信できます。 データは **、SQLPutData**への複数の呼び出しで、部分的に送信されます。 実行時にデータが送信される列は、 *"実行時データ列*" と呼ばれます。  
  
> [!NOTE]  
>  アプリケーションは、実際には**SQLPutData**を使用して実行時に任意の種類のデータを送信できますが、文字データとバイナリ データのみを一部で送信できます。 ただし、データが 1 つのバッファーに収まるほど小さい場合は、 **SQLPutData**を使用する理由が一般的にありません。 バッファーをバインドし、ドライバーがバッファーからデータを取得する方がはるかに簡単です。  
  
 長いデータ列は通常バインドされないため、アプリケーションは**SQLBulkOperations**または**SQLSetPos**を呼び出す前に列をバインドし **、SQLBulkOperations**または**SQLSetPos**を呼び出した後にバインドを解除する必要があります。 **SQLBulkOperations**または**SQLSetPos**はバインドされた列でのみ動作し **、SQLGetData**を使用して列からデータを取得できるようにバインドを解除する必要があるため、列をバインドする必要があります。  
  
 実行時にデータを送信するために、アプリケーションは次の処理を行います。  
  
1.  データ値の代わりに行セット バッファーに 32 ビット値を配置します。 この値は後でアプリケーションに返されるため、アプリケーションは列の数やデータを含むファイルのハンドルなどの意味のある値に設定する必要があります。  
  
2.  長さ/インジケーター バッファーの値を SQL_LEN_DATA_AT_EXEC(*長さ*) マクロの結果に設定します。 この値は、パラメーターのデータが**SQLPutData**と共に送信されることをドライバーに示します。 *長さ*値は、長いデータをデータ ソースに送信するときに使用され、そのデータが領域を事前に割り当てることができるように、送信される長いデータのバイト数を知る必要があります。 データ ソースがこの値を必要とするかどうかを判断するには、アプリケーションはSQL_NEED_LONG_DATA_LEN オプションを指定して**SQLGetInfo**を呼び出します。 すべてのドライバーは、このマクロをサポートする必要があります。データ ソースがバイト長を必要としない場合、ドライバーはそれを無視できます。  
  
3.  を呼び出します**SQLSetPos****。** ドライバーは、長さ/インジケーター バッファーがSQL_LEN_DATA_AT_EXEC(*length*) マクロの結果を含むを検出し、関数の戻り値としてSQL_NEED_DATAを返します。  
  
4.  SQL_NEED_DATA戻り値に応答して**SQLParamData**を呼び出します。 長いデータを送信する必要がある場合は **、SQLParamData は**SQL_NEED_DATAを返します。 *ValuePtrPtr*引数によって指されるバッファーでは、ドライバーは、アプリケーションが行セット バッファーに配置した一意の値を返します。 実行時に複数のデータ列がある場合、アプリケーションはこの値を使用して、データを送信する列を決定します。ドライバーは、特定の順序で実行時のデータ列のデータを要求する必要はありません。  
  
5.  列データをドライバーに送信する**SQLPutData**を呼び出します。 列データが単一のバッファーに収まらない場合 (長いデータの場合が多い場合と同様) は、アプリケーションは**SQLPutData**を繰り返し呼び出してデータを部分的に送信します。データを再構成するのは、ドライバーとデータ ソースによって行われます。 アプリケーションが null で終わる文字列データを渡す場合、ドライバーまたはデータ ソースは、再アセンブリ プロセスの一部として null 終端文字を削除する必要があります。  
  
6.  **SQLParamData を**再度呼び出して、列のすべてのデータを送信したことを示します。 データが送信されていない実行時データ列がある場合、ドライバーは次の実行時データ列のSQL_NEED_DATAと一意の値を返します。アプリケーションはステップ 5 に戻ります。 実行データ列のすべてのデータが送信されている場合、その行のデータはデータ ソースに送信されます。 **次に、SQLParamData は**SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返し **、SQLBulk オペレーション**または**SQL セットポス**が返すことができる任意の SQLSTATE を返すことができます。  
  
 **SQLBulkOperations**または**SQLSetPos**がSQL_NEED_DATAを返した後、最後に実行されたデータ列に対してデータが完全に送信される前に、ステートメントは必要なデータ状態になります。 この状態では、アプリケーションは **、SQLPutData** **、SQLParamData、SQL**キャンセル **、SQLGetDiagField**、または**SQLGetDiagRec**のみを呼び出すことができます。 **SQLCancel**その他のすべての関数は、SQLSTATE HY010 (関数シーケンスエラー) を返します。 **SQLCancel**を呼び出すと、ステートメントの実行がキャンセルされ、前の状態に戻ります。 詳細については、「[付録 B : ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。
