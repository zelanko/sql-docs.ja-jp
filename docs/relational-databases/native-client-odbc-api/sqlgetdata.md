---
title: データを取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5ebda3de96cbd9a4a1ceadd62093420cc372a169
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302159"
---
# <a name="sqlgetdata"></a>SQLGetData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLGetData**は、列の値をバインドせずに結果セット データを取得するために使用されます。 **SQLGetData**を同じ列で連続して呼び出して、**テキスト** **、ntext**、または**イメージ**のデータ型を持つ列から大量のデータを取得できます。  
  
 アプリケーションでは、変数をバインドして結果セット データをフェッチする必要はありません。 任意の列のデータは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**、SQLGetData**を使用してネイティブ クライアント ODBC ドライバーから取得できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは **、SQLGetData**を使用してランダムな列の順序でデータを取得するをサポートしていません。 **SQLGetData**で処理されるすべての非バインド列は、結果セット内のバインドされた列よりも高い列序数を持つ必要があります。 アプリケーションでは、バインドされていない列の値を、列序数の小さい列から大きい列へと処理する必要があります。 前に処理した列よりも列序数が小さい列からデータを取得しようとすると、エラーが発生します。 アプリケーションで、結果セット行を報告するためにサーバー カーソルを使用している場合は、現在の行を再フェッチしてから列の値をフェッチできます。 既定の読み取り専用の前方専用カーソルでステートメントを実行する場合は **、SQLGetData**をバックアップするステートメントを再実行する必要があります。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは **、SQLGetData**を使用して取得した**テキスト** **、ntext、** および**イメージ**データの長さを正確に報告します。 アプリケーションは *、StrLen_or_IndPtr*パラメーターの戻りを利用して、長いデータを迅速に取得できます。  
  
> [!NOTE]  
>  大きな値型の場合 *、StrLen_or_IndPtr*はデータの切り捨て時にSQL_NO_TOTALを返します。  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a>SQLGetData による機能強化された日付と時刻のサポート  
 日付/時刻型の結果列値は[、「SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)」で説明されているように変換されます。  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a>SQLGetData による大きな CLR UDT のサポート  
 **SQLGetData は**、大規模な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="example"></a>例  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59350)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
