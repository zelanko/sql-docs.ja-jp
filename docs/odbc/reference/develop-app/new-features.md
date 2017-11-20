---
title: "新機能 |Microsoft ドキュメント"
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
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e2b48097b6c398772e14d2594a583d89e6825e0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="new-features"></a>新機能
ODBC 3 以下の新機能が導入されました。*x*です。 ODBC 3 です。*x* ODBC 2 作業アプリケーション*.x*ドライバーでは、この機能を使用できません。 ODBC 3 です。*x* ODBC 2 を使用する場合に、ドライバー マネージャーでこれらの機能がマップされていない*.x*ドライバー。  
  
-   記述子を受け取る関数を引数として処理: **SQLSetDescField**、 **SQLGetDescField**、 **SQLSetDescRec**、 **SQLGetDescRec**、および**SQLCopyDesc**です。  
  
-   関数は、 **SQLSetEnvAttr**と**SQLGetEnvAttr**です。  
  
-   使用**SQLAllocHandle**記述子ハンドルを割り当てられません。 (使用**SQLAllocHandle**環境、接続、およびステートメントのハンドルの割り当てが重複している、いない新しい機能です)。  
  
-   使用**SQLGetConnectAttr** SQL_ATTR_AUTO_IPD 接続属性を取得します。 (の使用**SQLSetConnectAttr**を設定して**SQLGetConnectAttr**得るには、その他の接続属性が重複している、いない新しい機能です)。  
  
-   使用**SQLSetStmtAttr**を設定して**SQLGetStmtAttr** 、次のステートメント属性を取得します。 (の使用**SQLSetStmtAttr**を設定して**SQLGetStmtAttr**得るには、その他のステートメント属性が重複している、いない新しい機能です)。  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_ENABLE_AUTO_IPD  
  
     SQL_ATTR_FETCH_BOOKMARK_PTR  
  
     SQL_ATTR_BIND_OFFSET  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     SQL_DESC_PARAM_STATUS_PTR  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR  
  
     SQL_ATTR_PARAMSET_SIZE  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_ROW_ARRAY_SIZE  
  
-   使用**SQLGetStmtAttr**を次のステートメント属性を取得します。 (使用**SQLGetStmtAttr**を他のステートメントを取得する属性が重複している機能のない新しい機能です)。  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Interval C データ型、interval SQL データ型、BIGINT C データ型 SQL_C_NUMERIC データ構造体の使用。  
  
-   パラメーターの行方向のバインド。  
  
-   呼び出しなど、オフセットに基づくブックマークをフェッチ**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK および 0 以外のオフセットを指定の引数。  
  
-   **SQLFetch**行の状態配列を使用した呼び出しを混在、複数の行をフェッチ、フェッチされた行の数を返す**SQLFetchScroll**とでの呼び出しを混在させないで**SQLBulkOperations**または**SQLSetPos**です。 詳細については、次のセクションを参照してください。[ブロック カーソル、スクロール可能なカーソル、および ODBC 3.x アプリケーションとの下位互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)です。  
  
-   名前付きパラメーターです。  
  
-   ODBC 3 のいずれか。*x*– 特定**SQLGetInfo**オプション。 (ODBC 3 場合。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーは、いくつかの ODBC 2 は置き換え SQL_XXX_CURSOR_ATTRIBUTES1 の情報の種類を呼び出します*。x*情報の種類は信頼性が高く、情報のいくつか必要がありますが、信頼性の高いものがあります。 詳細については、次を参照してください[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)。)。  
  
-   オフセットをバインドします。  
  
-   更新、更新、およびブックマークを削除 (を呼び出すことによって**SQLBulkOperations**)。  
  
-   呼び出す**SQLBulkOperations**または**SQLSetPos** S5 状態にします。  
  
-   診断レコードの ROW_NUMBER と目のフィールド (置換関数で取得する必要が**SQLGetDiagField**または**SQLGetDiagRec**)。  
  
-   おおよその行をカウントします。  
  
-   警告情報 (から SQL_ROW_SUCCESS_WITH_INFO **SQLFetchScroll**)。  
  
-   可変長ブックマーク。  
  
-   パラメーターの配列の拡張エラー情報。  
  
-   すべてのカタログ関数によって返される結果セットに新しい列です。  
  
-   使用**SQLDescribeCol**と**SQLColAttribute**列 0 にします。  
  
-   ODBC 3 を使用します。*x*– 特定の列属性への呼び出しで**SQLColAttribute**です。  
  
-   複数の環境ハンドルを使用します。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [ブロック カーソル、スクロール可能なカーソル、および ODBC 3.x アプリケーションの旧バージョンとの互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)

