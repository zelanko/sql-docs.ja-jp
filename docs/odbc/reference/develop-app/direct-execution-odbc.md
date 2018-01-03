---
title: "ODBC の実行を指示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 058dada1c14b901b32f721bc2d42f3cc24434f07
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="direct-execution-odbc"></a>ODBC の実行を指示します。
直接実行は、ステートメントを実行する最も簡単な方法です。 実行のため、ステートメントが送信されると、データ ソースはアクセス プランにコンパイルし、そのアクセス プランを実行します。  
  
 直接実行は、通常をビルドおよび実行時にステートメントを実行する汎用アプリケーションによって使用されます。 たとえば、次のコードでは、SQL ステートメントを構築しに 1 回だけ実行します。  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 直接実行は、1 回実行されるステートメントに最適です。 その主な欠点が実行されるたびに、SQL ステートメントが解析されたことです。 さらに、アプリケーションがステートメントによって作成された、(存在する場合) まで、ステートメントが実行した後に結果セットに関する情報を取得できません。これには、ステートメントが準備され、2 つの別々 の手順で実行された場合です。  
  
 ステートメントを実行するには、直接、アプリケーションを実行します、次のアクション。  
  
1.  すべてのパラメーターの値を設定します。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)、このセクションで後述します。  
  
2.  呼び出し**SQLExecDirect**し、SQL ステートメントを含む文字列を渡します。  
  
3.  ときに**SQLExecDirect**が呼び出されると、ドライバー。  
  
    -   ステートメントを解析することがなく、データ ソースの SQL 文法を使用する SQL ステートメントを変更します。これで説明されているエスケープ シーケンスを置き換えることが含まれています。 [odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)です。 アプリケーションが呼び出すことによって、SQL ステートメントの変更後のフォームを取得できます**SQLNativeSql**です。 SQL_ATTR_NOSCAN ステートメント属性が設定されている場合、エスケープ シーケンスは置き換えられません。  
  
    -   現在のパラメーター値を取得し、必要に応じてそれらを変換します。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)、このセクションで後述します。  
  
    -   実行のデータ ソースに変換されるパラメーター値とステートメントを送信します。  
  
    -   すべてのエラーを返します。 シーケンス処理または SQLSTATE 24000 など状態診断 (無効なカーソルの状態)、SQLSTATE 42000 (構文エラーまたはアクセス違反、) などの構文エラーとセマンティック エラー SQLSTATE 42S02 などが含まれます (ベース テーブルまたはビューが見つかりません)。
