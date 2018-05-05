---
title: パラメーター マーカーをバインド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29f7f37bb67a20d994e3e82e383332b2b35197bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="binding-parameter-markers"></a>パラメーター マーカーをバインド
アプリケーションが呼び出すことによってパラメーターをバインド**SQLBindParameter**です。 **SQLBindParameter**一度に 1 つのパラメーターをバインドします。 アプリケーションには、次を指定します。  
  
-   パラメーターの数。 パラメーターは、SQL ステートメントの 1 から開始で増加するパラメーターの順序で番号が付けられます。 上位層にあるパラメーターの数を指定する有効なステートメントを実行すると、SQL ステートメントのパラメーターの数よりパラメーター値は無視されます。  
  
-   パラメーターの型 (入力、入力/出力、または出力) します。 プロシージャ呼び出しのパラメーターを除くすべてのパラメーターは入力パラメーターが。 詳細については、次を参照してください。[プロシージャ パラメーター](../../../odbc/reference/develop-app/procedure-parameters.md)、このセクションで後述します。  
  
-   変数の C データ型、アドレス、およびバイト長は、パラメーターにバインドします。 ドライバーは、データを C データ型から SQL データ型に変換できる必要があります。 またはエラーが返されます。 サポートされる変換の一覧は、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)付録 d: データ型にします。  
  
-   SQL データ型、有効桁数、およびパラメーター自体の小数点以下桁数です。  
  
-   長さ/インジケーター バッファーのアドレス。 バイナリまたは文字データの長さをバイト、データが NULL の場合、または、データに送信されることを指定します**SQLPutData**です。 詳細については、次を参照してください。[長さ/インジケーターの値を使用する](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)です。  
  
 たとえば、次のコード バインド*販売員*と*CustID*販売員および CustID 列のパラメーターにします。 *販売員*可変長である、文字データを格納して、コードのバイト長の指定*販売員*(11) し、バインド*SalesPersonLenOrInd*に内のデータのバイトの長さを含む*販売員*です。 この情報は必要ありません*CustID*固定長の整数データが含まれています。  
  
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
  
 ときに**SQLBindParameter**が呼び出されると、ドライバー情報を保存、ステートメントの構造にします。 ステートメントを実行すると、情報を使用して、パラメーター データを取得し、データ ソースに送信します。  
  
> [!NOTE]  
>  ODBC 1.0 では、パラメーターがバインドされていると**SQLSetParam**です。 ドライバー マネージャーの間の呼び出しをマップする**SQLSetParam**と**SQLBindParameter**アプリケーションおよびドライバーによって使用される ODBC のバージョンに応じて、します。
