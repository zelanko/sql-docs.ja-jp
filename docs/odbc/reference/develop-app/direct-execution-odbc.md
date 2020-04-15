---
title: 直接実行 ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc5d942ac0c2af54168248d8e416ca233b2c69e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305163"
---
# <a name="direct-execution-odbc"></a>直接実行 (ODBC)
直接実行は、ステートメントを実行する最も簡単な方法です。 ステートメントが実行のために送信されると、データ ソースはそれをアクセス プランにコンパイルし、そのアクセス プランを実行します。  
  
 直接実行は、通常、実行時にステートメントをビルドして実行する汎用アプリケーションで使用されます。 たとえば、次のコードは SQL ステートメントを作成し、1 回実行します。  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 直接実行は、1 回実行されるステートメントに最適です。 その主な欠点は、SQL ステートメントが実行されるたびに解析されることです。 さらに、アプリケーションは、ステートメントが実行されるまで、ステートメントによって作成された結果セットに関する情報を取得できません 。;これは、ステートメントが準備され、2 つの別々のステップで実行される場合に可能です。  
  
 ステートメントを直接実行するには、アプリケーションは次のアクションを実行します。  
  
1.  任意のパラメータの値を設定します。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
2.  **SQLExecDirect を**呼び出し、SQL ステートメントを含む文字列を渡します。  
  
3.  **SQLExecDirect**が呼び出されると、ドライバーは次のようになります。  
  
    -   ステートメントを解析せずにデータ ソースの SQL 文法を使用するように SQL ステートメントを変更します。これには、「ODBC のエスケープ シーケンス」で説明されている[エスケープ シーケンスの](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)置き換えも含まれます。 アプリケーションは **、SQLNativeSql**を呼び出すことによって、SQL ステートメントの変更された形式を取得できます。 SQL_ATTR_NOSCANステートメント属性が設定されている場合、エスケープ・シーケンスは置き換えされません。  
  
    -   現在のパラメーター値を取得し、必要に応じて変換します。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
    -   ステートメントを送信し、変換されたパラメーター値をデータ ソースに送信して実行します。  
  
    -   エラーを返します。 これには、SQLSTATE 24000 (カーソル状態が無効) などのシーケンス診断または状態診断、SQLSTATE 42000 などの構文エラー (構文エラーまたはアクセス違反)、および SQLSTATE 42S02 (基本表またはビューが見つからない) などのセマンティック・エラーが含まれます。
