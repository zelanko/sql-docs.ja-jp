---
title: "診断レコードとフィールド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- header records [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], diagnostic records
- ODBC error handling, diagnostic records
- SQLGetDiagField function
- diagnostic records [ODBC]
- errors [ODBC], diagnostic records
- fields [ODBC]
- status information [ODBC]
ms.assetid: 4949530c-62d1-4f1a-b592-144244444ce0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b2c800550b992735c0af6854a83d5ea28a2c597
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="diagnostic-records-and-fields"></a>診断レコードと診断フィールド
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  診断レコードは、ODBC 環境、接続、ステートメント、または記述子ハンドルに関連付けられています。 ODBC 関数から SQL_SUCCESS または SQL_INVALID_HANDLE 以外のリターン コードが返されるときは、その関数で呼び出されたハンドルに、情報メッセージまたはエラー メッセージが格納された診断レコードが関連付けられます。 これらの診断レコードは、同じハンドルを使用して別の関数が呼び出されるまで保持され、別の呼び出しが行われた時点で破棄されます。 1 つのハンドルに同時に関連付けることができる診断レコードの数に制限はありません。  
  
 診断レコードには、ヘッダー レコードと状態レコードの 2 種類があります。 ヘッダー レコードはレコード 0 です。状態レコードが存在する場合は、レコード 1 以降が状態レコードになります。 診断レコードのヘッダー レコードと状態レコードには、それぞれ異なるフィールドが含まれています。 また、ODBC コンポーネントでは、診断レコードに独自のフィールドを定義することもできます。  
  
 ヘッダー レコード内のフィールドには、リターン コード、行数、状態レコードの数、実行したステートメントの種類など、関数の実行に関する一般的な情報が保存されます。 ヘッダー レコードは、ODBC 関数から SQL_INVALID_HANDLE が返されない限り、常に作成されます。 ヘッダー レコードのフィールドの完全な一覧を参照してください。 [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md)です。  
  
 状態レコード内のフィールドには、SQLSTATE、ネイティブ エラー番号、診断メッセージ、列番号、行番号など、ODBC ドライバー マネージャー、ドライバー、またはデータ ソースから返される特定のエラーや警告に関する情報が保存されます。 状態レコードは、関数から SQL_ERROR、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_NEED_DATA、または SQL_STILL_EXECUTING が返された場合のみ作成されます。 状態レコード内のフィールドの完全な一覧を参照してください。 **SQLGetDiagField**です。  
  
 **SQLGetDiagRec** ODBC SQLSTATE、ネイティブ エラー番号、診断メッセージ フィールドと 1 つの診断レコードを取得します。 この機能は、ODBC 2 に似ています。*x * * * SQLError** 関数。 ODBC 3 で最も簡単なエラー処理関数です。*x*を繰り返し呼び出すは**SQLGetDiagRec**以降で、 *RecNumber*パラメーター 1 とインクリメントに設定*RecNumber*まで 1**SQLGetDiagRec** SQL_NO_DATA が返されます。 これは、ODBC 2 と同じです。*x*呼び出すアプリケーション**SQLError** SQL_NO_DATA_FOUND が返されるまでです。  
  
 ODBC 3 です。*x* ODBC 2 よりもはるかに診断情報をサポートしています*。x*です。 この情報が追加フィールドを使用して取得する診断レコードに格納されている**SQLGetDiagField**です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーで取得できるドライバー固有の診断フィールドが含まれている**SQLGetDiagField**です。 これらのドライバー固有のフィールドのラベルは、sqlncli.h で定義されています。 これらのラベルを使用して、各診断レコードに関連付けられた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の状態、重大度レベル、サーバー名、プロシージャ名、および行番号を取得します。 また、sqlncli.h には、ドライバーを使用してアプリケーションを呼び出す場合は、TRANSACT-SQL ステートメントを識別するコードの定義が含まれて**SQLGetDiagField**で*DiagIdentifier* SQL_DIAG_DYNAMIC_ に設定FUNCTION_CODE です。  
  
 **SQLGetDiagField**エラー情報を基になるドライバーからキャッシュを使用して ODBC ドライバー マネージャーによって処理されます。 ODBC ドライバー マネージャーでは、接続が正しく確立されるまでドライバー固有の診断フィールドをキャッシュしません。 **SQLGetDiagField**成功した接続が完了する前に、ドライバー固有の診断フィールドを取得するために呼び出さは SQL_ERROR を返します。 ODBC 接続関数から SQL_SUCCESS_WITH_INFO が返されても、その接続関数のドライバー固有の診断フィールドはまだ使用できません。 呼び出しを開始する**SQLGetDiagField**ドライバー固有の診断フィールド別の ODBC を行った後にのみの関数を呼び出した後、その接続関数。  
  
 ほとんどのエラーによって報告された、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを効果的に診断によって返される情報のみを使用して**SQLGetDiagRec**です。 ただし、ドライバー固有の診断フィールドから返される情報がエラーを診断するうえで重要になることもあります。 ODBC エラー ハンドラーを使用するアプリケーションをコーディングする際、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーも使用することをお勧めは**SQLGetDiagField**取得には、少なくとも、SQL_DIAG_SS_MSGSTATE と SQL_DIAG_SS_SEVERITYドライバー固有のフィールドです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コード内の複数の箇所で特定のエラーが発生した可能性がある場合は、SQL_DIAG_SS_MSGSTATE により、エラーの厳密な発生箇所がマイクロソフトのサポート エンジニアに報告されます。この情報は、問題の診断に役立つことがあります。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
