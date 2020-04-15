---
title: レベル 1 API 関数 (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37305ee75ebeb0686bafe039f1102cb3c6e18674
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299952"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>レベル 1 API 関数 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 このレベルの関数は、コア インターフェイスの準拠に加えて、トランザクション サポートなどの追加機能を提供します。  
  
|API 関数|Notes|  
|------------------|-----------|  
|**SQLColumns**|テーブルの結果セットを作成します。 PUBLIC シノニムの列を要求する場合は、SYNONYMCOLUMNS 接続属性を設定し、空の文字列を*szTableOwner*引数として指定する必要があります。 PUBLIC シノニムの列を返す場合、ドライバーは、テーブル名列を空の文字列に設定します。 結果セットには、各行の末尾に追加の列 ORDINAL 位置が含まれます。 この値は、テーブル内の列の序数位置です。|  
|**SQLDriverConnect**|既存のデータ ソースに接続します。 詳細については、「[接続文字列の形式と属性](../../odbc/microsoft/connection-string-format-and-attributes.md)」を参照してください。|  
|**オプションを指定します。**|接続オプションの現在の設定を返します。 この関数は部分的にサポートされています。 ドライバーは *、fOption*引数のすべての値をサポートしていますが *、fOption*引数[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md)いくつかの*vParam*値をサポートしていません。 詳細については、「[接続オプション](../../odbc/microsoft/connect-options.md)」を参照してください。|  
|**SQLGetData**|指定された結果セットの現在のレコード内の単一のフィールドの値を取得します。|  
|**SQLGetFunctions**|サポートされているすべての関数に対して TRUE を返します。 ドライバー マネージャーによって実装されます。|  
|**SQLGetInfo**|接続ハンドル hdbc に関連付けられた Oracle およびデータ ソースの ODBC ドライバーに関する情報\*(SQLHDBC、SQLUSMALLINT、SQLPOINTER、SQLSMALLINT、および SQLSMALLINT など) を返します。 *hdbc*|  
|**オプションを指定します。**|ステートメント オプションの現在の設定値を返します。 詳細については、「[ステートメントオプション](../../odbc/microsoft/statement-options.md)」を参照してください。|  
|**SQLGetTypeInfo**|データ ソースでサポートされているデータ型に関する情報を返します。 ドライバーは、SQL 結果セット内の情報を返します。|  
|**SQLParamData**|ステートメント実行時にパラメーター データを指定するために**SQLPutData**と組み合わせて使用します。|  
|**SQLPutData**|アプリケーションが、ステートメントの実行時に、パラメーターまたは列のデータをドライバーに送信できるようにします。|  
|**オプションを指定します。**|接続の側面を制御するオプションへのアクセスを提供します。 この関数は部分的にサポートされています: ドライバーは*fOption*引数のすべての値をサポートしていますが *、fOption*引数[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md)いくつかの*vParam*値をサポートしていません。 詳細については、「[接続オプション](../../odbc/microsoft/connect-options.md)」を参照してください。|  
|**オプションを設定します。**|ステートメント ハンドル*hstmt*に関連するオプションを設定します。 詳細については、「[ステートメントオプション](../../odbc/microsoft/statement-options.md)」を参照してください。|  
|**SQLSpecialColumns**|テーブル内の行を一意に識別する列の最適なセットを取得します。|  
|**SQLStatistics**|単一のテーブルと、そのテーブルに関連付けられているインデックスまたはタグ名に関する統計情報のリストを取得します。 ドライバーは、結果セットとして情報を返します。|  
|**SQLTables**|**SQLTables**ステートメントのパラメーターで指定されたテーブル名の一覧を返します。 パラメーターを指定しない場合は、現在のデータ ソースに格納されているテーブル名を返します。 ドライバーは、結果セットとして情報を返します。<br /><br /> 列挙型の呼び出しは、リモート ビューまたはローカル のパラメーター化されたビューの結果セット エントリを受け取りません。 ただし、一意のテーブル名指定子を持つ**SQLTables の**呼び出しは、その名前を持つビューが存在する場合は、一致するビューを検索します。これにより、新しいテーブルを作成する前に、API で名前の競合をチェックできます。<br /><br /> PUBLIC シノニムは、TABLE_OWNER値 "" で返されます。<br /><br /> SYS またはシステムが所有するビューは、システム ビューとして識別されます。|
