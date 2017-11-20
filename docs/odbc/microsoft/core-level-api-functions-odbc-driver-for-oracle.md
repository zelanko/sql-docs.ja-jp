---
title: "コア レベルの API 関数 (ODBC Driver for Oracle) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- core level API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 8596eed7-bda6-4cac-ae1f-efde1aab785f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3bc36063659da3cf0cd6b2b837be0c4fce46c6f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="core-level-api-functions-odbc-driver-for-oracle"></a>コア レベルの API 関数 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 このレベルでの関数は、ODBC ドライバーでのインターフェイスへの準拠の最低レベルを構成します。  
  
|API 関数|注|  
|------------------|-----------|  
|**SQLAllocConnect**|接続ハンドルのメモリを割り当てます*hdbc*、によって識別される、環境内で*henv*です。 ドライバー マネージャーは、この呼び出しを処理し、ドライバーを呼び出します**SQLAllocConnect**関数のたびに**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**と呼びます。|  
|**SQLAllocEnv**|Oracle クライアント ソフトウェアの要件を指定するダイアログ ボックスを表示し、SQL_NULL_HANDLE を返します。 この関数が、環境ハンドルのメモリを割り当て、Oracle クライアント ソフトウェアがインストールされていない場合*henv*、し、アプリケーションで使用するための ODBC 呼び出しレベルのインターフェイスを初期化します。|  
|**SQLAllocStmt**|ステートメント ハンドルのメモリを割り当て、hdbc によって指定された接続に、ステートメント ハンドルを関連付けます。 ドライバー マネージャーは、ドライバーは、hstmt 構造用のメモリ割り当てにこの呼び出しを渡します。|  
|**SQLBindCol**|結果列の記憶域スペースを割り当てられ、結果の種類を指定します。|  
|**SQLCancel**|Hstmt、ステートメント ハンドルでの処理をキャンセルします。 場合によっては、Oracle では実行中のステートメントの取り消しを使用することはできません。 つまり、Oracle には、その時点、ステートメントからの結果はすべて取り消されます for Oracle ODBC ドライバーで、プロセスが完了するまで実行中のステートメントが続行されます。|  
|**SQLColAttributes**|結果セット内の列の記述子の情報を返します。 記述子の情報は、文字の文字列、32 ビットの記述子に依存する値、または整数値として返されます。|  
|**SQLConnect**|データ ソースに接続します。 Oracle オペレーティング システムの認証を使用するには指定として「/」、 *szUID*パラメーターと""として、 *szAuthStr*パラメーター。|  
|**SQLDescribeCol**|名前、型、有効桁数、小数点以下桁数、および指定された結果列の null 値許容属性を返します。 **注:****SQLDescribeCol** SQL_VARCHAR として計算列をレポートします。  |  
|**SQLDisconnect**|接続を閉じます。 共有環境の接続プールが有効になっているし、アプリケーションを呼び出すかどうか**SQLDisconnect**環境で、接続で接続が接続プールに返されますが使用可能でを使用して他のコンポーネント同じ共有環境です。|  
|**SQLError**|最後のエラーについてのエラー状態や状態の情報を返します。 このドライバーは、スタックまたはを返すことのできるエラーの一覧、 *hstmt*、 *hdbc*、および*henv*方法に応じて、引数への呼び出し**SQLError**が行われます。 エラー キューは、各ステートメントの後にフラッシュされます。 通常、Oracle のエラー メッセージを取得、それ以外の場合空です。|  
|**SQLExecDirect**|新しい、準備されていない SQL ステートメントを実行します。 ドライバーは、ステートメントにパラメーターが存在しない場合、変数の現在値、パラメーター マーカーを使用します。 テーブル、ビュー、またはフィールド名にスペースが含まれる場合を囲む名前背面に引用符記号。 たとえば、データベースには、という名前のテーブルが含まれています。 *My Table*とフィールドの*My Field*、識別子の各要素を囲む次のように。<br /><br /> 選択\`表\`です。 \`マイ Field1\`、です。\`表\`.\`マイ Field2\` FROM\`行をテーブル '|  
|**SQLExecute**|準備された SQL ステートメントを実行します (によって既に準備ステートメント**SQLPrepare**)。 ドライバーは、ステートメントにパラメーターが存在しない場合、変数の現在値、パラメーター マーカーを使用します。|  
|**SQLFetch**|以前の呼び出しで指定された場所に結果セットから 1 つの行を取得**SQLBindCol**です。 呼び出すのため、ドライバーを準備**SQLGetData**バインドされていない列にします。|  
|**SQLFreeConnect**|接続ハンドルを解放し、ハンドルの割り当てられたすべてのメモリを解放します。|  
|**SQLFreeEnv**|ODBC Driver for Oracle を閉じるし、ドライバーに関連付けられているすべてのメモリを解放します。|  
|**SQLFreeStmt**|特定 hstmt に関連付けられている処理を停止、hstmt に関連付けられた開いているカーソルを閉じ、保留中の結果を破棄および必要に応じて、ステートメント ハンドルに関連付けられているすべてのリソースを解放します。|  
|**SQLGetCursorName**|指定された hstmt に関連付けられているカーソルの名前を返します。|  
|**SQLNumResultCols**|カーソルの結果セット列の数を返します。|  
|**SQLPrepare**|最適化し、ステートメントを実行する方法を計画することで、SQL ステートメントを準備します。 実行するため、SQL ステートメントがコンパイルされた**SQLExecDirect**です。<br /><br /> テーブル、ビュー、またはフィールド名にスペースが含まれる場合を囲む名前背面に引用符記号。 たとえば、データベースには、という名前のテーブルが含まれています。 *My Table*とフィールドの*My Field*、次のように、識別子の各要素を囲みます。<br /><br /> 選択\`表\`.\`My Field\` FROM\`行をテーブル '<br /><br /> 正式なパラメーターとしての配列を含む結果セットを使用する方法の詳細については、次を参照してください。[ストアド プロシージャから配列パラメーターを返す](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md)です。|  
|**SQLRowCount**|Oracle では、結果セットの後、最後の行をフェッチするように返されるまで – 1 の行の数を決定する方法は提供されません。|  
|**SQLSetCursorName**|カーソル名をアクティブなステートメント ハンドルに関連付けます*hstmt*です。|  
|**SQLSetParam**|ODBC 2 の場合は、SQLBindParameter に置換されます。*x*です。|  
|**SQLTransact**|コミットまたはロールバック操作は、すべてのステートメント ハンドル (hstmts)、接続に関連付けられているすべてのアクティブな操作や環境ハンドルに関連付けられているすべての接続を要求*henv*です。 手動モードのときに、コミットが失敗した場合、トランザクションが消えないです。トランザクションをロールバックまたはコミット操作を再試行することができます。 コミット操作は、自動トランザクション モードのときに失敗すると、トランザクションは自動的にロールバックします。トランザクションは、非アクティブにすることはできません。|

