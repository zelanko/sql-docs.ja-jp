---
title: "長い形式のデータの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0ea30c211e3cfd66acf1588ef9ca2a45fd1037d1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getting-long-data"></a>長い形式のデータを取得します。
Dbms 定義*長いデータ*任意の文字または 255 文字などの特定のサイズ以上のバイナリ データとして。 このデータは、いくつかの文字が 1000 単位のパーツの説明など、1 つのバッファーに格納するのに十分な小さ可能性があります。 ただし、長いテキスト ドキュメントやビットマップなどのメモリに格納するには長すぎる場合があります。 ドライバーを使用してパーツにから取得されたこのようなデータは、1 つのバッファーに格納されることはできません、ので**SQLGetData**行の他のデータがフェッチされた後にします。  
  
> [!NOTE]  
>  アプリケーションは、任意の型を使用してデータの実際に取得できます**SQLGetData**、だけでなく長時間かかる場合は、データが、部分では、文字データやバイナリ データだけを取得できるか。 ただし、データがそれほど 1 つのバッファーに収まらない場合は通常を使用する理由**SQLGetData**です。 バッファーを列にバインドし、バッファー内のデータを返す、ドライバーを使用できます。 非常に簡単です。  
  
 アプリケーションの最初の呼び出しを長い形式のデータを列から取得する**SQLFetchScroll**または**SQLFetch**を行に移動し、バインドされた列のデータをフェッチします。 その後、アプリケーションを呼び出す**SQLGetData**です。 **SQLGetData**と同じ引数を持つ**SQLBindCol**: ステートメント ハンドル; 列番号、アプリケーション変数; の C データ型、アドレス、およびバイト長および長さ/インジケーター バッファーのアドレス。 どちらの関数は、基本的に同じタスクを実行するために同じ引数を持ちます。 それらの説明、ドライバーをアプリケーション変数とその変数に特定の列のデータを返すことを指定します。 主な違いを**SQLGetData**は行をフェッチ後に呼び出される (とも呼ば*遅延バインディング*この理由により) によって、バインドが指定されていると**SQLGetData**の呼び出しの間のみ存続します。  
  
 1 つの列に関する**SQLGetData**のように動作**SQLFetch**: 列のデータを取得、アプリケーション変数の型に変換し、その変数に返します。 長さ/インジケーター バッファー内のデータのバイトの長さも返します。 方法の詳細についての**SQLFetch**のデータを返しますを参照してください[行のデータのフェッチ](../../../odbc/reference/develop-app/fetching-a-row-of-data.md)です。  
  
 **SQLGetData**異なる**SQLFetch** 1 つの重要な点でします。 これが呼び出された場合も複数回連続して、同じ列の各呼び出しは、データの連続する部分を返します。 各呼び出しの最後の呼び出し以外を返します SQL_SUCCESS_WITH_INFO と SQLSTATE 01004 (文字列データの右側切り捨てられます)。最後の呼び出しは関係なく SQL_SUCCESS を返します。 これは、どのように**SQLGetData**部分で長い形式のデータを取得するために使用します。 戻るには、データがある場合に**SQLGetData** SQL_NO_DATA が返されます。 アプリケーションは、長い形式のデータをまとめるため、データの部分を連結することを意味する可能性があります。 各部分は null で終わるです。アプリケーションは、部分を連結する場合、null 終端文字を削除する必要があります。 ブックマークを他の長い形式のデータの場合と同様に可変長の部分のデータの取得を実行できます。 一般的に、ドライバーを使用できるデータの量を検出し、SQL_NO_TOTAL バイトの長さを返すことができませんが、前の呼び出しで返されるバイトの数によって、長さ/インジケーター バッファーの増減の各呼び出しで返される値。 例:  
  
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
  
 使用していくつかの制限がある**SQLGetData**です。 一般に、列にアクセスで**SQLGetData**:  
  
-   列番号の昇順 (方法により、結果セットの列がデータ ソースから読み取られます) の順序でアクセスする必要があります。 たとえばを呼び出すとエラーが**SQLGetData**列 5 の 4 列目に呼び出すこととします。  
  
-   バインドすることはできません。  
  
-   最後のバインドされた列よりも高い、列番号が必要です。 たとえば、最後のバインドされた列が 3 列の場合を呼び出すとエラー **SQLGetData** 2 列目にします。 このため、アプリケーションが、選択リストの最後に長い形式のデータ列を配置することを確認してください。  
  
-   場合に使用することはできません**SQLFetch**または**SQLFetchScroll**が 1 つ以上の行を取得する呼び出されました。 詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)です。  
  
 一部のドライバーでは、これらの制限は適用されません。 存在したり、呼び出すことによって制限は適用されませんを調べたり、相互運用可能なアプリケーションが想定するか、必要があります**SQLGetInfo** SQL_GETDATA_EXTENSIONS オプションを使用します。  
  
 アプリケーションに文字またはバイナリ データ列のすべてのデータが必要がない場合、ネットワーク トラフィックが減少 DBMS に基づいたドライバーの属性を設定して、SQL_ATTR_MAX_LENGTH ステートメント、ステートメントを実行する前にします。 これは、任意の文字またはバイナリ列に返されるデータのバイト数を制限します。 たとえば、列には、長いテキストのドキュメントが含まれているとします。 この列を含むテーブルを参照するアプリケーションは、各ドキュメントの最初のページのみを表示する必要があります。 このステートメント属性をシミュレートできるは、ドライバーで、ただし、これを行う必要はありません。 具体的には、アプリケーションは、文字またはバイナリ データの切り捨てを希望する場合にする必要がありますバインド小さなバッファー列に**SQLBindCol**し、データの切り捨て、ドライバーを使用できます。

