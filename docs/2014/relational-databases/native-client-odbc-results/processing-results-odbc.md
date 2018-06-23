---
title: 処理 (Odbc) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e81c060d0bbbdd5dcf41c86443cbb48c8942d54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083180"
---
# <a name="processing-results-odbc"></a>結果の処理 (ODBC)
  アプリケーションで SQL ステートメントが実行されると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では結果として生成されるすべてのデータを 1 つ以上の結果セットとして返します。 結果セットとは、クエリの条件に一致する行と列の集まりです。 SELECT ステートメント、カタログ関数、および一部のストアド プロシージャでは、アプリケーションで使用できる結果セットが表形式で生成されます。 実行される SQL ステートメントがストアド プロシージャ、複数のコマンドを含むバッチ、またはキーワードを含む SELECT ステートメントの場合、処理対象の結果セットが複数生成されます。  
  
 ODBC カタログ関数では、データを取得することもできます。 たとえば、 [SQLColumns](../native-client-odbc-api/sqlcolumns.md)データ ソース内の列に関するデータを取得します。 これらの結果セットには、0 行以上の行を含めることができます。  
  
 GRANT や REVOKE など、結果セットが返されない SQL ステートメントもあります。 これらのステートメントの戻り値のコードから**SQLExecute**または**SQLExecDirect**は通常、だけが示されます、ステートメントが正常に完了しました。  
  
 INSERT ステートメント、UPDATE ステートメント、および DELETE ステートメントからは、変更によって処理された行数だけを含む結果セットが返されます。 この数には、アプリケーションがあるときに使用できる呼び出しが行われた[SQLRowCount](../native-client-odbc-api/sqlrowcount.md)です。 ODBC 3 です。*x*アプリケーションには、いずれかの呼び出しがある必要があります**SQLRowCount**結果を取得するには設定または[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)をキャンセルします。 使用して、各変更ステートメントからの結果セットを処理する必要があります、バッチまたはストアド プロシージャの複数の INSERT、UPDATE、または DELETE ステートメントを含む、アプリケーションの実行時に**SQLRowCount** を使用して取り消すまたは**SQLMoreResults**です。 バッチやストアド プロシージャに SET NOCOUNT ON ステートメントを含めることで、これらの数をキャンセルできます。  
  
 Transact-SQL には、NOCOUNT ステートメントが含まれています。 NOCOUNT オプションを設定すると、SQL Server が返されません、ステートメントによって影響を受ける行の数と**SQLRowCount** 0 を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのバージョンにドライバー固有の仕様が導入されています[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)オプションとして SQL_SOPT_SS_NOCOUNT_STATUS、NOCOUNT オプションがオンかオフかどうかを報告します。 いつでも**SQLRowCount**返します 0 の場合、アプリケーションで SQL_SOPT_SS_NOCOUNT_STATUS をテストする必要があります。 SQL_NC_ON が返されます、値は 0 から**SQLRowCount**のみ SQL Server では、行の数が返されないことを示します。 SQL_NC_OFF が返される場合は、NOCOUNT がオフであることと、値の 0 から**SQLRowCount**こと、ステートメントによって影響されなかったすべての行を示します。 アプリケーションの値を表示しないで**SQLRowCount** SQL_SOPT_SS_NOCOUNT_STATUS が SQL_NC_OFF のときです。 大きなバッチやストアド プロシージャには、複数の SET NOCOUNT ステートメントが含まれていることがあるので、プログラマは SQL_SOPT_SS_NOCOUNT_STATUS が一定であると想定することはできません。 たびに、オプションをテストする必要があります**SQLRowCount** 0 を返します。  
  
 他のいくつかの Transact-SQL ステートメントは、結果セットではなく、メッセージにデータを含めて返します。 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーがこれらのメッセージを受け取り、アプリケーションに情報メッセージが利用できることを通知できるようにする SQL_SUCCESS_WITH_INFO が返されます。 アプリケーションが呼び出すことができますし、 **SQLGetDiagRec**をこれらのメッセージを取得します。 このように機能する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを次に示します。  
  
-   DBCC  
  
-   SET SHOWPLAN (以前のバージョンの SQL Server で使用可能)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、重大度が 11 以上の RAISERROR の SQL_ERROR が返されます。 RAISERROR の重大度が 19 以上の場合は、接続も削除されます。  
  
 アプリケーションでは、SQL ステートメントから返される結果セットを処理するために次の処理を行います。  
  
-   結果セットの特性を判断します。  
  
-   プログラム変数に列をバインドします。  
  
-   1 つの値、値の行全体、または値の複数の行を取得します。  
  
-   さらに結果セットが存在するかどうかを確認するテストを行い、存在する場合は、新しい結果セットの特性を判断する処理まで戻って、それ以降をループ処理します。  
  
 データ ソースから行を取得し、取得した行をアプリケーションに返す処理をフェッチと呼びます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [結果セットの特性を決定する&#40;ODBC&#41;](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [ストレージの割り当て](assigning-storage.md)  
  
-   [結果データのフェッチ](fetching-result-data.md)  
  
-   [データ型のマッピング&#40;ODBC&#41;](mapping-data-types-odbc.md)  
  
-   [データ型の使用方法](data-type-usage.md)  
  
-   [文字データの自動変換](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [結果を処理方法に関するトピック&#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  