---
title: ODBC カーソル ライブラリのエラー コード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c263ce53c41546e63dc2a830d3db3b903e2e3515
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301433"
---
# <a name="odbc-cursor-library-error-codes"></a>ODBC カーソル ライブラリのエラー コード
> [!IMPORTANT]  
>  この機能は、将来のバージョンの Microsoft データ アクセス コンポーネントで削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 代わりに、ドライバーカーソルとサーバー カーソルを使用します。  
  
 ODBC カーソル ライブラリは[、ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)に示されている SQLSTATE に加えて、次の SQLSTATE を返します。  
  
> [!NOTE]  
>  カーソル ライブラリは、ステータス レコードを順序付けしません。ドライバ マネージャと ODBC 3 を使用します。*x*ドライバは、ステータス レコードの順序付けを行います。  
  
|SQLSTATE|説明|から返すことができます|  
|--------------|-----------------|--------------------------|  
|01000|カーソルは更新できません。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|カーソル ライブラリは使用されていません。 読み込みに失敗しました。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|カーソル ライブラリは使用されていません。 ドライバのサポートが不十分です。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|カーソル ライブラリは使用されていません。 ドライバ マネージャとのバージョンの不一致。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|ドライバーはSQL_SUCCESS_WITH_INFOを返しました。 警告メッセージは失われました。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|一般エラー: ファイル バッファを作成できません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般エラー: ファイル バッファから読み取れません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般エラー: ファイル バッファに書き込むことができません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般エラー: ファイル バッファを閉じまたは削除できません。|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|検索可能な列がバインドされていないため、位置指定要求を実行できません。|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|結合条件によって結果セットが作成されたため、位置指定要求を実行できませんでした。|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|バインドされたバッファーが最大セグメント サイズを超えています。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|結果セットは**SELECT**ステートメントによって生成されませんでした。|**SQLGetData**|  
|SL005|**SELECT**ステートメントには、GROUP BY 句が含まれています。|**SQLGetData**|  
|SL006|パラメーター配列は、位置指定要求ではサポートされません。|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData**は、順方向専用 (バッファーなし) カーソルでは使用できません。|**SQLGetData**|  
|SL009|**SQLFetch**または SQL フェッチ**スクロール**を呼び出す前にバインドされた列はありません。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|内部バッファーへのバインドの試行中に **、SQL_ERROR**を返しました。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|ステートメント オプションは **、SQLFetch**または**SQLFetchScroll**を呼び出した後でのみ有効です。|**SQLGetStmtAttr**|  
|SL012|カーソルがオープンされている間は、ステートメント・バインディングを変更することはできません。|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|位置指定要求が発行され、すべての列カウント・フィールドがバッファーに入れられていない。|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQL フェッチ**と**SQL フェッチスクロールを**混在させることはできません。|**フェッチ**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
