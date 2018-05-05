---
title: 準備実行 ODBC |Microsoft ドキュメント
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
- prepared execution [ODBC]
- SQL statements [ODBC], prepared execution
- SQL statements [ODBC], executing
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e03123e34834033b4c53fb1eb5818f6c78def82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="prepared-execution-odbc"></a>準備実行 ODBC
準備実行は、ステートメントを複数回実行する効率的な方法です。 ステートメントが最初にコンパイルされたまたは*準備ができている、*アクセス プランにします。 アクセスの計画は、1 つを実行し、他にも、後でします。 アクセスのプランの詳細については、次を参照してください。 [SQL ステートメントの処理](../../../odbc/reference/processing-a-sql-statement.md)です。  
  
 準備実行は、同じ、パラメーター化された SQL ステートメントを繰り返し実行する垂直方向およびカスタム アプリケーションで通常使用されます。 たとえば、次のコードは、さまざまな部分の価格を更新するステートメントを準備します。 たびに異なるパラメーター値で複数回ステートメントを実行します。  
  
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
  
 ステートメントは 1 回だけコンパイルされるため、主に、準備実行が複数回実行されるステートメントを直接実行よりも高速化直接実行されるステートメントには、実行されるたびにはコンパイルされます。 準備実行もできるネットワーク トラフィックの削減されるため、ドライバーに送信するアクセス プラン識別子、データ ソースごとに、ステートメントが実行、SQL ステートメント全体ではなく場合識別子は、データ ソースのアクセスをサポートします。  
  
 アプリケーションでは、結果セットをステートメントが準備された後が実行される前のメタデータを取得できます。 ただし、準備のメタデータを返して、実行されていないステートメントがいくつかのドライバーのコストと相互運用可能なアプリケーションで可能な限り避ける必要があります。 詳細については、次を参照してください。[結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)です。  
  
 準備実行は、1 回しか実行されないステートメントには使用しないでください。 このようなステートメントが直接実行よりもわずかに遅くなります、その他の ODBC 関数呼び出しを必要となるためです。  
  
> [!IMPORTANT]  
>  コミットまたはロールバック、トランザクションは、明示的に呼び出すか**SQLEndTran**または自動コミット モードで作業して一部のデータ ソース接続ですべてのステートメントのアクセスの計画を削除すると発生します。 詳細については、SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR のオプションを参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。  
  
 準備し、アプリケーションでステートメントを実行します。  
  
1.  呼び出し**SQLPrepare**し、SQL ステートメントを含む文字列を渡します。  
  
2.  すべてのパラメーターの値を設定します。 パラメーターは、前に、または、ステートメントを準備した後に実際に設定できます。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)、このセクションで後述します。  
  
3.  呼び出し**SQLExecute**データのフェッチなど、必要な追加の処理を行うとします。  
  
4.  必要に応じて、手順 2. および 3. を繰り返します。  
  
5.  ときに**SQLPrepare**が呼び出されると、ドライバー。  
  
    -   ステートメントを解析することがなく、データ ソースの SQL 文法を使用する SQL ステートメントを変更します。 これで説明されているエスケープ シーケンスを置き換えることが含まれています。 [odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)です。 アプリケーションが呼び出すことによって、SQL ステートメントの変更後のフォームを取得できます**SQLNativeSql**です。 SQL_ATTR_NOSCAN ステートメント属性が設定されている場合、エスケープ シーケンスは置き換えられません。  
  
    -   ステートメントを準備のため、データ ソースに送信します。  
  
    -   返されたアクセス プランの識別子を格納後の実行 (準備に成功した) 場合や、(準備が失敗した) 場合は、すべてのエラーを返します。 エラーには、構文エラーなど SQLSTATE 42000 (構文エラーまたはアクセス違反) エラーとセマンティック エラー SQLSTATE 42S02 などが含まれます (ベース テーブルまたはビューが見つかりません)。  
  
        > [!NOTE]  
        >  一部のドライバーはこの時点でエラーが返される操作を行いますが、代わりに、ステートメントが実行されるとき、またはカタログ関数が呼び出されたときに返します。 したがって、 **SQLPrepare**実際に失敗した場合に成功したことがあります。  
  
6.  ときに**SQLExecute**が呼び出されると、ドライバー。  
  
    -   現在のパラメーター値を取得し、必要に応じてそれらを変換します。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)、このセクションで後述します。  
  
    -   データ ソースに変換されるパラメーター値とアクセス プランの識別子を送信します。  
  
    -   すべてのエラーを返します。 これらは、SQLSTATE 24000 など一般的に、ランタイム エラー (無効なカーソルの状態) です。 ただし、一部のドライバーは構文および意味のエラーをこの時点で返します。  
  
 データ ソースがステートメントの準備をサポートしていない場合、ドライバー必要がありますエミュレート、可能な限りです。 など、ドライバーが何もしないときに**SQLPrepare**が呼び出され、ステートメントの直接実行を実行時に**SQLExecute**と呼びます。  
  
 ドライバーが確認するときのステートメントを送信可能性があります、データ ソースは、構文チェックが実行をサポートする場合**SQLPrepare**が呼び出され、ステートメントの実行を送信するときに**SQLExecute**はと呼ばれる。  
  
 ドライバーは、ステートメントの準備をエミュレートできない場合は、ステートメントが格納時に**SQLPrepare**が呼び出され、実行のために送信時に**SQLExecute**と呼びます。  
  
 エミュレートされたステートメントの準備が完全ではないため**SQLExecute**によって通常返されたエラーを返すことができます**SQLPrepare**です。
