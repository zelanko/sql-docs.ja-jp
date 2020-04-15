---
title: パラメータの配列をバインドする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameter arrays [ODBC]
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 037afe23-052d-4f3a-8aa7-45302b199ad0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73cfcde89e89edb87a4955cf0854c66a01d81e6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283422"
---
# <a name="binding-arrays-of-parameters"></a>パラメーターのバインディング配列
パラメーターの配列を使用するアプリケーションは、配列を SQL ステートメントのパラメーターにバインドします。 バインディング スタイルには、次の 2 つがあります。  
  
-   配列を各パラメーターにバインドします。 各データ構造 (配列) には、1 つのパラメーターのすべてのデータが含まれます。 これは、単一のパラメーターの値の列をバインドするため、*列方向*バインディングと呼ばれます。  
  
-   パラメータのセット全体のパラメータ データを保持し、これらの構造体の配列をバインドする構造体を定義します。 各データ構造には、単一の SQL ステートメントのデータが含まれています。 これは *、1 行のパラメーターを*バインドするため、行方向のバインドと呼ばれます。  
  
 アプリケーションは、単一の変数をパラメーターにバインドするときと同様に **、SQLBindParameter**を呼び出して配列をパラメーターにバインドします。 唯一の違いは、渡されるアドレスは配列アドレスであり、単一変数アドレスではないということです。 アプリケーションは、SQL_ATTR_PARAM_BIND_TYPEステートメント属性を設定して、列方向 (デフォルト) または行方向のバインディングを使用するかどうかを指定します。 列方向バインディングと行方向バインディングのどちらを使用するかは、アプリケーションの好みの問題です。 プロセッサがメモリにアクセスする方法によっては、行方向のバインドが高速になる場合があります。 ただし、非常に多くのパラメータ行を除いて、その差は無視できる可能性があります。  
  
## <a name="column-wise-binding"></a>列方向のバインド  
 列方向のバインドを使用する場合、アプリケーションは、データを提供する各パラメーターに 1 つまたは 2 つの配列をバインドします。 最初の配列はデータ値を保持し、2 番目の配列は長さ/インジケーター バッファーを保持します。 各配列には、パラメーターの値と同じ数の要素が含まれます。  
  
 列方向のバインドが既定です。 また、アプリケーションは、SQL_ATTR_PARAM_BIND_TYPE ステートメント属性を設定することで、行方向のバインドから列方向のバインドに変更することもできます。 次の図は、列方向のバインドのしくみを示しています。  
  
 ![列&#45;賢明なバインドのしくみを示します。](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 たとえば、次のコードでは、10 要素の配列を PartID、説明、および Price 列のパラメーターにバインドし、10 行を挿入するステートメントを実行します。 列方向のバインドを使用します。  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
                                                "VALUES (?, ?, ?)";  
SQLUINTEGER    PartIDArray[ARRAY_SIZE];  
SQLCHAR        DescArray[ARRAY_SIZE][DESC_LEN];  
SQLREAL        PriceArray[ARRAY_SIZE];  
SQLINTEGER     PartIDIndArray[ARRAY_SIZE], DescLenOrIndArray[ARRAY_SIZE],  
               PriceIndArray[ARRAY_SIZE];  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
memset(DescLenOrIndArray, 0, sizeof(DescLenOrIndArray));  
memset(PartIDIndArray, 0, sizeof(PartIDIndArray));  
memset(PriceIndArray, 0, sizeof(PriceIndArray));  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN, 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in column-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  PartIDArray, 0, PartIDIndArray);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  DescArray, DESC_LEN, DescLenOrIndArray);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  PriceArray, 0, PriceIndArray);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartIDArray[i], DescArray[i], &PriceArray[i]);  
   PartIDIndArray[i] = 0;  
   DescLenOrIndArray[i] = SQL_NTS;  
   PriceIndArray[i] = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
}  
```  
  
## <a name="row-wise-binding"></a>行方向のバインド  
 行方向のバインドを使用する場合、アプリケーションはパラメーターのセットごとに構造体を定義します。 構造体には、各パラメーターに対して 1 つまたは 2 つの要素が含まれます。 最初の要素はパラメータ値を保持し、2 番目の要素は長さ/インジケーター バッファを保持します。 アプリケーションは、これらの構造体の配列を割り当てます。  
  
 アプリケーションは、SQL_ATTR_PARAM_BIND_TYPE ステートメント属性を使用してドライバーに構造体のサイズを宣言します。 アプリケーションは、配列の最初の構造体のパラメーターのアドレスをバインドします。 したがって、ドライバは、特定の行および列のデータのアドレスを計算することができます。  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 ここで、行は 1 からパラメーター セットのサイズまで番号が付けられます。 オフセットが定義されている場合、オフセットは、SQL_ATTR_PARAM_BIND_OFFSET_PTRステートメント属性によって指される値です。 次の図は、行方向のバインドのしくみを示しています。 パラメーターは、任意の順序で構造に配置できますが、わかりやすくするために順番に表示されます。  
  
 ![行&#45;賢明なバインドのしくみを示します。](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 次のコードでは、値を PartID、説明、および価格の列に格納する要素を持つ構造体を作成します。 次に、これらの構造体の 10 要素の配列を割り当て、行方向のバインドを使用して PartID、説明、および価格の列のパラメーターにバインドします。 次に、10 行を挿入するステートメントを実行します。  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
typedef tagPartStruct {  
   SQLREAL       Price;  
   SQLUINTEGER   PartID;  
   SQLCHAR       Desc[DESC_LEN];  
   SQLINTEGER    PriceInd;  
   SQLINTEGER    PartIDInd;  
   SQLINTEGER    DescLenOrInd;  
} PartStruct;  
  
PartStruct PartArray[ARRAY_SIZE];  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  
                Price) "  
               "VALUES (?, ?, ?)";  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, sizeof(PartStruct), 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in row-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartArray[0].PartID, 0, &PartArray[0].PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  PartArray[0].Desc, DESC_LEN, &PartArray[0].DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &PartArray[0].Price, 0, &PartArray[0].PriceInd);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartArray[i].PartID, PartArray[i].Desc, &PartArray[i].Price);  
   PartArray[0].PartIDInd = 0;  
   PartArray[0].DescLenOrInd = SQL_NTS;  
   PartArray[0].PriceInd = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
```
