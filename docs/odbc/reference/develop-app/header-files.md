---
title: ヘッダー ファイル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62364d828e7b1f1ed8c70cae7ae1fc7dc3bc33fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300192"
---
# <a name="header-files"></a>ヘッダー ファイル
Sql.h ヘッダー ファイルには、コア ODBC インターフェイス準拠レベルの関数と機能のプロトタイプが含まれています。 Sqlext.h ヘッダー ファイルには、レベル 1 とレベル 2 の API 準拠レベルの関数と機能のプロトタイプが含まれています。 Sqltypes.h ヘッダー ファイルには、SQL データ型の型定義とインジケータが含まれています。  
  
 ヘッダー ファイルには、アプリケーションまたはドライバーが ODBC の異なるバージョン用にコンパイルされるように設定できる **#define**、ODBCVER が含まれています。  
  
 ISO CLI およびオープン グループ CLI に合わせて、ヘッダー ファイルには**SQLGetInfo**の呼び出しで使用される情報の種類のエイリアスが含まれています。 次の表の 「ODBC 名」列は、ODBC [API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)の情報型の ODBC 名を示しています。 「ヘッダー・ファイル内の別名」列は、ISO CLI およびオープン・グループ CLI で使用される名前を示します。 これらのマニフェスト名の実際の数値は、ODBC と標準の CL の両方で同じです。 これらのエイリアスを使用すると、標準に準拠したアプリケーションまたはドライバーが ODBC *3.x*ヘッダー ファイルを使用してコンパイルできるようになります。  
  
 これらのエイリアスには、名前がよりわかりやすくなるように、ODBC 名の省略形の拡張が含まれます。 「MAX」は「最大」「レン」から「レン」から「マルチ」「マルチ」「OJ」から「OUTER_JOIN」、「TXN」から「トランザクション」に拡大されます。  
  
|ODBC 名|ヘッダー ファイルのエイリアス|  
|---------------|--------------------------|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAXIMUM_CATALOG_NAME_LENGTH|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAXIMUM_COLUMN_NAME_LENGTH|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAXIMUM_COLUMNS_IN_GROUP_BY|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAXIMUM_COLUMNS_IN_ORDER_BY|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAXIMUM_COLUMNS_IN_SELECT|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAXIMUM_COLUMNS_IN_TABLE|  
|SQL_MAX_CONCURRENT_ACTIVITIES|SQL_MAXIMUM_CONCURRENT_ACTIVITIES|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAXIMUM_CURSOR_NAME_LENGTH|  
|SQL_MAX_DRIVER_CONNECTIONS|SQL_MAXIMUM_DRIVER_CONNECTIONS|  
|SQL_MAX_IDENTIFIER_LEN|SQL_MAXIMUM_IDENTIFIER_LENGTH|  
|SQL_MAX_SCHEMA_NAME_LEN|SQL_MAXIMUM_SCHEMA_NAME_LENGTH|  
|SQL_MAX_STATEMENT_LEN|SQL_MAXIMUM_STATEMENT_LENGTH|  
|SQL_MAX_TABLE_NAME_LEN|SQL_MAXIMUM_TABLE_NAME_LENGTH|  
|SQL_MAX_TABLES_IN_SELECT|SQL_MAXIMUM_TABLES_IN_SELECT|  
|SQL_MAX_USER_NAME_LEN|SQL_MAXIMUM_USER_NAME_LENGTH|  
|SQL_MULT_RESULT_SETS|SQL_MULTIPLE_RESULT_SETS|  
|SQL_OJ_CAPABILITIES|SQL_OUTER_JOIN_CAPABILITIES|  
|SQL_TXN_CAPABLE|SQL_TRANSACTION_CAPABLE|  
|SQL_TXN_ISOLATION_OPTION|SQL_TRANSACTION_ISOLATION_OPTION|
