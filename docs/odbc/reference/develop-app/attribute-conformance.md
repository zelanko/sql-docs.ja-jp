---
title: 属性への準拠 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44f1311d98f37412454ad2352366492a8d5a1768
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62672527"
---
# <a name="attribute-conformance"></a>属性の適合性
次の表では、これが適切に定義されている各 ODBC 環境属性の準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|コア|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] これは省略可能な機能であり適合性レベルの一部でないようです。  
  
 次の表では、これが適切に定義されている各 ODBC 接続属性の準拠レベルを示します。  
  
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
  
 [1] (必要なレベル 1) 接続レベルの非同期処理をサポートするアプリケーションをサポートしてが SQL_TRUE に呼び出すことによってこの属性を設定する必要があります**SQLSetConnectAttr**; 属性は、既定以外の値に設定可能な必要はありません値を通じて**SQLSetStmtAttr**します。 この属性をいずれの関数を使用して SQL_TRUE に設定 (レベル 2 に必要)、ステートメント レベルの非同期処理をサポートするアプリケーションがサポートする必要があります。  
  
 [2] のレベル 1 インターフェイスの適合性、ドライバーがドライバーで定義された既定値だけでなく、1 つの値をサポートする必要があります (呼び出すことによって利用可能な**SQLGetInfo** SQL_DEFAULT_TXN_ISOLATION オプションを使用)。 レベル 2 インターフェイスの適合性のドライバーで SQL_TXN_SERIALIZABLE もサポートする必要があります。  
  
 次の表では、これが適切に定義されている各 ODBC ステートメント属性の準拠レベルを示します。  
  
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
  
 [1] (必要なレベル 1) 接続レベルの非同期処理をサポートするアプリケーションをサポートしてが SQL_TRUE に呼び出すことによってこの属性を設定する必要があります**SQLSetConnectAttr**; 属性は、既定以外の値に設定可能な必要はありません値を通じて**SQLSetStmtAttr**します。 この属性をいずれの関数を使用して SQL_TRUE に設定 (レベル 2 に必要)、ステートメント レベルの非同期処理をサポートするアプリケーションがサポートする必要があります。  
  
 [2] のレベル 2 インターフェイスの適合性、ドライバーは SQL_CONCUR_READ_ONLY およびその他の少なくとも 1 つの値をサポートする必要があります。  
  
 [3] のレベル 1 インターフェイスの適合性、ドライバーは SQL_CURSOR_FORWARD_ONLY およびその他の少なくとも 1 つの値をサポートする必要があります。 レベル 2 インターフェイスの適合性、ドライバーはこのドキュメントで定義されているすべての値をサポートする必要があります。
