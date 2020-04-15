---
title: レベル 2 API 関数 (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- ODBC API functions [ODBC]
- API functions [ODBC]
- level 2 API functions [ODBC]
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1e181c5863d6b906eaf9a3ba499728c595f0449
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284182"
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>レベル 2 API 関数 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 このレベルの関数は、レベル 1 のインターフェイス準拠に加えて、ブックマーク、動的パラメータ、ODBC 関数の非同期実行のサポートなどの追加機能を提供します。  
  
|API 関数|Notes|  
|------------------|-----------|  
|**SQLBindParameter**|SQL ステートメント内のパラメーター・マーカーにバッファーを関連付けます。|  
|**SQLBrowseConnect**|属性と属性値の連続したレベルを返します。|  
|**データベースソース**|データ ソース名を一覧表示します。 ドライバー マネージャーによって実装されます。|  
|**SQLDescribeParam**|準備された SQL ステートメントに関連付けられたパラメーター・マーカーの説明を戻します。<br /><br /> ステートメントの解析に基づいて、パラメーターの最適な推測を返します。 パラメータの型を決定できない場合、SQL_VARCHARは長さ 2000 で返されます。|  
|**SQLDrivers**|ドライバー マネージャーによって実装されます。|  
|**フェッチ**|**SQLFetch**と似ていますが、各列の配列を使用して複数の行を返します。 結果セットは前方スクロール可能であり、カーソルが前方スクロールではなく静的に定義されている場合は、後方スクロール可能にできます。 デフォルトの列バインディングを持つ前方専用カーソルの場合、BUFFERSIZE 接続属性より大きいデータ・セットからの列データは、データ・バッファーに直接フェッチされます。 可変長のブックマークをサポートせず、ブックマークからのオフセット (0 以外) での行セットのフェッチはサポートしていません。|  
|**SQLForeignKeys**|単一のテーブル内の外部キーのリスト、または単一のテーブルを参照する他のテーブルの外部キーのリストを返します。|  
|**SQLMoreResults**|SELECT、UPDATE、INSERT、または DELETE ステートメントを含むステートメント ハンドル、hstmt、および保留中の結果がある場合は、その結果の処理を初期化するかどうかを決定します。<br /><br /> Oracle では、{resultset.... } エスケープ シーケンスを使用する場合、ストアド プロシージャからのみ複数の結果セットがサポートされます。|  
|**SQLNativeSql**|使用方法については、「 ストアド[プロシージャから配列パラメーターを返す](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md)」を参照してください。|  
|**SQLNumParams**|SQL ステートメント内のパラメーターの数を返します。 パラメータの数は **、SQLPrepare**に渡される SQL ステートメントの疑問符の数と同じである必要があります。|  
|**SQLPrimaryKeys**|テーブルの主キーを構成する列名を返します。|  
|**SQLProcedureColumns**|入力および出力パラメーター、戻り値、1 つのプロシージャの結果セット内の列、および 2 つの追加の列 OVERLOAD とORDINAL_POSITIONを返します。 オーバーロードは、Oracle データディクショナリビューのALL_ARGUMENTS表のオーバーロード列です。 ORDINAL_POSITIONは、Oracle データディクショナリビューのALL_ARGUMENTSテーブルの SEQUENCE 列です。 パッケージ化されたプロシージャーの場合、プロシージャー名列は*パッケージ名.プロシージャー名*フォーマットです。 プロシージャまたは関数を参照する、作成されたシノニムのプロシージャ列を返しません。|  
|**SQLProcedures**|データ ソース内のプロシージャの一覧を返します。 パッケージ化されたプロシージャーの場合、プロシージャー名列は*パッケージ名.プロシージャー名*フォーマットです。<br /><br /> Oracle ではパッケージ化されたプロシージャとパッケージ化された関数を区別する方法が提供されないため、ドライバーはPROCEDURE_TYPE列のSQL_PT_UNKNOWNを返します。|  
|**SQLSetPos**|行セット内のカーソル位置を設定します。 **SQLSetPos**と**SQLGetData**を使用すると、行セット内の特定の行にカーソルを配置した後、バインドされていない列から行を取得できます。 *fOption* SQL_ADDを使用して結果セットに追加された行は、結果セットの最後の行の後に追加されます。|  
|**スクロールオプション**|ステートメント ハンドル hstmt に関連付けられたカーソルの動作を制御するオプションを設定します。 詳細については、「[カーソルの種類と同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)」を参照してください。|
