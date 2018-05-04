---
title: レベル 1 API 関数 (ODBC Driver for Oracle) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e3f6f331dc283c25fa9e6a36b7272db56763f53
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>レベル 1 API 関数 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 このレベルを指定してコア インターフェイスへの準拠の関数の他のトランザクションなどの追加機能をサポートします。  
  
|API 関数|注|  
|------------------|-----------|  
|**SQLColumns**|これは、指定したテーブルの列の一覧、テーブルまたはテーブルを結果セットを作成します。 パブリック シノニムの列を要求するときにする必要があります SYNONYMCOLUMNS 接続属性を設定して、空の文字列として指定された、 *szTableOwner*引数。 パブリック シノニムを列の値を返す、ときに、ドライバーは、空の文字列に、テーブル名 列を設定します。 結果セットには、追加の列、行ごとの最後の序数位置が含まれています。 この値は、テーブル内の列の序数位置です。|  
|**SQLDriverConnect**|既存のデータ ソースに接続します。 詳細については、「[接続文字列の形式と属性](../../odbc/microsoft/connection-string-format-and-attributes.md)です。|  
|**SQLGetConnectOption**|接続オプションの現在の設定を返します。 この関数は部分的にサポートされています。 ドライバーのすべての値をサポートしている、 *fOption*引数一部サポートされていませんが、 *vParam*の値を*fOption*引数[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). 詳細については、次を参照してください。[接続オプション](../../odbc/microsoft/connect-options.md)です。|  
|**SQLGetData**|指定された結果セットの現在のレコードの単一のフィールドの値を取得します。|  
|**SQLGetFunctions**|サポートされているすべての関数の場合は TRUE を返します。 ドライバー マネージャーによって実装されます。|  
|**SQLGetInfo**|SQLHDBC、SQLUSMALLINT、SQLPOINTER、SQLSMALLINT、SQLSMALLINT などの情報を返します\*、接続ハンドルに関連付けられた Oracle およびデータ ソース用の ODBC ドライバーは*hdbc*です。|  
|**SQLGetStmtOption**|ステートメント オプションの現在の設定を返します。 詳細については、次を参照してください。[ステートメント オプション](../../odbc/microsoft/statement-options.md)です。|  
|**SQLGetTypeInfo**|データ ソースによってサポートされるデータ型に関する情報を返します。 ドライバーは、SQL 結果セット内の情報を返します。|  
|**SQLParamData**|組み合わせて使用**SQLPutData**ステートメントの実行時にパラメーター データを指定します。|  
|**SQLPutData**|ステートメントの実行時にドライバーをパラメーターまたは列のデータを送信するアプリケーションを使用します。|  
|**SQLSetConnectOption**|接続の側面を制御するオプションへのアクセスを提供します。 この関数は部分的にサポートされています: ドライバーのすべての値をサポートしている、 *fOption*引数一部サポートされていませんが、 *vParam*の値を*fOption*引数[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md)です。 詳細については、次を参照してください。[接続オプション](../../odbc/microsoft/connect-options.md)です。|  
|**SQLSetStmtOption**|ステートメント ハンドルに関連するオプションを設定*hstmt*です。 詳細については、次を参照してください。[ステートメント オプション](../../odbc/microsoft/statement-options.md)です。|  
|**SQLSpecialColumns**|テーブル内の行を一意に識別する列の最適なセットを取得します。|  
|**SQLStatistics**|1 つのテーブルとインデックス、またはテーブルに関連付けられているタグ名に関する統計情報の一覧を取得します。 ドライバーは、情報の結果セットとしてを返します。|  
|**SQLTables**|内のパラメーターで指定されたテーブル名の一覧を返します、 **SQLTables**ステートメントです。 パラメーターが指定されていない場合は、現在のデータ ソースに格納されているテーブル名を返します。 ドライバーは、情報の結果セットとしてを返します。<br /><br /> 列挙型の呼び出しでは、リモート ビュー、またはローカル パラメーター化されたビューの結果セットのエントリは表示されません。 ただしへの呼び出し**SQLTables**一意テーブルの名前指定子は、一致を見つけるこのようなビューには、存在する場合、その名前を持つです。 これにより、API を新しいテーブルを作成する前に名前の競合を確認します。<br /><br /> パブリック シノニムが TABLE_OWNER 値と共に返される""です。<br /><br /> SYS またはシステムによって所有されているビューは、システム ビューとして識別されます。|
