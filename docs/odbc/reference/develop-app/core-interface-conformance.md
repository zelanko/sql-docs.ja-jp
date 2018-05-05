---
title: インターフェイスへの準拠をコア |Microsoft ドキュメント
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c45fdfe2b01ddfd34e7db391b799b95ce696da8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="core-interface-conformance"></a>コア インターフェイスへの準拠
すべての ODBC ドライバーは、少なくともコア レベルを示す必要がありますインターフェイスへの準拠です。 最も一般的な相互運用可能なアプリケーションで必要なものでは、コア レベルの機能、ために、ドライバーは、このようなアプリケーションで操作できます。 コア レベルの機能は、ISO CLI 仕様で定義されている機能と、開いているグループ CLI 仕様で定義されている nonoptional 機能にも対応しています。 コア レベル – インターフェイスに準拠する ODBC ドライバーは、以下のすべてを実行するようにアプリケーションを使用できます。  
  
-   呼び出して、すべての種類のハンドルを解放の割り当てと**SQLAllocHandle**と**SQLFreeHandle**です。  
  
-   すべてのフォームを使用して、 **SQLFreeStmt**関数。  
  
-   呼び出して結果セットの列をバインド**SQLBindCol**です。  
  
-   呼び出して、入力方向にのみ、パラメーターの配列を含む、動的パラメーターを取り扱えません。 **SQLBindParameter**と**SQLNumParams**です。 (出力方向のパラメーターは、機能で 203[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md))。  
  
-   バインドのオフセットを指定します。  
  
-   呼び出しに関連する実行時データのダイアログ ボックスを使用して**SQLParamData**と**SQLPutData**です。  
  
-   呼び出してカーソルやカーソル名を管理**SQLCloseCursor**、 **SQLGetCursorName**、および**SQLSetCursorName**です。  
  
-   呼び出して、結果セットの (メタデータ) の説明へのアクセスを取得**SQLColAttribute**、 **SQLDescribeCol**、 **SQLNumResultCols**、および**SQLRowCount**. (ブックマークのメタデータを取得する列番号を 0 にこれらの関数の使用がで 204 を機能[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md))。  
  
-   カタログ関数を呼び出すことによって、データ ディクショナリをクエリ**SQLColumns**、 **SQLGetTypeInfo**、 **SQLStatistics**、および**SQLTables**です。  
  
     ドライバーは、データベース テーブルとビューのマルチパート名をサポートする必要はありません。 (詳細については、機能 101 を参照してください[インターフェイスへの準拠レベル 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)で 201 の機能と[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)。)。ただし、列名の修飾およびインデックスの名前など、SQL 92 仕様の特定の機能はマルチパート名前付けするために構文的に比較します。 ODBC の機能の存在の一覧は、SQL 92 のような側面に新しいオプションを紹介するものではありません。  
  
-   呼び出してデータ ソースとの接続を管理**SQLConnect**、 **SQLDataSources**、 **SQLDisconnect**、および**SQLDriverConnect**です。 どの ODBC に関係なくレベル、サポートを呼び出してドライバーに関する情報を入手**SQLDrivers**です。  
  
-   準備し、呼び出すことによって、SQL ステートメントを実行**SQLExecDirect**、 **SQLExecute**、および**SQLPrepare**です。  
  
-   呼び出して結果セットの 1 つの行または前方にのみ、複数の行をフェッチ**SQLFetch**または呼び出すことによって**SQLFetchScroll**で、 *FetchOrientation*引数SQL_FETCH_NEXT に設定されます。  
  
-   呼び出すことによって、部分に非バインド列を取得**SQLGetData**です。  
  
-   呼び出して、他のすべての属性の現在の値を取得**SQLGetConnectAttr**、 **SQLGetEnvAttr**、および**SQLGetStmtAttr**、し、既定値にすべての属性を設定し、既定以外の値を呼び出すことによって特定の属性を設定**SQLSetConnectAttr**、 **SQLSetEnvAttr**、および**SQLSetStmtAttr**です。  
  
-   呼び出して、記述子の特定のフィールドを操作**SQLCopyDesc**、 **SQLGetDescField**、 **SQLGetDescRec**、 **SQLSetDescField**、および**SQLSetDescRec**です。  
  
-   呼び出して、診断情報を取得**SQLGetDiagField**と**SQLGetDiagRec**です。  
  
-   呼び出してドライバーの機能を検出**SQLGetFunctions**と**SQLGetInfo**です。 また、テキストの置換が呼び出すことによって、データ ソースに送信される前に、SQL ステートメントに加えられたすべての結果を検出**SQLNativeSql**です。  
  
-   構文を使用して**SQLEndTran**トランザクションをコミットします。 コア レベル ドライバー必要がある場合は true。 トランザクションをサポートしていませんそのため、アプリケーションを指定できません SQL_ROLLBACK も SQL_AUTOCOMMIT_OFF SQL_ATTR_AUTOCOMMIT 接続属性。 (詳細については、機能 109 を参照してください[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)。)。  
  
-   呼び出す**SQLCancel**実行時のデータ ダイアログをキャンセルして、マルチ スレッド環境で、ODBC 関数別のスレッドで実行をキャンセルします。 コア レベル インターフェイスへの準拠させる必要はありません、関数の非同期実行もの使用のサポート**SQLCancel**を非同期的に実行する ODBC 関数を取り消します。 プラットフォームでも、ODBC ドライバーに独立したアクティビティを同時に実行するために、ドライバーのマルチ スレッドを使用する必要があります。 ただし、マルチ スレッド環境では、ODBC ドライバーがスレッド セーフなをする必要があります。 アプリケーションからの要求のシリアル化は、場合でも、パフォーマンスに重大な問題を作成する可能性がありますが、この仕様を実装するに準拠する方法です。  
  
-   呼び出して、テーブルの SQL_BEST_ROWID - 行を識別する列を入手**SQLSpecialColumns**です。 (SQL_ROWVER のサポートが機能で 208[インターフェイスへの準拠レベル 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md))。  
  
    > [!IMPORTANT]  
    >  ODBC ドライバーでは、コア インターフェイスへの準拠レベルで関数を実装する必要があります。
