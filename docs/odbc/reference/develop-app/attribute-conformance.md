---
title: 属性の適合性 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2880a35f4bdc997cc037cdd0d60720267ff4a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306403"
---
# <a name="attribute-conformance"></a>属性の適合性
次の表は、各 ODBC 環境属性の準拠レベルを示しています。  
  
|機能|一致レベル|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|コア|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] これはオプションの機能であり、準拠レベルの一部ではありません。  
  
 次の表は、各 ODBC 接続属性の準拠レベルを示しています。  
  
|機能|一致レベル|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|コア|  
|SQL_ATTR_ASYNC_ENABLE|レベル1/レベル2[1]|  
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
|SQL_ATTR_TXN_ISOLATION|レベル1/レベル2[2]|  
  
 [1] 接続レベルの非同期をサポートするアプリケーション (レベル 1 に必要) は **、SQLSetConnectAttr**を呼び出してこの属性をSQL_TRUEに設定することをサポートする必要があります。属性は **、 SQLSetStmtAttr**を使用してデフォルト値以外の値に設定する必要はありません。 ステートメント レベルの非同期をサポートするアプリケーション (レベル 2 に必須) は、どちらの関数を使用してもこの属性をSQL_TRUEに設定することをサポートする必要があります。  
  
 [2] レベル 1 のインターフェイスに準拠する場合、ドライバーはドライバー定義の既定値 (SQL_DEFAULT_TXN_ISOLATION オプションを使用して**SQLGetInfo**を呼び出すことによって利用可能) に加えて 1 つの値をサポートする必要があります。 レベル 2 のインターフェイス準拠の場合、ドライバーもSQL_TXN_SERIALIZABLEをサポートする必要があります。  
  
 次の表は、各 ODBC ステートメント属性の準拠レベルを示しています。  
  
|機能|一致レベル|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|コア|  
|SQL_ATTR_APP_ROW_DESC|コア|  
|SQL_ATTR_ASYNC_ENABLE|レベル1/レベル2[1]|  
|SQL_ATTR_CONCURRENCY|レベル1/レベル2[2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|[レベル 1]|  
|SQL_ATTR_CURSOR_SENSITIVITY|[レベル 2]|  
|SQL_ATTR_CURSOR_TYPE|コア/レベル2[3]|  
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
  
 [1] 接続レベルの非同期をサポートするアプリケーション (レベル 1 に必要) は **、SQLSetConnectAttr**を呼び出してこの属性をSQL_TRUEに設定することをサポートする必要があります。属性は **、 SQLSetStmtAttr**を使用してデフォルト値以外の値に設定する必要はありません。 ステートメント レベルの非同期をサポートするアプリケーション (レベル 2 に必須) は、どちらの関数を使用してもこの属性をSQL_TRUEに設定することをサポートする必要があります。  
  
 [2] レベル 2 のインターフェイスの準拠の場合、ドライバーは、SQL_CONCUR_READ_ONLYと少なくとも 1 つの他の値をサポートする必要があります。  
  
 [3] レベル 1 のインターフェイス準拠の場合、ドライバーは、SQL_CURSOR_FORWARD_ONLYと少なくとも 1 つの他の値をサポートする必要があります。 レベル 2 のインターフェイス準拠のドライバーは、このドキュメントで定義されているすべての値をサポートする必要があります。
