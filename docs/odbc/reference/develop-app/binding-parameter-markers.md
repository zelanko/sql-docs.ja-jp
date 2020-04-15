---
title: パラメータマーカーをバインドする |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be99bc884a8baa66f3d632ee4731985f0cc85732
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306393"
---
# <a name="binding-parameter-markers"></a>バインディング パラメーター マーカー
アプリケーションは **、SQLBindParameter**を呼び出すことによってパラメーターをバインドします。 **一度に**1 つのパラメーターをバインドします。 このアプリケーションでは、次の項目を指定します。  
  
-   パラメーター番号。 パラメーターは、SQL ステートメント内で、1 から始まる増加パラメーター順で番号付けされます。 SQL ステートメントのパラメーター数よりも大きいパラメーター番号を指定することは有効ですが、ステートメントの実行時にパラメーター値は無視されます。  
  
-   パラメータの種類 (入力、入出力、または出力)。 プロシージャ呼び出しのパラメーターを除き、すべてのパラメーターは入力パラメーターです。 詳細については、このセクションの後半の[「プロシージャ パラメータ](../../../odbc/reference/develop-app/procedure-parameters.md)」を参照してください。  
  
-   パラメーターにバインドされた変数の C データ型、アドレス、およびバイト長。 ドライバーは、C データ型から SQL データ型にデータを変換できる必要があります、エラーが返されます。 サポートされている変換の一覧については、「付録 D:[データ型」の「C から SQL データ型への](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)データの変換」を参照してください。  
  
-   パラメーター自体の SQL データ型、有効桁数、および位取り。  
  
-   長さ/インジケーター バッファーのアドレス。 バイナリ データまたは文字データのバイト長を提供する、データが NULL であることを指定する、**または SQLPutData**を使用してデータを送信することを指定します。 詳細については、「[長さ/インジケーター値の使用](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)」を参照してください。  
  
 たとえば、次のコードは *、営業担当者*と CustID を "営業担当者" 列と *"CustID"* 列のパラメーターにバインドします。 *SalesPerson には*可変長の文字データが含まれているため、このコードは*SalesPerson* (11) のバイト長を指定し *、SalesPerson*内のデータのバイト長を含むには*SalesPersonLenOrInd*をバインドします。 *CustID*には、固定長の整数データが含まれているため、この情報は必要ありません。  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 **SQLBindParameter**が呼び出されると、ドライバーは、ステートメントの構造体にこの情報を格納します。 ステートメントが実行されると、その情報を使用してパラメーター データを取得し、データ ソースに送信します。  
  
> [!NOTE]  
>  ODBC 1.0 では、パラメータは**SQLSetParam**でバインドされました。 ドライバー マネージャーは、アプリケーションとドライバーで使用される ODBC のバージョンに応じて **、SQLSetParam**と**SQLBindParameter**の間の呼び出しをマップします。
