---
title: 準備実行 ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 147ca85b21296575ff55afbe66ab286cc4824fae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282312"
---
# <a name="prepared-execution-odbc"></a>準備実行 ODBC
実行を準備すると、ステートメントを複数回実行する効率的な方法です。 このステートメントは、最初にコンパイルされるか、*または準備されてアクセス*・プランに入れられます。 その後、アクセス・プランは、後で 1 回以上実行されます。 アクセス・プランの詳細については[、SQL ステートメントの処理を](../../../odbc/reference/processing-a-sql-statement.md)参照してください。  
  
 通常、準備実行は、同じパラメータ化された SQL ステートメントを繰り返し実行するために、垂直アプリケーションとカスタム アプリケーションで使用されます。 たとえば、次のコードは、さまざまな部分の価格を更新するステートメントを準備します。 その後、毎回異なるパラメータ値を使用してステートメントを複数回実行します。  
  
```  
SQLREAL       Price;  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0, PriceInd = 0;  
  
// Prepare a statement to update salaries in the Employees table.  
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);  
  
// Bind Price to the parameter for the Price column and PartID to  
// the parameter for the PartID column.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &PartID, 0, &PartIDInd);  
  
// Repeatedly execute the statement.  
while (GetPrice(&PartID, &Price)) {  
   SQLExecute(hstmt);  
}  
```  
  
 準備された実行は、ステートメントが複数回実行される場合よりも高速です。直接実行されるステートメントは、実行されるたびにコンパイルされます。 また、データ ソースがアクセス プラン識別子をサポートしている場合、ステートメントが実行されるたびに、SQL ステートメント全体ではなく、データ ソースにアクセス プラン識別子を送信できるため、実行準備を行っても、ネットワーク トラフィックを削減できます。  
  
 アプリケーションは、ステートメントの準備後および実行前に結果セットのメタデータを取得できます。 ただし、準備済みの実行されていないステートメントのメタデータを返すドライバーにはコストがかかり、可能であれば相互運用可能なアプリケーションでは避ける必要があります。 詳細については、「[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)」を参照してください。  
  
 準備実行は、1 回しか実行されないステートメントには使用しないでください。 このようなステートメントの場合は、ODBC 関数呼び出しを追加する必要があるため、直接実行よりも少し時間がかかります。  
  
> [!IMPORTANT]  
>  **SQLEndTran**を明示的に呼び出すか、自動コミット モードで動作することによって、トランザクションをコミットまたはロールバックすると、一部のデータ ソースは接続上のすべてのステートメントのアクセス プランを削除します。 詳細については[、SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明のSQL_CURSOR_COMMIT_BEHAVIORおよびSQL_CURSOR_ROLLBACK_BEHAVIOR オプションを参照してください。  
  
 ステートメントを準備して実行するには、次のアプリケーションを実行します。  
  
1.  **SQLPrepare を**呼び出し、SQL ステートメントを含む文字列を渡します。  
  
2.  任意のパラメータの値を設定します。 パラメータは、実際にはステートメントの準備の前または後に設定できます。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
3.  **SQLExecute**を呼び出し、データのフェッチなど、必要な追加の処理を実行します。  
  
4.  必要に応じて、手順 2 と 3 を繰り返します。  
  
5.  **SQLPrepare が**呼び出されると、ドライバーは次のようになります。  
  
    -   ステートメントを解析せずにデータ ソースの SQL 文法を使用するように SQL ステートメントを変更します。 これには、「ODBC のエスケープ シーケンス」で説明されている[エスケープ シーケンスの](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)置き換えも含まれます。 アプリケーションは **、SQLNativeSql**を呼び出すことによって、SQL ステートメントの変更された形式を取得できます。 SQL_ATTR_NOSCANステートメント属性が設定されている場合、エスケープ・シーケンスは置き換えされません。  
  
    -   準備のためにステートメントをデータ ソースに送信します。  
  
    -   後で実行するために返されたアクセス プラン識別子を格納します (準備が成功した場合) か、エラーを返します (準備が失敗した場合)。 エラーには、SQLSTATE 42000 (構文エラーまたはアクセス違反) などの構文エラーや、SQLSTATE 42S02 (基本表またはビューが見つからない) などのセマンティック・エラーが含まれます。  
  
        > [!NOTE]  
        >  一部のドライバーは、この時点ではエラーを返さないが、代わりに、ステートメントが実行されたとき、またはカタログ関数が呼び出されたときに、エラーを返します。 したがって、実際に失敗した場合 **、SQLPrepare**は成功したように見える可能性があります。  
  
6.  **SQLExecute が**呼び出されると、ドライバーは次のようになります。  
  
    -   現在のパラメーター値を取得し、必要に応じて変換します。 詳細については、このセクションの[後の「ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
    -   アクセス・プラン ID と変換されたパラメーター値をデータ・ソースに送信します。  
  
    -   エラーを返します。 これらは一般に、SQLSTATE 24000 (無効なカーソル状態) などの実行時エラーです。 ただし、一部のドライバーは、この時点で構文エラーと意味エラーを返します。  
  
 データ ソースがステートメントの準備をサポートしていない場合、ドライバーは可能な範囲でそれをエミュレートする必要があります。 たとえば、**ドライバーは、SQLPrepare**が呼び出されたときに何もしないし **、SQLExecute**が呼び出されたときにステートメントの直接実行を実行します。  
  
 データ ソースが実行せずに構文チェックをサポートしている場合、ドライバーは**SQLPrepare**が呼び出されたときにチェック用のステートメントを送信し **、SQLExecute**が呼び出されたときに実行のためにステートメントを送信します。  
  
 ドライバーは、ステートメントの準備をエミュレートできない場合は **、SQLPrepare**が呼び出されたときにステートメントを格納し **、SQLExecute**が呼び出されたときに実行のために実行するために、それを送信します。  
  
 エミュレートされたステートメントの準備は完全ではないため **、SQLExecute は**通常**SQLPrepare**によって返されるエラーを返すことができます。
