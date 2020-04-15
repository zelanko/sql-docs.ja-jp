---
title: 結果データのフェッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLFetchScroll function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], fetching
- SQLBindCol function
- result sets [ODBC], fetching
- fetching [ODBC]
- ODBC data types, fetching
- SQLFetch function
- SQL Server Native Client ODBC driver, data types
- SQLGetData function
ms.assetid: b289c7fb-5017-4d7e-a2d3-19401e9fc4cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1d9fdfcd7bcc4f86afacc75dff5b40b77bb7b2a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304616"
---
# <a name="fetching-result-data"></a>結果データのフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC アプリケーションでは、結果データのフェッチを 3 つの方法で実行できます。  
  
 最初のオプションは[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)に基づいています。 結果セットをフェッチする前に、アプリケーションは**SQLBindCol**を使用して、結果セット内の各列をプログラム変数にバインドします。 列がバインドされた後、ドライバーは、アプリケーションが SQLFetch または**SQLFetchScroll**を呼び出すたびに、結果セット列にバインドされた[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)変数に現在の行のデータを転送します。 結果セット列のデータ型とプログラム変数のデータ型が異なる場合、ドライバーによってデータ変換が処理されます。 アプリケーションで 1 より大きい値SQL_ATTR_ROW_ARRAY_SIZE設定されている場合は、結果列を変数の**配列にバインド**できます。  
  
 2 番目のオプションは[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)に基づいています。 アプリケーションは、結果セット列をプログラム変数にバインドするために**SQLBindCol**を使用しません。 **SQLFetch**を呼び出すたびに、アプリケーションは結果セットの各列に対して**SQLGetData**を 1 回呼び出します。 **SQLGetData**は、特定の結果セット列から特定のプログラム変数にデータを転送し、列と変数のデータ型を指定するドライバーに指示します。 そのため、結果列のデータ型とプログラム変数のデータ型が異なる場合は、ドライバーでデータを変換できます。 **テキスト****、ntext、** および**image**の各列は、通常は大きすぎてプログラム変数に収まりきりませんが、 **SQLGetData**を使用して取得できます。 結果列**text**のテキスト **、ntext、** または**image**のデータがプログラム変数より大きい場合 **、SQLGetData**はSQL_SUCCESS_WITH_INFOと SQLSTATE 01004 (文字列データ、右切り捨て) を返します。 **SQLGetData**の連続した呼び出しは **、テキスト**または**イメージ**データの連続したチャンクを返します。 データの末尾に達すると **、sqlGetData**はSQL_SUCCESSを返します。 SQL_ATTR_ROW_ARRAY_SIZE に 1 よりも大きい値を指定すると、フェッチのたびに行セットが返されます。 **SQLGetData**を使用する前に、まず**SQLSetPos**を使用して、行セット内の特定の行を現在の行として指定する必要があります。  
  
 3 番目のオプションは **、SQLBindCol**と**SQLGetData**を組み合わせて使用することです。 たとえば、アプリケーションは、結果セットの最初の 10 列をバインドし、フェッチごとに**SQLGetData**を 3 回呼び出して、3 つの非バインド列からデータを取得できます。 通常、この値は、結果セットに 1 つ以上の**テキスト**列または**イメージ**列が含まれている場合に使用されます。  
  
 結果セットに設定されたカーソル オプションによっては、アプリケーションは**SQLFetchScroll**のスクロール オプションを使用して、結果セットをスクロールすることもできます。  
  
 **SQLBindCol を**使用して結果セット列をプログラム変数にバインドすると **、SQLBindCol**によって ODBC ドライバーがメモリを割り当てるので、コストが高くなります。 結果列を変数にバインドすると[、SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を呼び出してステートメント ハンドルを解放するか、*または fOption*を SQL_UNBIND に設定して[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)を呼び出すまで、そのバインディングは有効です。 バインドは、ステートメントが完了しても自動的には元に戻りません。  
  
 このロジックにより、異なるパラメーターを指定して同じ SELECT ステートメントを何度も実行することで、効率を上げることができます。 結果セットは同じ構造を保持するため、結果セットを 1 回バインドして、すべての SELECT ステートメントを処理してから、最後の実行後に SQL_UNBIND に設定された*fOption*を指定して**SQLFreeStmt**を呼び出すことができます。 以前のバインディングを解放するために*fOption*を設定して**sqlFreeStmt**を呼び出さずに、結果セット内の列をバインドするために**SQLBindCol**を呼び出SQL_UNBINDしないでください。  
  
 **SQLBindCol**を使用する場合は、行方向または列方向のバインドを行うことができます。 行方向のバインドの方が、列方向のバインドよりも処理がやや高速になります。  
  
 **SQLGetData**を使用すると、結果セット列をバインドする代わりに、列ごとにデータを取得できます。 **SQLBindCol** 結果セットに含まれる行が数行しかない場合は **、SQLBindCol**の代わりに**SQLGetData**を使用する方が高速です。それ以外の場合は **、SQLBindCol**が最高のパフォーマンスを提供します。 常に同じ変数セットにデータを配置しない場合は、常に再バインドするのではなく **、SQLGetData**を使用する必要があります。 すべての列が**SQLBindCol**でバインドされた後、選択リストにある列に対してのみ**SQLGetData**を使用できます。 列は **、SQLGetData**を既に使用している列の後にも表示する必要があります。  
  
 **SQLGetData** **、SQLBindCol**、および[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)などのプログラム変数との間でデータを移動する ODBC 関数は、暗黙的なデータ型変換をサポートします。 たとえば、整数列を文字列プログラム変数にバインドするアプリケーションでは、プログラム変数にデータを格納する前に、ドライバーが自動的にそのデータを整数から文字に変換します。  
  
 アプリケーションでのデータ変換は最小限に抑える必要があります。 列やパラメーターは、アプリケーションでの処理にデータ変換が必要な場合を除き、同じデータ型のプログラム変数にバインドする必要があります。 ただし、あるデータ型から別のデータ型に変換する必要がある場合は、アプリケーションでのデータ変換よりもドライバーによるデータ変換の方が効率的です。 通常、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ネットワーク バッファーからアプリケーションの変数にデータを直接転送します。 データ変換を行うようにドライバーに要求すると、ドライバーはデータをバッファーに格納し、CPU サイクルを使用してデータを変換します。  
  
 プログラム変数は、**テキスト****、ntext、****およびイメージ**データを除き、列から転送されたデータを保持するのに十分な大きさである必要があります。 結果セットのデータを取得してそのデータを変数に格納するときに、その変数が小さすぎてデータを保持できない場合、ドライバーは警告を生成します。 その結果、ドライバーでは警告メッセージ用のメモリを割り当て、ドライバーとアプリケーションの両方で、警告メッセージの処理やエラーの処理に CPU サイクルが必要になります。 アプリケーションでは、取得するデータを保持するのに十分なサイズの変数を割り当てるか、選択リストで SUBSTRING 関数を使用して結果セット内の列のサイズを小さくする必要があります。  
  
 SQL_C_DEFAULT を使用して C 変数のデータ型を指定する場合は注意が必要です。 SQL_C_DEFAULT は、C 変数のデータ型と、列やパラメーターの SQL データ型を一致させることを指定します。 **SQL_C_DEFAULT ntext**、 **nchar**、または**nvarchar**列に指定すると、Unicode データがアプリケーションに返されます。 そのため、アプリケーションが Unicode データを処理するようにコーディングされていないと、さまざまな問題が発生する可能性があります。 **一意識別子**(SQL_GUID) データ型でも同じ種類の問題が発生する可能性があります。  
  
 **テキスト**、 **ntext**、および**イメージ**のデータは、通常、1 つのプログラム変数に収まるには大きすぎて、通常は**SQLBindCol**ではなく**SQLGetData**で処理されます。 サーバー カーソルを使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブ クライアント ODBC ドライバは、行がフェッチされるときに非**text**連結テキスト **、ntext、** または**image**列のデータを送信しないように最適化されます。 **テキスト**、 **ntext**、または**イメージ**のデータは、アプリケーションが列に対して**SQLGetData**を発行するまで、実際にはサーバーから取得されません。  
  
 この最適化は、ユーザーがカーソルを上下にスクロールしている間、**テキスト****、ntext、** または**イメージ**のデータが表示されないように、アプリケーションに適用できます。 ユーザーが行を選択すると、アプリケーションは**SQLGetData**を呼び出して**テキスト** **、ntext**、または**イメージ**データを取得できます。 これにより、ユーザーが選択しない行の**テキスト****、ntext、** または**image**データの送信が保存され、大量のデータの送信を保存できます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;結果の処理](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
