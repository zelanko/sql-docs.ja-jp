---
title: "SQLBindCol を使用して |Microsoft ドキュメント"
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 300ac3348efa4d66076879917091200ac73a8a62
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-sqlbindcol"></a>SQLBindCol の使用
アプリケーションが呼び出すことによって列をバインド**SQLBindCol**です。 この関数は、一度に 1 つの列をバインドします。 アプリケーションには、次を指定します。  
  
-   列番号。 0 の列がブックマーク列です。この列は、いくつかの結果セットには含まれません。 その他のすべての列は、1 から始まる番号が付けられます。 エラーが、結果セット内の列よりも大きい番号の列をバインドするにはこのエラー検出できません、結果セットが作成されるまでによって返されるように**SQLFetch**ではなく、 **SQLBindCol**です。  
  
-   変数の C データ型、アドレス、およびバイト長は、列にバインドします。 エラーを列の SQL データ型を変換できません; C データ型を指定するにはこのエラー検出されない結果セットが作成されるまでによって返されるように**SQLFetch**ではなく、 **SQLBindCol**です。 サポートされる変換の一覧は、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)付録 d: データ型にします。 バイトの長さの詳細については、次を参照してください。[データ バッファーの長さ](../../../odbc/reference/develop-app/data-buffer-length.md)です。  
  
-   長さ/インジケーター バッファーのアドレス。 長さ/インジケーター バッファーはオプションです。 データが NULL の場合、バイナリまたは文字データや戻り値の SQL_NULL_DATA のバイトの長さを返すために使用されます。 詳細については、次を参照してください。[長さ/インジケーターの値を使用する](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)です。  
  
 ときに**SQLBindCol**が呼び出されると、ドライバー情報を関連付けますこのステートメントを使用します。 各データ行がフェッチしたときに情報を使用して、各列のデータ バインドされたアプリケーション変数内に配置します。  
  
 たとえば、次のコードは、販売員および CustID 列に変数をバインドします。 列のデータが返されます*販売員*と*CustID*です。 *販売員*を文字バッファーには、ドライバーは、データを切り捨てるかどうかを判断できるように、アプリケーションがそのバイトの長さ (11) を指定します。 返されたのバイト長のタイトルまたは NULL であるかどうかに返されます*SalesPersonLenOrInd*です。  
  
 *CustID*整数型の変数し、が固定長のバイト長を指定する必要はありません。 ドライバーは、ことが前提としています。 **sizeof (**SQLUINTEGER**)**です。 返された顧客のバイト長のデータを ID または NULL であるかどうかに返されます*CustIDInd*です。 バイトの長さは、常にあるため、アプリケーションが、給与が NULL であるかのみを求めていることに注意してください**sizeof (**SQLUINTEGER**)**です。  
  
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
  
 次のコードが実行される、**選択**ステートメントは、ユーザーが入力し、結果セット内のデータの各行を出力します。 アプリケーションは、結果の形状を予測できないため、設定によって作成された、**選択**ステートメントでは、結果セットを前の例のようににハード コーディングされた変数もバインドできません。 代わりに、アプリケーション データを保持するバッファーおよび長さ/インジケーター バッファーを割り当てますその行の各列。 各列の列のメモリの開始のオフセットを計算列のデータと長さ/インジケーター バッファーはアラインメントの境界で開始するために、このオフセットを調整します。 メモリの列にオフセットを開始し、バインドします。 ドライバーの観点から、このメモリのアドレスでは、前の例でバインドされている変数のアドレスを区別します。 配置の詳細については、次を参照してください。[配置](../../../odbc/reference/develop-app/alignment.md)です。  
  
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

