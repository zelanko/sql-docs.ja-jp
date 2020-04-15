---
title: コア インターフェイス準拠 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- core-level interface conformance levels [ODBC]
ms.assetid: aaaa864a-6477-45ff-a50a-96d8db66a252
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 886ded1cd79b35488c0d47df3dbd8055dc6a8016
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302134"
---
# <a name="core-interface-conformance"></a>コア インターフェイスの適合性
すべての ODBC ドライバーは、少なくともコア レベル のインターフェイスの準拠を示す必要があります。 Core レベルの機能は、ほとんどの汎用相互運用可能なアプリケーションで必要な機能であるため、ドライバーは、このようなアプリケーションで動作できます。 コア レベルの機能は、ISO CLI 仕様で定義されている機能と、Open Group CLI 仕様で定義されているオプション以外の機能にも対応します。 コア レベル インターフェイスに準拠した ODBC ドライバーを使用すると、アプリケーションは次のすべてを実行できます。  
  
-   **すべての**種類のハンドルを割り当て、**解放します。**  
  
-   すべての形式の**関数を**使用します。  
  
-   **SQLBindCol**を呼び出して、結果セット列をバインドします。  
  
-   パラメータの配列を含む動的パラメータを入力方向のみで処理するには、 **SQLBindParameter**と**SQLNumParams**を呼び出します。 (出力方向のパラメータは、レベル 2[のインターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能 203 です。  
  
-   バインド オフセットを指定します。  
  
-   **SQLParamData**および**SQLPutData**の呼び出しを含む実行時データ ダイアログを使用します。  
  
-   カーソルとカーソル名を管理**するには、SQLCloseCursor** **、SQLGetCursorName**、および**SQLSetCursorName**を呼び出します。  
  
-   SQLCol 属性 **、SQLDescribeCol、SQLNumResultCols**、および**SQLNumResultCols****SQLRowCount**を呼び出すことによって、結果セットの説明 (メタデータ) にアクセスします。 **SQLColAttribute** (ブックマークメタデータを取得する列番号 0 にこれらの関数を使用する[機能は、レベル 2 のインターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能 204 です。  
  
-   カタログ関数 SQLColumns **、SQLGetTypeInfo** **、SQLStatistics**、および**SQLTables**を呼び出すことによって、データ ディクショナリをクエリします。 **SQLColumns**  
  
     ドライバは、データベーステーブルとビューのマルチパート名をサポートする必要はありません。 (詳細については、レベル 2[インターフェイス準拠の「レベル 1 インターフェイス準拠](../../../odbc/reference/develop-app/level-1-interface-conformance.md)」の機能 101 および機能[201 を参照](../../../odbc/reference/develop-app/level-2-interface-conformance.md)してください。ただし、列修飾やインデックス名など、SQL-92 仕様の特定の機能は、構文的にはマルチパートの名前付けに相当します。 ODBC 機能の現在のリストは、SQL-92 のこれらの側面に新しいオプションを導入することを意図していません。  
  
-   データ ソースと接続を管理するには **、SQLConnect** **、SQL データソース****、SQL 切断**、および**SQLDriverConnect**を呼び出します。 サポートする ODBC レベルに関係なく **、SQLDrivers**を呼び出して、ドライバーに関する情報を取得します。  
  
-   SQL ステートメントを準備し **、SQLExecDirect** **、SQL 実行**、および**SQLPrepare**を呼び出して実行します。  
  
-   **SQLFetch**を呼び出すか、または SQL_FETCH_NEXT に設定された*FetchOrientation*引数を指定して**SQLFetchScroll**を呼び出すことによって、順方向にのみ、結果セットまたは複数行の 1 行をフェッチします。  
  
-   **SQLGetData**を呼び出すことによって、パーツでバインドされていない列を取得します。  
  
-   すべての属性の現在の値を取得するには **、SQLGetConnectAttr** **、SQLGetEnvAttr**、および**SQLGetStmtAttr**を呼び出し、すべての属性を既定値に設定**し、特定**の属性を既定以外**SQLSetEnvAttr**の値に設定**します。**  
  
-   記述子の特定のフィールドを操作するには **、SQLCopyDesc**、SQLGetDescField、SQLGetDescRec、SQLSetDescフィールド、および**SQLGetDescRec** **SQLGetDescField** **SQLSetDescRec**を呼び出します。 **SQLSetDescField**  
  
-   診断情報を取得するには **、SQLGetDiagField**と**SQLGetDiagRec**を呼び出します。  
  
-   ドライバーの機能を検出するには **、SQLGet 関数**と**SQLGetInfo**を呼び出します。 また **、SQLNativeSql**を呼び出すことによって、データ ソースに送信される前に、SQL ステートメントに対して行われたテキスト置換の結果を検出します。  
  
-   トランザクションをコミットするには **、SQLEndTran**の構文を使用します。 コア レベル ドライバーは、真のトランザクションをサポートする必要はありません。したがって、アプリケーションは、SQL_ATTR_AUTOCOMMIT接続属性に対してSQL_ROLLBACKもSQL_AUTOCOMMIT_OFFも指定できません。 (詳細については、[レベル 2 インターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能 109 を参照してください。  
  
-   **SQLCancel**を呼び出して実行時のデータ ダイアログをキャンセルし、マルチスレッド環境では、別のスレッドで実行されている ODBC 関数をキャンセルします。 コア レベル インターフェイスの準拠は、関数の非同期実行のサポートや、非同期実行の ODBC 関数をキャンセルする**SQLCancel**の使用を義務付けません。 ドライバーが同時に独立したアクティビティを実行するために、プラットフォームと ODBC ドライバーのどちらもマルチスレッドである必要があります。 ただし、マルチスレッド環境では、ODBC ドライバーはスレッド セーフである必要があります。 アプリケーションからの要求のシリアル化は、パフォーマンスに重大な問題が発生する可能性がある場合でも、この仕様を実装するための準拠の方法です。  
  
-   SQLSpecialColumns を呼び出して、テーブルのSQL_BEST_ROWID行を識別**する列を取得します**。 (SQL_ROWVERのサポートは、レベル 2[のインターフェイス準拠](../../../odbc/reference/develop-app/level-2-interface-conformance.md)の機能 208 です。  
  
    > [!IMPORTANT]  
    >  ODBC ドライバーは、コア インターフェイスの準拠レベルで関数を実装する必要があります。
