---
title: 属性の準拠 |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2116a8a1bfcd042924d3dbe695036aeed136222
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="attribute-conformance"></a>属性への準拠
次の表では、これは適切に定義された各 ODBC 環境属性の準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|コア|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] これは省略可能な機能でありよう準拠レベルの一部ではありません。  
  
 次の表では、これは適切に定義された各 ODBC 接続属性の準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|コア|  
|SQL_ATTR_ASYNC_ENABLE|レベル 1 またはレベル 2 の [1]|  
|SQL_ATTR_AUTO_IPD|[レベル 2]|  
|SQL_ATTR_AUTOCOMMIT|[レベル 1]|  
|SQL_ATTR_CONNECTION_DEAD|[レベル 1]|  
|SQL_ATTR_CONNECTION_TIMEOUT|[レベル 2]|  
|SQL_ATTR_CURRENT_CATALOG|[レベル 2]|  
|SQL_ATTR_LOGIN_TIMEOUT|[レベル 2]|  
|SQL_ATTR_ODBC_CURSORS|コア|  
|SQL_ATTR_PACKET_SIZE|[レベル 2]|  
|SQL_ATTR_QUIET_MODE|コア|  
|SQL_ATTR_TRACE|コア|  
|SQL_ATTR_TRACEFILE|コア|  
|SQL_ATTR_TRANSLATE_LIB|コア|  
|SQL_ATTR_TRANSLATE_OPTION|コア|  
|SQL_ATTR_TXN_ISOLATION|レベル 1 またはレベル 2 の [2]|  
  
 [1] (レベル 1 に必要)、接続レベルの非同期処理をサポートするアプリケーションが SQL_TRUE に呼び出すことによってこの属性を設定をサポートする必要があります**SQLSetConnectAttr**; 属性に既定以外の値に設定可能な必要はありません値のを通じて**SQLSetStmtAttr**です。 SQL_TRUE のいずれかの関数を使用するこの属性を設定する (レベル 2 に必要)、ステートメント レベルの非同期処理をサポートするアプリケーションがサポートする必要があります。  
  
 [2] の第 1 レベル インターフェイスに準拠して、ドライバーがドライバーの定義済みの既定値だけでなく、1 つの値をサポートする必要があります (呼び出すことによって利用可能な**SQLGetInfo** SQL_DEFAULT_TXN_ISOLATION オプションを使用)。 レベル 2 インターフェイスに準拠して、ドライバーは、SQL_TXN_SERIALIZABLE をサポートもする必要があります。  
  
 次の表では、これは適切に定義された ODBC ステートメント属性ごとの準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|コア|  
|SQL_ATTR_APP_ROW_DESC|コア|  
|SQL_ATTR_ASYNC_ENABLE|レベル 1 またはレベル 2 の [1]|  
|SQL_ATTR_CONCURRENCY|レベル 1 またはレベル 2 の [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|[レベル 1]|  
|SQL_ATTR_CURSOR_SENSITIVITY|[レベル 2]|  
|SQL_ATTR_CURSOR_TYPE|コア/レベル 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|[レベル 2]|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|[レベル 2]|  
|SQL_ATTR_IMP_PARAM_DESC|コア|  
|SQL_ATTR_IMP_ROW_DESC|コア|  
|SQL_ATTR_KEYSET_SIZE|[レベル 2]|  
|SQL_ATTR_MAX_LENGTH|[レベル 1]|  
|SQL_ATTR_MAX_ROWS|[レベル 1]|  
|SQL_ATTR_METADATA_ID|コア|  
|SQL_ATTR_NOSCAN|コア|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|コア|  
|SQL_ATTR_PARAM_BIND_TYPE|コア|  
|SQL_ATTR_PARAM_OPERATION_PTR|コア|  
|SQL_ATTR_PARAM_STATUS_PTR|コア|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|コア|  
|SQL_ATTR_PARAMSET_SIZE|コア|  
|SQL_ATTR_QUERY_TIMEOUT|[レベル 2]|  
|SQL_ATTR_RETRIEVE_DATA|[レベル 1]|  
|SQL_ATTR_ROW_ARRAY_SIZE|コア|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|コア|  
|SQL_ATTR_ROW_BIND_TYPE|コア|  
|SQL_ATTR_ROW_NUMBER|[レベル 1]|  
|SQL_ATTR_ROW_OPERATION_PTR|[レベル 1]|  
|SQL_ATTR_ROW_STATUS_PTR|コア|  
|SQL_ATTR_ROWS_FETCHED_PTR|コア|  
|SQL_ATTR_SIMULATE_CURSOR|[レベル 2]|  
|SQL_ATTR_USE_BOOKMARKS|[レベル 2]|  
  
 [1] (レベル 1 に必要)、接続レベルの非同期処理をサポートするアプリケーションが SQL_TRUE に呼び出すことによってこの属性を設定をサポートする必要があります**SQLSetConnectAttr**; 属性に既定以外の値に設定可能な必要はありません値のを通じて**SQLSetStmtAttr**です。 SQL_TRUE のいずれかの関数を使用するこの属性を設定する (レベル 2 に必要)、ステートメント レベルの非同期処理をサポートするアプリケーションがサポートする必要があります。  
  
 [2] の第 2 レベル インターフェイスに準拠して、ドライバーは SQL_CONCUR_READ_ONLY およびその他の少なくとも 1 つの値をサポートする必要があります。  
  
 [3] をレベル 1 インターフェイスに準拠して、ドライバーは SQL_CURSOR_FORWARD_ONLY およびその他の少なくとも 1 つの値をサポートする必要があります。 レベル 2 インターフェイスに準拠して、ドライバーはこのドキュメントで定義されたすべての値をサポートする必要があります。
