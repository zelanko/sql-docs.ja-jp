---
title: エラーとメッセージの処理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4a4d87ccae235aee1a11e58aff60fe8e34d6205
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68207094"
---
# <a name="handling-errors-and-messages"></a>エラーとメッセージの処理
  アプリケーションで ODBC 関数を呼び出すときは、ドライバーが関数を実行して診断情報を 2 とおりの方法で返します。つまり、リターン コードで ODBC 関数が成功したか失敗したかを示し、診断レコードで関数の詳細な情報を伝えます。 診断レコードは、ヘッダー レコードと状態レコードから構成されます。 関数が成功した場合でも、少なくとも 1 つの診断レコード、つまりヘッダー レコードが返されます。  
  
 診断情報を開発時に使用すると、ハードコードした SQL ステートメントに存在する、無効なハンドルや構文エラーなどのプログラミング エラーを把握できます。 実行時に使用すると、ユーザーが入力した SQL ステートメントのデータの切り捨て、規則違反、構文エラーなどの実行時エラーや警告を確認できます。 一般的に、プログラミング ロジックはリターン コードを基に組み立てます。  
  
 たとえば、アプリケーションが**Sqlfetch**を呼び出して結果セットの行を取得すると、結果セットの末尾に到達したか (SQL_NO_DATA)、情報メッセージが返されたか (SQL_SUCCESS_WITH_INFO)、エラーが発生したか (SQL_ERROR) が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーが SQL_SUCCESS 以外のものを返した場合、アプリケーションは、情報メッセージまたはエラーメッセージを取得するために**SQLGetDiagRec**を呼び出すことができます。 複数のメッセージがある場合は、 **SQLGetDiagRec**を使用してメッセージセットを上下にスクロールします。  
  
 リターン コード SQL_INVALID_HANDLE は常にプログラミング エラーを示します。実行時にはこのコードが返されないようにしてください。 それ以外のリターン コードは実行時の情報を含んでいます。ただし、SQL_ERROR はプログラミング エラーを示す場合もあります。  
  
 元[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のネイティブ API である db-library (C) を使用すると、アプリケーションは、エラーまたはメッセージを返すコールバックエラー処理関数およびメッセージ処理関数をインストールできます。 PRINT、RAISERROR、DBCC、SET など、一部の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、結果セットではなく DB-Library メッセージ ハンドラー関数に結果を返します。 しかし、ODBC API にはそのようなコールバック機能がありません。 から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れたメッセージが Native Client odbc ドライバーによって検出されると、odbc リターンコードが SQL_SUCCESS_WITH_INFO または SQL_ERROR に設定され、そのメッセージが1つ以上の診断レコードとして返されます。 そのため、ODBC アプリケーションでは、これらのリターンコードを注意深くテストし、 **SQLGetDiagRec**を呼び出してメッセージデータを取得する必要があります。  
  
 エラーのトレースの詳細については、「[データ アクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)」を参照してください。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] に追加されたエラーのトレースの機能強化については、「[拡張イベント ログの診断情報へのアクセス](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [メッセージを生成するステートメントの処理](processing-statements-that-generate-messages.md)  
  
-   [診断レコードと診断フィールド](diagnostic-records-and-fields.md)  
  
-   [ネイティブ エラー番号](native-error-numbers.md)  
  
-   [SQLSTATE &#40;ODBC エラーコード&#41;](sqlstate-odbc-error-codes.md)  
  
-   [エラー メッセージ](error-messages.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
