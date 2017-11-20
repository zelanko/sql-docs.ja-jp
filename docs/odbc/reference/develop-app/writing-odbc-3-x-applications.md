---
title: "ODBC 3.x アプリケーションの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3941a679210a18b39ed201dd564b9613b48a2a58
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="writing-odbc-3x-applications"></a>ODBC 3.x アプリケーションの作成
ODBC 2 時にします。*x*アプリケーションが ODBC 3 にアップグレードします*。x*、両方の ODBC 2 と連携するようは記述されている必要があります*。x*および 3 *。x*ドライバー。 アプリケーションでは、ODBC 3 の活用するために条件付きのコードを組み込む必要があります。*x*機能します。  
  
 SQL_OV_ODBC2 にまた環境属性を設定する必要があります。 これにより、ドライバーは ODBC 2 のように動作するよう*.x*セクションで説明されている変更に関してドライバー[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)です。  
  
 かどうか、アプリケーションで使用のセクションで説明する機能のいずれかの[の新機能](../../../odbc/reference/develop-app/new-features.md)、ドライバーは ODBC 3 であるかどうかを決定する条件付きコードを使用する必要があります*。x*または ODBC 2*.x*ドライバー。 アプリケーションを使用して**SQLGetDiagField**と**SQLGetDiagRec** ODBC 3 を取得します*。x* SQLSTATEs これらの条件付きコード フラグメントの処理中にエラーの実行中にします。 新しい機能に関する次の点を考慮する必要があります。  
  
-   行セット サイズの動作の変更によって影響を受けるアプリケーションの呼び出しをしないように注意する必要があります**SQLFetch**配列のサイズが 1 より大きい場合。 これらのアプリケーションへの呼び出しを置き換える必要があります**SQLExtendedFetch**への呼び出しに**SQLSetStmtAttr** SQL_ATTR_ARRAY_STATUS_PTR ステートメント属性を設定して**SQLFetchScroll**両方 ODBC 3 で動作する一般的なコードを持つようにする、します。*x*および ODBC 2 *。x*ドライバー。 **SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE を型にマップされます**SQLSetStmtAttr** ODBC 2 SQL_ROWSET_SIZE と*。x*ドライバー、その複数行のフェッチ操作のため、アプリケーションは SQL_ATTR_ROW_ARRAY_SIZE を設定できますだけです。  
  
-   ほとんどのアプリケーションをアップグレードするには実際に受けません SQLSTATE コードの変更。 影響を受けるアプリケーションの機械的な検索を行うし、「SQLSTATE マッピング」セクションで、エラー変換テーブルを使用して、ODBC 3 を変換するほとんどの場合に交換できます。*x*エラー コードが ODBC 2*.x*コード。 ODBC 3 以降*.x*ドライバー マネージャーは ODBC 2 からマッピングを実行します*。x* odbc 3 SQLSTATEs *。x* SQLSTATEs、これらのアプリケーションの作成者に ODBC 3 のチェックだけが必要があります*。x* SQLSTATEs であり、ODBC 2 を追加する方法がありません*。x* SQLSTATEs の条件付きコードにします。  
  
-   アプリケーションが日付、時刻、および timestamp データ型の優れた使用する場合、アプリケーションは ODBC 2 自体を宣言できます。*x*調整コードを使用する代わりに、既存のコードをアプリケーションおよび使用します。  
  
 アップグレードには、次の手順を実行する必要があります。  
  
-   呼び出す**SQLSetEnvAttr** SQL_OV_ODBC2 にまた環境属性を設定する接続を割り当てる前にします。  
  
-   すべての呼び出しを置き換える**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt**への呼び出しに**SQLAllocHandle**と適切な*HandleType* SQL_HANDLE_ENV、sql_handle_dbc として、または SQL_HANDLE_STMT の引数。  
  
-   すべての呼び出しを置き換える**SQLFreeEnv**または**SQLFreeConnect**への呼び出しに**SQLFreeHandle**と適切な*HandleType*引数sql_handle_dbc としてまたは SQL_HANDLE_STMT です。  
  
-   すべての呼び出しを置き換える**SQLSetConnectOption**への呼び出しに**SQLSetConnectAttr**です。 属性を設定するには、値が文字列の場合、設定、 *StringLength*引数適切にします。 変更*属性*SQL_XXXX から SQL_ATTR_XXXX への引数。  
  
-   すべての呼び出しを置き換える**SQLGetConnectOption**への呼び出しに**SQLGetConnectAttr**です。 文字列またはバイナリ属性を取得する場合は、設定*BufferLength*に適切な値を渡します、 *StringLength*引数。 変更*属性*SQL_XXXX から SQL_ATTR_XXXX への引数。  
  
-   すべての呼び出しを置き換える**SQLSetStmtOption**への呼び出しに**SQLSetStmtAttr**です。 属性を設定するには、値が文字列の場合、設定、 *StringLength*引数適切にします。 変更*属性*SQL_XXXX から SQL_ATTR_XXXX への引数。  
  
-   すべての呼び出しを置き換える**SQLGetStmtOption**への呼び出しに**SQLGetStmtAttr**です。 文字列またはバイナリ属性を取得する場合は、設定*BufferLength*に適切な値を渡します、 *StringLength*引数。 変更*属性*SQL_XXXX から SQL_ATTR_XXXX への引数。  
  
-   すべての呼び出しを置き換える**SQLTransact**への呼び出しに**SQLEndTran**です。 場合の右端にある有効なハンドル、 **SQLTransact**呼び出しは、環境ハンドル、 *HandleType* SQL_HANDLE_ENV の引数を使用する必要があります、 **SQLEndTran**を呼び出す適切な*処理*引数。 場合の右端にある有効なハンドル、 **SQLTransact**呼び出しは、接続ハンドル、 *HandleType* sql_handle_dbc としての引数を使用する必要があります、 **SQLEndTran**を呼び出す適切な*処理*引数。  
  
-   すべての呼び出しを置き換える**SQLColAttributes**への呼び出しに**SQLColAttribute**です。 場合、 *FieldIdentifier*引数が SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、または SQL_COLUMN_LENGTH 関数の名前以外の何かを変更しないでください。 いない場合は、変更*FieldIdentifier* SQL_COLUMN_XXXX SQL_DESC_XXXX するからです。 場合*FieldIdentifier* SQL_DESC_CONCISE_TYPE は、データ型が datetime データ型を変更、対応する ODBC 3*.x*データ型。  
  
-   ブロック カーソル、スクロール可能なカーソル、またはその両方を使用する場合、アプリケーションは、次を行います。  
  
    -   行セットのサイズ、カーソルの種類、およびカーソルの同時実行制御を使用して設定**SQLSetStmtAttr**です。  
  
    -   呼び出し**SQLSetStmtAttr**状態レコードの配列を指す SQL_ATTR_ROW_STATUS_PTR を設定します。  
  
    -   呼び出し**SQLSetStmtAttr** SQLINTEGER を指す SQL_ATTR_ROWS_FETCHED_PTR を設定します。  
  
    -   必要なバインドを実行し、SQL ステートメントを実行します。  
  
    -   呼び出し**SQLFetchScroll**行をフェッチし、結果内を移動するループ内で設定します。  
  
    -   ブックマークでフェッチする場合、アプリケーションが呼び出す**SQLSetStmtAttr** SQL_ATTR_FETCH_BOOKMARK_PTR をフェッチする行と呼び出しのブックマークを格納する変数に設定する**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK の引数。  
  
-   パラメーターの配列を使用する場合、アプリケーションは、次を行います。  
  
    -   呼び出し**SQLSetStmtAttr** SQL_ATTR_PARAMSET_SIZE 属性パラメーターの配列のサイズを設定します。  
  
    -   呼び出し**SQLSetStmtAttr**内部 UDWORD 変数を指す SQL_ATTR_ROWS_PROCESSED_PTR を設定します。  
  
    -   実行を準備する、バインド、および適切な操作を実行します。  
  
    -   何らかの理由 (SQL_NEED_DATA) などの実行が停止しは SQL_ATTR_ROWS_PROCESSED_PTR によって示される場所を調べることによってパラメーターの「現在」の行を検索できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [アプリケーションの旧バージョンとの互換性のための置換関数のマップ](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [SQLCloseCursor を呼び出す](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [SQLGetDiagField を呼び出し](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [SQLSetPos を呼び出す](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [カーソル ライブラリ操作](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [カーソル Attributes1 情報の種類のマッピング](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)

