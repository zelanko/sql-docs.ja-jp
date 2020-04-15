---
title: ODBC 3.x アプリケーションの作成 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ba48d76babcaa5fcc49a541088f7c4cc349b569
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288990"
---
# <a name="writing-odbc-3x-applications"></a>ODBC 3.x アプリケーションの作成
ODBC *2.x*アプリケーションを ODBC *3.x*にアップグレードする場合は、ODBC *2.x と 3.x*の両方のドライバで動作するように記述する必要があります。 *3.x* アプリケーションには、ODBC *3.x*の機能を最大限に活用する条件付きコードを組み込む必要があります。  
  
 SQL_ATTR_ODBC_VERSION環境属性は、SQL_OV_ODBC2に設定する必要があります。 これにより、ドライバーは、「[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)」で説明されている変更に対して ODBC *2.x*ドライバのように動作します。  
  
 アプリケーションで[「新機能](../../../odbc/reference/develop-app/new-features.md)」セクションで説明されている機能のいずれかを使用する場合は、ドライバーが ODBC *3.x*または ODBC *2.x*ドライバーであるかどうかを判断するために条件付きコードを使用する必要があります。 アプリケーションは、これらの条件付きコード フラグメントでエラー処理を行っている間に ODBC *3.x* SQLSTATE を取得するのに**は、SQLGetDiagField**と**SQLGetDiagRec**を使用します。 新機能に関する次の点を考慮する必要があります。  
  
-   行セットサイズの動作の変更によって影響を受けるアプリケーションは、配列サイズが 1 より大きい場合に**SQLFetch**を呼び出さないように注意する必要があります。 これらのアプリケーションは、ODBC *3.x*と ODBC *2.x*の両方のドライバーで動作する共通のコードを持つため、SQL_ATTR_ARRAY_STATUS_PTR ステートメント属性を設定する**SQLSetStmtAttr**および**SQLFetchScroll**への呼び出しに**SQLExtendedFetch**呼び出しを置き換える必要があります。 SQL_ATTR_ROW_ARRAY_SIZEを持つ**SQLSetStmtAttr**は ODBC *2.x*ドライバー用のSQL_ROWSET_SIZEを使用して**SQLSetStmtAttr**にマップされるため、アプリケーションは複数行フェッチ操作のSQL_ATTR_ROW_ARRAY_SIZEを設定するだけで済みます。  
  
-   アップグレード中のほとんどのアプリケーションは、実際には SQLSTATE コードの変更の影響を受けません。 影響を受けるアプリケーションでは、ほとんどの場合、ODBC *3.x*エラー コードを ODBC *2.x*コードに変換する「SQLSTATE マッピング」セクションのエラー変換テーブルを使用して、機械的な検索を実行し、置換できます。 ODBC *3.x*ドライバー・マネージャーは ODBC *2.x* SQLSTATE から ODBC *3.x* SQLSTATE へのマッピングを実行するため、これらのアプリケーション・ライターは ODBC *3.x* SQLSTATE を検査するだけで、条件コードに ODBC *2.x* SQLSTATE を含める心配はありません。  
  
-   アプリケーションが日付、時刻、およびタイムスタンプのデータ型を使用する場合、アプリケーションは、それ自体を ODBC *2.x*アプリケーションとして宣言し、コンディショニング コードを使用する代わりに既存のコードを使用できます。  
  
 アップグレードには、次の手順も含める必要があります。  
  
-   接続を割り当てる前に**SQLSetEnvAttr**を呼び出して、SQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC2に設定します。  
  
-   **SQLAllocEnv、SQLAllocConnect、** または**SQLAllocStmt**のすべての呼び出しを、SQL_HANDLE_ENV、SQL_HANDLE_DBC、またはSQL_HANDLE_STMTの適切な*HandleType*引数を持つ**SQLAllocHandle**の呼び出しに置き換えます。 **SQLAllocConnect**  
  
-   **SQLFreeEnv**または**SQLFreeConnect**のすべての呼び出しを、SQL_HANDLE_DBCまたはSQL_HANDLE_STMTの適切な*HandleType*引数を持つ**SQLFreeHandle**への呼び出しに置き換えます。  
  
-   すべての呼び出しを**SQL セットコネクト****Attr**への呼び出しに置き換えます。 値が文字列である属性を設定する場合は、*引数 StringLength*を適切に設定します。 *属性引数を*SQL_XXXXからSQL_ATTR_XXXXに変更します。  
  
-   すべての呼び出しを**SQLGetConnectAttr**への呼び出しに置き換えます。 **SQLGetConnectOption** 文字列またはバイナリ属性を取得する場合は *、BufferLength*を適切な値に設定し *、StringLength*引数を渡します。 *属性引数を*SQL_XXXXからSQL_ATTR_XXXXに変更します。  
  
-   すべての呼び出しを **、SQLSetStmtAttr**への呼び出しに置き換えます。 **SQLSetStmtOption** 値が文字列である属性を設定する場合は、*引数 StringLength*を適切に設定します。 *属性引数を*SQL_XXXXからSQL_ATTR_XXXXに変更します。  
  
-   すべての呼び出しを **、SQLGetStmtAttr**への呼び出しに置き換えます。 **SQLGetStmtOption** 文字列またはバイナリ属性を取得する場合は *、BufferLength*を適切な値に設定し *、StringLength*引数を渡します。 *属性引数を*SQL_XXXXからSQL_ATTR_XXXXに変更します。  
  
-   **SQLTransact**のすべての呼び出しを**SQLEndTran**への呼び出しに置き換えます。 **SQLTransact**呼び出しの右端の有効なハンドルが環境ハンドルである場合は、SQL_HANDLE_ENVの*HandleType*引数を適切な*Handle*引数を指定して**SQLEndTran**呼び出しで使用する必要があります。 **SQLTransact**呼び出しの中で最も右側の有効なハンドルが接続ハンドルである場合は、SQL_HANDLE_DBCの*HandleType*引数を**SQLEndTran**呼び出しで使用し、適切な*Handle*引数を指定します。  
  
-   **SQLCol 属性**のすべての呼び出しを**SQLCol 属性**の呼び出しに置き換えます。 *引数*がSQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、またはSQL_COLUMN_LENGTHの場合は、関数の名前以外は変更しないでください。 指定されていない場合は、[*フィールド識別子] を*SQL_COLUMN_XXXX から SQL_DESC_XXXX に変更します。 *FieldIdentifier*がSQL_DESC_CONCISE_TYPE、データ型が日付時刻データ型の場合は、対応する ODBC *3.x*データ型に変更します。  
  
-   ブロック・カーソル、スクロール可能カーソル、またはその両方を使用する場合、アプリケーションは以下を実行します。  
  
    -   行セットのサイズ、カーソルの種類、およびカーソルの同時実行を**SQLSetStmtAttr**を使用して設定します。  
  
    -   ステータス レコードの配列を指すSQL_ATTR_ROW_STATUS_PTR設定するために **、SQLSetStmtAttr**を呼び出します。  
  
    -   SQL_ATTR_ROWS_FETCHED_PTRを SQLINTEGER を指す設定を行うために **、SQLSetStmtAttr**を呼び出します。  
  
    -   必要なバインディングを実行し、SQL ステートメントを実行します。  
  
    -   ループ内で**SQLFetchScroll**を呼び出して、行をフェッチし、結果セット内を移動します。  
  
    -   ブックマークでフェッチする場合、アプリケーションは**SQLSetStmtAttr**を呼び出して、SQL_ATTR_FETCH_BOOKMARK_PTRをフェッチする行のブックマークを含む変数に設定し、SQL_FETCH_BOOKMARKの FetchOrientation 引数を指定して**SQLFetchScroll** *を*呼び出します。  
  
-   パラメーターの配列を使用する場合、アプリケーションは次の処理を行います。  
  
    -   SQL_ATTR_PARAMSET_SIZE属性をパラメーター配列のサイズに設定するために **、SQLSetStmtAttr**を呼び出します。  
  
    -   内部 UDWORD 変数を指すSQL_ATTR_ROWS_PROCESSED_PTR設定するために**SQLSetStmtAttr**を呼び出します。  
  
    -   必要に応じて、準備、バインド、および実行の操作を実行します。  
  
    -   何らかの理由で実行が停止した場合 (SQL_NEED_DATAなど)、SQL_ATTR_ROWS_PROCESSED_PTRが指す場所を調べることによって、パラメータの 「現在の」行を見つけることができます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [アプリケーションの旧バージョンとの互換性のためのマッピング置換関数](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [SQLCloseCursor の呼び出し](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [SQLGetDiagField の呼び出し](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [SQLSetPos の呼び出し](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [カーソル ライブラリの操作](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Cursor Attributes1 の情報の種類のマッピング](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
