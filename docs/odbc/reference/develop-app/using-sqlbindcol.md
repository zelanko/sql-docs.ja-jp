---
title: SQL バインドを使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da49ad4db80b93d02534a0c4ecacdc2621c9cf8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294632"
---
# <a name="using-sqlbindcol"></a>SQLBindCol の使用
アプリケーションは **、SQLBindCol**を呼び出すことによって列をバインドします。 この関数は、一度に 1 つの列をバインドします。 このアプリケーションでは、次の項目を指定します。  
  
-   列番号。 列 0 はブックマーク列です。この列は、一部の結果セットには含まれません。 その他の列には、番号 1 から始まる番号が付けられます。 結果セット内の列よりも番号の大きい列をバインドするとエラーになります。このエラーは、結果セットが作成されるまで検出できないため **、SQLBindCol**ではなく**SQLFetch**によって返されます。  
  
-   列にバインドされた変数の C データ型、アドレス、およびバイト長。 列の SQL データ・タイプを変換できない C データ・タイプを指定すると、エラーになります。このエラーは、結果セットが作成されるまで検出されない可能性があるため **、SQLBindCol**ではなく**SQLFetch**によって返されます。 サポートされている変換の一覧については、「付録 D:[データ型」の「SQL から C データ型への](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)データの変換」を参照してください。 バイト長については、「データ バッファの[長さ](../../../odbc/reference/develop-app/data-buffer-length.md)」を参照してください。  
  
-   長さ/インジケーター バッファーのアドレス。 長さ/インジケーターバッファーはオプションです。 バイナリまたは文字データのバイト長を返すために使用されるか、データが NULL の場合はSQL_NULL_DATAを返します。 詳細については、「[長さ/インジケーター値の使用](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)」を参照してください。  
  
 **SQLBindCol**が呼び出されると、ドライバーは、ステートメントにこの情報を関連付けます。 データの各行がフェッチされると、バインドされたアプリケーション変数の各列のデータを配置するために情報が使用されます。  
  
 たとえば、次のコードは変数を SalesPerson 列と CustID 列にバインドします。 列のデータは *、SalesPerson*および*CustID*に返されます。 *SalesPerson*は文字バッファーであるため、アプリケーションは、データを切り捨てるかどうかをドライバーが判断できるように、バイトの長さ (11) を指定します。 返されるタイトルのバイト長、またはそれが NULL かどうかは *、SalesPersonLenOrInd*に返されます。  
  
 *CustID*は整数変数であり、固定長なので、バイト長を指定する必要はありません。ドライバは、サイズ**が (** SQLUINTEGER ) であると想定**しています**。 返された顧客 ID データのバイト長、または NULL かどうかが *、CustIDInd*に返されます。 アプリケーションは、バイト長が常に**sizeof (** SQLUINTEGER **)** であるため、給与が NULL であるかどうかだけに関係することに注意してください。  
  
```  
SQLCHAR       SalesPerson[11];  
SQLUINTEGER   CustID;  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLRETURN     rc;  
SQLHSTMT      hstmt;  
  
// Bind SalesPerson to the SalesPerson column and CustID to the   
// CustID column.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, SalesPerson, sizeof(SalesPerson),  
            &SalesPersonLenOrInd);  
SQLBindCol(hstmt, 2, SQL_C_ULONG, &CustID, 0, &CustIDInd);  
  
// Execute a statement to get the sales person/customer of all orders.  
SQLExecDirect(hstmt, "SELECT SalesPerson, CustID FROM Orders ORDER BY SalesPerson",  
               SQL_NTS);  
  
// Fetch and print the data. Print "NULL" if the data is NULL. Code to   
// check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (SalesPersonLenOrInd == SQL_NULL_DATA)   
            printf("NULL                     ");  
   else   
            printf("%10s   ", SalesPerson);  
   if (CustIDInd == SQL_NULL_DATA)   
         printf("NULL\n");  
   else   
            printf("%d\n", CustID);  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 次のコードは、ユーザーが入力した**SELECT**ステートメントを実行し、結果セット内の各データ行を出力します。 アプリケーションは**SELECT**ステートメントで作成された結果セットの形状を予測できないため、前の例のようにハードコーディングされた変数を結果セットにバインドできません。 代わりに、アプリケーションは、データを保持するバッファーと、その行の各列に対して長さ/インジケーター バッファーを割り当てます。 列ごとに、列のメモリの先頭へのオフセットを計算し、列のデータと長さ/インジケーター バッファーが配置境界から始まるようにこのオフセットを調整します。 次に、オフセットから始まるメモリを列にバインドします。 ドライバーの観点から見ると、このメモリのアドレスは、前の例でバインドされた変数のアドレスと区別できません。 配置の詳細については、「[配置](../../../odbc/reference/develop-app/alignment.md)」を参照してください。  
  
```  
// This application allocates a buffer at run time. For each column, this   
// buffer contains memory for the column's data and length/indicator.   
// For example:  
//      column 1         column 2      column 3      column 4  
// <------------><---------------><-----><------------>  
//      db1   li1   db2   li2   db3   li3   db4   li4  
//      |      |      |      |      |      |      |         |  
//      _____V_____V________V_______V___V___V______V_____V_  
// |__________|__|_____________|__|___|__|__________|__|  
//  
// dbn = data buffer for column n  
// lin = length/indicator buffer for column n  
  
// Define a macro to increase the size of a buffer so that it is a   
// multiple of the alignment size. Thus, if a buffer starts on an   
// alignment boundary, it will end just before the next alignment   
// boundary. In this example, an alignment size of 4 is used because   
// this is the size of the largest data type used in the application's   
// buffer--the size of an SDWORD and of the largest default C data type   
// are both 4. If a larger data type (such as _int64) was used, it would   
// be necessary to align for that size.  
#define ALIGNSIZE 4  
#define ALIGNBUF(Length) Length % ALIGNSIZE ? \  
                  Length + ALIGNSIZE - (Length % ALIGNSIZE) : Length  
  
SQLCHAR        SelectStmt[100];  
SQLSMALLINT    NumCols, *CTypeArray, i;  
SQLINTEGER *   ColLenArray, *OffsetArray, SQLType, *DataPtr;  
SQLRETURN      rc;   
SQLHSTMT       hstmt;  
  
// Get a SELECT statement from the user and execute it.  
GetSelectStmt(SelectStmt, 100);  
SQLExecDirect(hstmt, SelectStmt, SQL_NTS);  
  
// Determine the number of result set columns. Allocate arrays to hold   
// the C type, byte length, and buffer offset to the data.  
SQLNumResultCols(hstmt, &NumCols);  
CTypeArray = (SQLSMALLINT *) malloc(NumCols * sizeof(SQLSMALLINT));  
ColLenArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
OffsetArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
  
OffsetArray[0] = 0;  
for (i = 0; i < NumCols; i++) {  
   // Determine the column's SQL type. GetDefaultCType contains a switch   
   // statement that returns the default C type for each SQL type.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i) + 1, SQL_DESC_TYPE, NULL, 0, NULL, (SQLPOINTER) &SQLType);  
   CTypeArray[i] = GetDefaultCType(SQLType);  
  
   // Determine the column's byte length. Calculate the offset in the   
   // buffer to the data as the offset to the previous column, plus the   
   // byte length of the previous column, plus the byte length of the   
   // previous column's length/indicator buffer. Note that the byte   
   // length of the column and the length/indicator buffer are increased   
   // so that, assuming they start on an alignment boundary, they will  
   // end on the byte before the next alignment boundary. Although this   
   // might leave some holes in the buffer, it is a relatively   
   // inexpensive way to guarantee alignment.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i)+1, SQL_DESC_OCTET_LENGTH, NULL, 0, NULL, &ColLenArray[i]);  
   ColLenArray[i] = ALIGNBUF(ColLenArray[i]);  
   if (i)  
      OffsetArray[i] = OffsetArray[i-1]+ColLenArray[i-1]+ALIGNBUF(sizeof(SQLINTEGER));  
}  
  
// Allocate the data buffer. The size of the buffer is equal to the   
// offset to the data buffer for the final column, plus the byte length   
// of the data buffer and length/indicator buffer for the last column.  
void *DataPtr = malloc(OffsetArray[NumCols - 1] +  
               ColLenArray[NumCols - 1] + ALIGNBUF(sizeof(SQLINTEGER)));  
  
// For each column, bind the address in the buffer at the start of the   
// memory allocated for that column's data and the address at the start   
// of the memory allocated for that column's length/indicator buffer.  
for (i = 0; i < NumCols; i++)  
   SQLBindCol(hstmt,  
            ((SQLUSMALLINT) i) + 1,  
            CTypeArray[i],  
            (SQLPOINTER)((SQLCHAR *)DataPtr + OffsetArray[i]),  
            ColLenArray[i],  
            (SQLINTEGER *)((SQLCHAR *)DataPtr + OffsetArray[i] + ColLenArray[i]));  
  
// Retrieve and print each row. PrintData accepts a pointer to the data,   
// its C type, and its byte length/indicator. It contains a switch   
// statement that casts and prints the data according to its type. Code   
// to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   for (i = 0; i < NumCols; i++) {  
      PrintData((SQLCHAR *)DataPtr[OffsetArray[i]], CTypeArray[i],  
               (SQLINTEGER *)((SQLCHAR *)DataPtr[OffsetArray[i] + ColLenArray[i]]));  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
