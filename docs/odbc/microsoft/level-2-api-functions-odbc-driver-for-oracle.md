---
title: "レベル 2 API 関数 (ODBC Driver for Oracle) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- functions [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], functions
- ODBC API functions [ODBC]
- API functions [ODBC]
- level 2 API functions [ODBC]
ms.assetid: d9f49520-72d7-4234-8635-260d0ce4199c
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 452af0d9daf66cee389f10029ea302efca14cf93
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="level-2-api-functions-odbc-driver-for-oracle"></a>レベル 2 API 関数 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 このレベルでの関数は、レベル 1 インターフェイスへの準拠とブックマーク、動的パラメーター、および ODBC 関数の非同期実行のサポートなどの追加機能を提供します。  
  
|API 関数|注|  
|------------------|-----------|  
|**SQLBindParameter**|バッファーを SQL ステートメントにパラメーター マーカーに関連付けます。|  
|**SQLBrowseConnect**|下位レベルの属性および属性値を返します。|  
|**SQLDataSources**|データ ソース名を一覧表示します。 ドライバー マネージャーによって実装されます。|  
|**SQLDescribeParam**|準備された SQL ステートメントに関連付けられているパラメーター マーカーの説明を返します。<br /><br /> どのようなパラメーターが、ステートメントの解析中に基づくの最善の推測を返します。 パラメーターの型を特定できない場合、SQL_VARCHAR は 2000 の長さを返します。|  
|**SQLDrivers**|ドライバー マネージャーによって実装されます。|  
|**SQLExtendedFetch**|ような**SQLFetch**列ごとに配列を使用して複数の行が返されます。 結果セットは前方スクロールし、旧バージョンとスクロールが静的、順方向専用カーソルが定義されている場合に行んだことができます。 既定の列のバインドに順方向専用カーソルの場合は、データ バッファーに直接 BUFFERSIZE 接続属性よりも大きいデータ セットから列データがフェッチされます。 可変長のブックマークをサポートしておらず、ブックマークからの (0) 以外のオフセットに行セットのフェッチをサポートしていません。|  
|**SQLForeignKeys**|1 つのテーブル、または 1 つのテーブルを参照している他のテーブルの外部キーの一覧内の外部キーの一覧を返します。|  
|**SQLMoreResults**|多くの結果が保留中かどうかを判断 hstmt、ステートメント ハンドルで SELECT、UPDATE、INSERT、または DELETE ステートメントを含むとそれらの結果の処理を初期化します。<br /><br /> Oracle は、{resultset...} エスケープ シーケンスを使用する場合にのみ、ストアド プロシージャから複数の結果セットをサポートします。|  
|**SQLNativeSql**|使用方法については、次を参照してください。[ストアド プロシージャから配列パラメーターを返す](../../odbc/microsoft/returning-array-parameters-from-stored-procedures.md)です。|  
|**SQLNumParams**|SQL ステートメントにパラメーターの数を返します。 パラメーターの数に渡された SQL ステートメントに疑問符 (?) の数に一致する必要があります**SQLPrepare**です。|  
|**SQLPrimaryKeys**|テーブルの主キーを構成する列の名前を返します。|  
|**SQLProcedureColumns**|入力と出力パラメーター、戻り値、1 つのプロシージャの結果セット内の列と 2 つの列、オーバー ロードと ORDINAL_POSITION の一覧を返します。 オーバー ロードは、Oracle データ辞書ビューの ALL_ARGUMENTS テーブルからオーバー ロード列です。 ORDINAL_POSITION は、Oracle データ辞書ビューの ALL_ARGUMENTS テーブルからシーケンス列です。 パッケージ化されたプロシージャの場合、プロシージャ名の列はで*packagename.procedurename*形式です。 プロシージャまたは関数を参照する、作成されたシノニムのプロシージャの列は返されません。|  
|**SQLProcedures**|データ ソース内のプロシージャの一覧を返します。 パッケージ化されたプロシージャの場合、プロシージャ名の列はで*packagename.procedurename*形式です。<br /><br /> Oracle で関数をパッケージにパッケージ化されたプロシージャを区別するための方法が提供されないため、ドライバーは PROCEDURE_TYPE 列を SQL_PT_UNKNOWN を返します。|  
|**SQLSetPos**|行セットのカーソル位置を設定します。 使用することができます**SQLSetPos**で**SQLGetData**行セット内の特定の行にカーソルを配置した後、バインドされていない列から行を取得します。 使用して設定の結果に追加された行*fOption* SQL_ADD が結果セットの最後の行の後に追加されます。|  
|**SQLSetScrollOptions**|Hstmt、ステートメント ハンドルに関連付けられているカーソルの動作を制御するオプションを設定します。 詳細については、「[カーソルの種類および同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)です。|
