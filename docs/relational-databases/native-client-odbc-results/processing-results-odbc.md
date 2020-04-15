---
title: 結果の処理 (ODBC) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39dafbb865ef951356bb01c4fd8f646bf943346b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304593"
---
# <a name="processing-results-odbc"></a>結果の処理 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  アプリケーションで SQL ステートメントが実行されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では結果として生成されるすべてのデータを 1 つ以上の結果セットとして返します。 結果セットとは、クエリの条件に一致する行と列の集まりです。 SELECT ステートメント、カタログ関数、および一部のストアド プロシージャでは、アプリケーションで使用できる結果セットが表形式で生成されます。 実行される SQL ステートメントがストアド プロシージャ、複数のコマンドを含むバッチ、またはキーワードを含む SELECT ステートメントの場合、処理対象の結果セットが複数生成されます。  
  
 ODBC カタログ関数では、データを取得することもできます。 たとえば[、SQLColumns は](../../relational-databases/native-client-odbc-api/sqlcolumns.md)、データ ソース内の列に関するデータを取得します。 これらの結果セットには、0 行以上の行を含めることができます。  
  
 GRANT や REVOKE など、結果セットが返されない SQL ステートメントもあります。 これらのステートメントの場合、通常は**SQLExecute**または**SQLExecDirect**からの戻りコードが、ステートメントが成功した唯一の指示です。  
  
 INSERT ステートメント、UPDATE ステートメント、および DELETE ステートメントからは、変更によって処理された行数だけを含む結果セットが返されます。 このカウントは、アプリケーションが[SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md)を呼び出したときに使用できます。 ODBC 3.*x*アプリケーションは **、SQLRowCount**を呼び出して結果セットを取得するか、[または SQLMoreResults を](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)キャンセルする必要があります。 アプリケーションが複数の INSERT、UPDATE、または DELETE ステートメントを含むバッチまたはストアド プロシージャを実行する場合、各変更ステートメントの結果セットは**SQLRowCount**を使用して処理するか **、SQLMoreResults**を使用して取り消す必要があります。 バッチやストアド プロシージャに SET NOCOUNT ON ステートメントを含めることで、これらの数をキャンセルできます。  
  
 Transact-SQL には、NOCOUNT ステートメントが含まれています。 NOCOUNT オプションがオンの場合、ステートメントの影響を受ける行の数は返されず **、0 が**返されます。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーのバージョンでは、NOCOUNT オプションがオンかオフかを報告するドライバー固有の[SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)オプションSQL_SOPT_SS_NOCOUNT_STATUSが導入されています。 **SQLRowCount が**0 を返すときはいつでも、アプリケーションはSQL_SOPT_SS_NOCOUNT_STATUSテストする必要があります。 SQL_NC_ONが返された場合 **、SQLRowCount**の値 0 は、SQL Server が行数を返していないことを示すだけです。 SQL_NC_OFFが返された場合は、NOCOUNT がオフであり **、SQLRowCount**の値 0 は、ステートメントがどの行にも影響を与えなかったことを示します。 アプリケーションでは、SQL_SOPT_SS_NOCOUNT_STATUSがSQL_NC_OFFされている場合 **、SQLRowCount**の値を表示しないでください。 大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、プログラマは SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。 このオプションは **、SQLRowCount**が 0 を返すたびにテストする必要があります。  
  
 他のいくつかの Transact-SQL ステートメントは、結果セットではなく、メッセージにデータを含めて返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、これらのメッセージを受信すると、アプリケーションに情報メッセージが利用可能であることを知らせるためにSQL_SUCCESS_WITH_INFOを返します。 アプリケーションは、これらのメッセージを取得する**SQLGetDiagRec**を呼び出すことができます。 このように機能する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを次に示します。  
  
-   DBCC  
  
-   SET SHOWPLAN (以前のバージョンの SQL Server で使用可能)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは、重大度 11 以上の RAISERROR に対してSQL_ERRORを返します。 RAISERROR の重大度が 19 以上の場合は、接続も削除されます。  
  
 アプリケーションでは、SQL ステートメントから返される結果セットを処理するために次の処理を行います。  
  
-   結果セットの特性を判断します。  
  
-   プログラム変数に列をバインドします。  
  
-   1 つの値、値の行全体、または値の複数の行を取得します。  
  
-   さらに結果セットが存在するかどうかを確認するテストを行い、存在する場合は、新しい結果セットの特性を判断する処理まで戻って、それ以降をループ処理します。  
  
 データ ソースから行を取得し、取得した行をアプリケーションに返す処理をフェッチと呼びます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ODBC&#41;の結果セットの特性&#40;決定する](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [ストレージの割り当て](../../relational-databases/native-client-odbc-results/assigning-storage.md)  
  
-   [結果データのフェッチ](../../relational-databases/native-client-odbc-results/fetching-result-data.md)  
  
-   [ODBC&#41;&#40;データ型のマッピング](../../relational-databases/native-client-odbc-results/mapping-data-types-odbc.md)  
  
-   [データ型の使用方法](../../relational-databases/native-client-odbc-results/data-type-usage.md)  
  
-   [文字データの自動変換](../../relational-databases/native-client-odbc-results/autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;SQL Server ネイティブ クライアント](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [ODBC&#41;&#40;結果の処理方法](https://msdn.microsoft.com/library/772d9064-c91d-4cac-8b60-fcc16bf76e10)  
  
  
