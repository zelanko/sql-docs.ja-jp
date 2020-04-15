---
title: 新機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b40803dac6c9f296043a8dcac50f9bc69036875a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302400"
---
# <a name="new-features"></a>新機能
次の新機能は、ODBC *3.x*で導入されました。 ODBC *2.x*ドライバを使用する ODBC *3.x*アプリケーションでは、この機能を使用できません。 ODBC *3.x*ドライバー マネージャーでは、ODBC *2.x*ドライバーを操作するときにこれらの機能をマップしません。  
  
-   記述子ハンドルを引数として受け取る関数: **SQLSetDescField**、SQLGetDescField、SQLSetDescRec、SQLGetDescRec 、および**SQLCopyDesc**。 **SQLGetDescField** **SQLSetDescRec** **SQLGetDescRec**  
  
-   関数**SQLSetEnvAttr**および**SQLGetEnvAttr**.  
  
-   記述子ハンドルを割り当てる**SQLAllocHandle**の使用。 **(SQLAllocHandle**を使用して環境、接続、およびステートメントのハンドルを割り当てる機能は、新機能ではなく重複しています)。  
  
-   SQL_ATTR_AUTO_IPD接続属性を取得するために**SQLGetConnectAttr**を使用します。 (設定に**SQLSetConnectAttr**を使用し、取得する**SQLGetConnectAttr**を使用すると、他の接続属性は新しい機能ではなく複製されます。  
  
-   次のステートメント属性を設定する**SQLSetStmtAttr**と取得する**SQLGetStmtAttr**の使用。 (設定に**SQLSetStmtAttr**を使用し、取得する**SQLGetStmtAttr**を使用すると、他のステートメント属性は、新しい機能ではなく、重複しています。  
  
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
  
-   次のステートメント属性を取得するために**SQLGetStmtAttr**を使用します。 **(SQLGetStmtAttr**を使用して他のステートメント属性を取得する場合は、新機能ではなく、機能が重複しています)。  
  
     SQL_ATTR_IMP_ROW_DESCSQL_ATTR_IMP_PARAM_DESC  
  
-   間隔 C データ・タイプ、インターバル SQL データ・タイプ、BIGINT C データ・タイプ、およびSQL_C_NUMERIC・データ構造の使用。  
  
-   パラメータの行方向のバインド。  
  
-   SQL_FETCH_BOOKMARKの*FetchOrientation*引数を指定して**SQLFetchScroll**を呼び出し、0 以外のオフセットを指定するなど、オフセットベースのブックマークフェッチ。  
  
-   行の状態の配列、フェッチされた行数、複数行のフェッチ、呼び出しの混合 、および呼び出しの組み合わせを**SQLBulkOperations**または**SQLSetPos**との混合を返す**SQLFetch。** **SQLFetchScroll** 詳細については、次のセクション「ブロック[カーソル、スクロール可能なカーソル、および ODBC 3.x アプリケーションの下位互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)」を参照してください。  
  
-   名前付きパラメーター。  
  
-   ODBC *3.x*固有の**SQLGetInfo**オプションのいずれか。 ODBC *2.x*ドライバを使用する ODBC *3.x*アプリケーションが、いくつかの ODBC *2.x*情報型を置き換えたSQL_XXX_CURSOR_ATTRIBUTES1情報型を呼び出す場合、情報の一部は信頼できる場合がありますが、信頼できないものもあります。 詳細については[、「SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)」を参照してください)。  
  
-   オフセットをバインドします。  
  
-   ブックマークによる更新、更新、および削除 **(SQLBulkOperations**への呼び出しを使用)。  
  
-   S5 状態で**SQL バルクオペレーション**または**SQLSetPos**を呼び出しています。  
  
-   診断レコードのROW_NUMBERフィールドとCOLUMN_NUMBERフィールド (置換関数**SQLGetDiagField または SQLGetDiagRec**によって取得する必要があります)。 **SQLGetDiagRec**  
  
-   おおよその行数。  
  
-   警告情報 **(SQL_ROW_SUCCESS_WITH_INFOから SQL フェッチスクロールを参照)。**  
  
-   可変長ブックマーク。  
  
-   パラメーターの配列の拡張エラー情報。  
  
-   カタログ関数によって返される結果セット内のすべての新しい列。  
  
-   列 0**に対して SQL DescribeCol**と**SQLCol 属性**を使用します。  
  
-   **SQLColAttribute**の呼び出しで ODBC *3.x*固有の列属性を使用します。  
  
-   複数の環境ハンドルの使用。  
  
 このセクションでは、次のトピックについて説明します。  
  
-   [ODBC 3.x アプリケーション用のブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
