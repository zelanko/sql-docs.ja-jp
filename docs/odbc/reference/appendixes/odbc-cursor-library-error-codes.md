---
title: "ODBC カーソル ライブラリのエラー コード |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1dcdaf02010c150e40295226e1258e385cdf75f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-cursor-library-error-codes"></a>ODBC カーソル ライブラリのエラー コード
> [!IMPORTANT]  
>  この機能は、Microsoft Data Access Component の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 代わりに、ドライバーとサーバー カーソルを使用します。  
  
 ODBC カーソル ライブラリを返しますに記載されているだけでなく次 SQLSTATEs [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
> [!NOTE]  
>  カーソル ライブラリが状態レコード; 順序付けしませんドライバー マネージャーと ODBC 3 です。*x*ドライバーが状態レコードの順序を担当します。  
  
|SQLSTATE|Description|を返されることができます。|  
|--------------|-----------------|--------------------------|  
|01000|カーソルは更新できません。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|カーソル ライブラリが使用されません。 読み込みに失敗しました。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|カーソル ライブラリが使用されません。 不足しているドライバーのサポート。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|カーソル ライブラリが使用されません。 バージョンのドライバー マネージャーが一致しません。|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|ドライバーでは、sql_success_with_info が返されます。 警告メッセージが失われました。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|一般的なエラー: ファイル バッファーを作成できません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般的なエラー: ファイル バッファーから読み取ることができません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般的なエラー: ファイルのバッファーに書き込むことができません。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|一般的なエラー: を閉じるか、ファイル バッファーを削除できません。|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|検索可能な列にバインドされていないために、位置指定のリクエストを実行できません。|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|結果セットは、結合条件によって作成されたために、位置指定の要求を実行できませんでした。|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|バインドされたバッファーは、セグメントの最大サイズを超えています。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|結果セットが生成されませんでした、**選択**ステートメントです。|**SQLGetData**|  
|SL005|**選択**ステートメントに GROUP BY 句が含まれています。|**SQLGetData**|  
|SL006|位置指定のリクエストは、パラメーター配列はサポートされていません。|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData**順方向専用の (バッファ) カーソルでは使用できません。|**SQLGetData**|  
|SL009|呼び出しの前に列にバインドされていない**SQLFetch**または**SQLFetchScroll**です。|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol**の試行中に内部バッファーをバインド SQL_ERROR が返されます。|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|ステートメントのオプションは、呼び出した後にだけ有効**SQLFetch**または**SQLFetchScroll**です。|**SQLGetStmtAttr**|  
|SL012|カーソルが開いている間、ステートメントのバインディングは変更できません。|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|位置指定の要求が発行されがバッファー内のすべての列数のフィールドです。|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch**と**SQLFetchScroll**混在させることはできません。|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
