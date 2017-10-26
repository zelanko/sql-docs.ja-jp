---
title: "長い形式のデータおよび SQLSetPos SQLBulkOperations |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 308e1ad6f2d99a0a6b7e73d8a82ac62362fea9a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>長い形式のデータおよび SQLSetPos SQLBulkOperations
行の更新時に長いデータを送信できるように SQL ステートメントのパラメーターを持つ場合は、 **SQLBulkOperations**または**SQLSetPos**を持つ行を挿入するときに、または**SQLBulkOperations**. 複数回呼び出すと、部分にデータが送信される**SQLPutData**です。 実行時にデータを送信する列と呼ばれる*実行時データ列*です。  
  
> [!NOTE]  
>  アプリケーションには実行時に任意のデータ型を送信することが実際にできます。 **SQLPutData**部分の文字とバイナリ データのみを送信できますが、します。 ただし、データがそれほど 1 つのバッファーに収まらない場合は通常を使用する理由**SQLPutData**です。 バッファーをバインドし、バッファーからデータを取得するドライバーをはるかに簡単です。  
  
 アプリケーションが呼び出す前に列をバインドする必要がありますので、通常の長いデータ列はバインドされていない、 **SQLBulkOperations**または**SQLSetPos**呼び出した後、これをアンバインドし、 **SQLBulkOperations**または**SQLSetPos**です。 列をバインドする必要があります**SQLBulkOperations**または**SQLSetPos**バインドされた列でのみ動作し、バインドする必要がありますように**SQLGetData**データを取得するために使用します。列です。  
  
 実行時にデータを送信するには、アプリケーションは次のとおり  
  
1.  データ値ではなく、行セットのバッファーには、32 ビット値を配置します。 アプリケーションを使用すると、列の数やデータを含むファイルのハンドルなどの意味のある値に設定する必要がありますので、後で、アプリケーションにこの値が返されます。  
  
2.  SQL_LEN_DATA_AT_EXEC の結果に長さ/インジケーター バッファーの値を設定 (*長さ*) マクロです。 この値は、ドライバーに送信されるパラメーターのデータを示します**SQLPutData**です。 *長さ*長い形式のデータのバイト数が送信されるため、領域をあらかじめ割り当てるには知っている必要があるデータ ソースに長いデータを送信するときに値が使用されます。 データ ソースにこの値は、アプリケーションの呼び出しが必要かどうかを判断する**SQLGetInfo** SQL_NEED_LONG_DATA_LEN オプションを使用します。 すべてのドライバーは、このマクロをサポートする必要があります。データ ソースにバイトの長さが必要としない場合、ドライバーによって無視できます。  
  
3.  呼び出し**SQLBulkOperations**または**SQLSetPos**です。 ドライバーは、長さ/インジケーター バッファーが、SQL_LEN_DATA_AT_EXEC の結果を含むことを検出します。 (*長さ*) マクロと関数の戻り値として SQL_NEED_DATA を返します。  
  
4.  呼び出し**SQLParamData** SQL_NEED_DATA への応答には、値を返します。 長い形式のデータを送信する必要がある場合**SQLParamData** SQL_NEED_DATA を返します。 指すバッファーに、 *ValuePtrPtr*引数、ドライバーは、行セットのバッファーに、アプリケーションが配置されて一意の値を返します。 アプリケーションが対象となるデータを送信するには、どの列を調べるに値を使用して 1 つ以上の実行時データ列がある場合ドライバーは、特定の順序で実行時データ列のデータを要求する必要はありません。  
  
5.  呼び出し**SQLPutData**ドライバーに、列のデータを送信します。 アプリケーションを呼び出す場合は、列のデータは、長い形式のデータの場合は、多くの場合とに 1 つのバッファーに収まらない、 **SQLPutData**パーツ; でデータを送信するには、繰り返し、ドライバーとデータ ソース、データを再構成するための責任です。 アプリケーションでは、null で終わる文字列データを渡す、ドライバーまたはデータ ソースは、再構築プロセスの一部として null 終端文字を削除する必要があります。  
  
6.  呼び出し**SQLParamData**のすべての列のデータ、送信されたことを示すためにもう一度です。 ドライバーが SQL_NEED_DATA と、次の実行時データ列の一意の値を返します、データが送信されていないすべての実行時データ列がある場合アプリケーションは、手順 5 を返します。 すべての実行時データ列のデータが送信された場合、行のデータはデータ ソースに送信します。 **SQLParamData**返し SQL_SUCCESS または SQL_SUCCESS_WITH_INFO が返す任意の SQLSTATE を**SQLBulkOperations**または**SQLSetPos**返すことができます。  
  
 後に**SQLBulkOperations**または**SQLSetPos** SQL_NEED_DATA を返しますあり、データが最後の実行時データ列を完全に送信される前に、ステートメントで状態のデータの必要があります。 この状態で、アプリケーションはのみ呼び出すことができます**SQLPutData**、 **SQLParamData**、 **SQLCancel**、 **SQLGetDiagField**、または**SQLGetDiagRec**; 他のすべての関数を返す SQLSTATE HY010 (関数のシーケンス エラーです)。 呼び出す**SQLCancel**ステートメントの実行をキャンセルし、以前の状態を返します。 詳細については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。

