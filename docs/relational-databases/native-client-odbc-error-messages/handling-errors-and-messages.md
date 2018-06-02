---
title: エラーとメッセージの処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-error-messages
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 640e21cdf83375d603fca4d40d1f0fb6fd7e01ce
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708210"
---
# <a name="handling-errors-and-messages"></a>エラーとメッセージの処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションで ODBC 関数を呼び出すときは、ドライバーが関数を実行して診断情報を 2 とおりの方法で返します。つまり、リターン コードで ODBC 関数が成功したか失敗したかを示し、診断レコードで関数の詳細な情報を伝えます。 診断レコードは、ヘッダー レコードと状態レコードから構成されます。 関数が成功した場合でも、少なくとも 1 つの診断レコード、つまりヘッダー レコードが返されます。  
  
 診断情報を開発時に使用すると、ハードコードした SQL ステートメントに存在する、無効なハンドルや構文エラーなどのプログラミング エラーを把握できます。 実行時に使用すると、ユーザーが入力した SQL ステートメントのデータの切り捨て、規則違反、構文エラーなどの実行時エラーや警告を確認できます。 一般的に、プログラミング ロジックはリターン コードを基に組み立てます。  
  
 たとえば、アプリケーションが呼び出す後**SQLFetch**を結果セット内の行を取得するには、リターン コードを示すかどうか、結果セットの末尾に達しました (SQL_NO_DATA)、情報メッセージには、(SQL_SUCCESS_ が返された場合WITH_INFO)、またはエラー (SQL_ERROR) が発生しました。  
  
 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが SQL_SUCCESS 以外を返します、アプリケーションが呼び出すことができます**SQLGetDiagRec**取得情報メッセージまたはエラー メッセージにします。 使用して**SQLGetDiagRec** 1 つ以上のメッセージがある場合は、設定、メッセージを上下にスクロールします。  
  
 リターン コード SQL_INVALID_HANDLE は常にプログラミング エラーを示します。実行時にはこのコードが返されないようにしてください。 それ以外のリターン コードは実行時の情報を含んでいます。ただし、SQL_ERROR はプログラミング エラーを示す場合もあります。  
  
 元の[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ API、c、Db-library により、コールバックのエラー処理をインストールするアプリケーションとメッセージ処理関数の戻り値のエラーまたはメッセージです。 PRINT、RAISERROR、DBCC、SET など、一部の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、結果セットではなく DB-Library メッセージ ハンドラー関数に結果を返します。 しかし、ODBC API にはそのようなコールバック機能がありません。 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを検出から戻ってきたメッセージ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ODBC リターン コードを SQL_SUCCESS_WITH_INFO または SQL_ERROR に設定し、メッセージ、1 つ以上の診断レコードが返されます。 したがって、ODBC アプリケーションを入念にテスト リターン コードと呼び出し**SQLGetDiagRec**メッセージ データを取得します。  
  
 トレースのエラーについては、次を参照してください。[データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=125805)です。 エラーのトレースで追加された機能強化については[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を参照してください[へのアクセス ログの診断情報、拡張イベント](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [メッセージを生成するステートメントの処理](../../relational-databases/native-client-odbc-error-messages/processing-statements-that-generate-messages.md)  
  
-   [診断レコードと診断フィールド](../../relational-databases/native-client-odbc-error-messages/diagnostic-records-and-fields.md)  
  
-   [ネイティブ エラー番号](../../relational-databases/native-client-odbc-error-messages/native-error-numbers.md)  
  
-   [SQLSTATE &#40;ODBC エラー コード&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)  
  
-   [エラー メッセージ](../../relational-databases/native-client-odbc-error-messages/error-messages.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
