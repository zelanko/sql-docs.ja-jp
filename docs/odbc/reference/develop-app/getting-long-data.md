---
title: 長いデータを取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da901c22eb26af063397b4af184179ebe5c75924
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298992"
---
# <a name="getting-long-data"></a>長い形式のデータの取得
DBMS は、*長いデータ*を、255 文字など、特定のサイズを超える任意の文字またはバイナリ データとして定義します。 このデータは、数千文字の部分記述など、単一のバッファーに格納できるほど小さい場合があります。 ただし、長いテキスト ドキュメントやビットマップなど、メモリに格納するには長すぎる場合があります。 このようなデータは 1 つのバッファーに格納できないため、行の他のデータがフェッチされた後 **、SQLGetData**を使用してドライバーから取得されます。  
  
> [!NOTE]  
>  アプリケーションは、長いデータだけでなく**SQLGetData**を使用して、実際には任意の種類のデータを取得できますが、文字データとバイナリ データのみを部分的に取得できます。 ただし、データが 1 つのバッファーに収まるほど小さい場合は、通常 **、SQLGetData**を使用する理由はありません。 列にバッファーをバインドし、ドライバーがバッファー内のデータを返す方がはるかに簡単です。  
  
 列から長いデータを取得するには、アプリケーションはまず**SQLFetchScroll**または**SQLFetch**を呼び出して行に移動し、バインドされた列のデータをフェッチします。 アプリケーションは、次に**SQLGetData**を呼び出します。 **SQLGetData は** **SQLBindCol**と同じ引数を持っています。列番号。アプリケーション変数の C データ型、アドレス、およびバイト長。長さ/インジケーターバッファのアドレス。 両方の関数は、基本的に同じタスクを実行するため、同じ引数を持っています: どちらも、ドライバーにアプリケーション変数を記述し、特定の列のデータをその変数に返す必要があることを指定します。 主な違いは、行がフェッチされた後に**SQLGetData**が呼び出され (この理由で*遅延バインディング*と呼ばれることもあります)、SQLGetData で指定されたバインディングが呼び出しの間だけ続く点です。 **SQLGetData**  
  
 1 つの列に関しては、 **SQLGetData**は**SQLFetch**のように動作します: 列のデータを取得し、それをアプリケーション変数の型に変換して、その変数に戻します。 また、長さ/インジケーター バッファー内のデータのバイト長も返します。 **SQLFetch**がデータを返す方法の詳細については、「[データ行のフェッチ](../../../odbc/reference/develop-app/fetching-a-row-of-data.md)」を参照してください。  
  
 **SQLGetData は**、1 つの重要な点で**SQLFetch と**は異なります。 同じ列に対して複数回連続して呼び出された場合、各呼び出しはデータの連続部分を返します。 最後の呼び出しを除く各呼び出しは、SQL_SUCCESS_WITH_INFOと SQLSTATE 01004 (ストリング・データ、右切り捨て) を戻します。最後の呼び出しはSQL_SUCCESSを返します。 このようにして **、SQLGetData**を使用して、パートで長いデータを取得します。 返されるデータがなくなった場合 **、SQLGetData は**SQL_NO_DATA返します。 アプリケーションは長いデータをまとめ、データの一部を連結する必要があります。 各部分は NULL で終わる;アプリケーションは、部品を連結する場合は、NULL 終了文字を削除する必要があります。 部分でデータを取得する場合は、可変長ブックマークや他の長いデータに対して行うことができます。 長さ/インジケーター バッファーで返される値は、前の呼び出しで返されたバイト数によって各呼び出しの値が減少しますが、ドライバーは、利用可能なデータの量を検出できず、バイト長のSQL_NO_TOTALを返すことができないのが一般的です。 次に例を示します。  
  
```  
// Declare a binary buffer to retrieve 5000 bytes of data at a time.  
SQLCHAR       BinaryPtr[5000];  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd, BinaryLenOrInd, NumBytes;  
SQLRETURN     rc;   
SQLHSTMT      hstmt;  
  
// Create a result set containing the ID and picture of each part.  
SQLExecDirect(hstmt, "SELECT PartID, Picture FROM Pictures", SQL_NTS);  
  
// Bind PartID to the PartID column.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &PartID, 0, &PartIDInd);  
  
// Retrieve and display each row of data.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // Display the part ID and initialize the picture.  
   DisplayID(PartID, PartIDInd);  
   InitPicture();  
  
   // Retrieve the picture data in parts. Send each part and the number   
   // of bytes in each part to a function that displays it. The number   
   // of bytes is always 5000 if there were more than 5000 bytes   
   // available to return (cbBinaryBuffer > 5000). Code to check if   
   // rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLGetData(hstmt, 2, SQL_C_BINARY, BinaryPtr, sizeof(BinaryPtr),  
                           &BinaryLenOrInd)) != SQL_NO_DATA) {  
      NumBytes = (BinaryLenOrInd > 5000) || (BinaryLenOrInd == SQL_NO_TOTAL) ?  
                  5000 : BinaryLenOrInd;  
      DisplayNextPictPart(BinaryPtr, NumBytes);  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 **SQLGetData**の使用にはいくつかの制限があります。 一般に **、SQLGetData**でアクセスされる列 :  
  
-   列番号を増やす順にアクセスする必要があります (結果セットの列がデータ ソースから読み取られる方法のため)。 たとえば、5 列目に対して**SQLGetData**を呼び出し、その後、4 桁目に対して呼び出すと、エラーになります。  
  
-   バインドできません。  
  
-   最後にバインドされた列よりも大きい列番号を指定してください。 たとえば、最後にバインドされた列が 3 列の場合、列 2 の**SQLGetData**を呼び出すとエラーになります。 このため、アプリケーションでは、選択リストの末尾に長いデータ列を配置する必要があります。  
  
-   複数の行を取得するために**SQLFetch**または**SQLFetchScroll**が呼び出された場合は使用できません。 詳細については、「ブロック[カーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)」を参照してください。  
  
 ドライバーによっては、これらの制限を適用しないものもあります。 相互運用可能なアプリケーションは、それらが存在すると仮定するか、SQL_GETDATA_EXTENSIONS オプションを指定して**SQLGetInfo**を呼び出して適用されない制限を決定する必要があります。  
  
 アプリケーションが文字またはバイナリ データ列のすべてのデータを必要としない場合は、ステートメントを実行する前に SQL_ATTR_MAX_LENGTH ステートメント属性を設定することにより、DBMS ベースのドライバーのネットワーク トラフィックを削減できます。 これにより、任意の文字またはバイナリ列に対して返されるデータのバイト数が制限されます。 たとえば、列に長いテキスト ドキュメントが含まれているとします。 この列を含むテーブルを参照するアプリケーションでは、各ドキュメントの最初のページのみを表示する必要があります。 このステートメント属性は、ドライバーでシミュレートできますが、これを行う理由はありません。 特に、アプリケーションが文字データまたはバイナリ データを切り捨てる場合は **、SQLBindCol**を使用して小さなバッファーを列にバインドし、ドライバーがデータを切り捨てできるようにする必要があります。
