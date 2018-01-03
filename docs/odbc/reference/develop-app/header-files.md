---
title: "ヘッダー ファイル |Microsoft ドキュメント"
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
helpviewer_keywords: header files [ODBC]
ms.assetid: b4a03273-5e30-4d7b-826e-02f8f28ba078
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 197c7ef28124fb1b1c52facbec541913330c69c5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="header-files"></a>ヘッダー ファイル
Sql.h ヘッダー ファイルには、主要な ODBC インターフェイスへの準拠レベルの機能と関数のプロトタイプが含まれています。 Sqlext.h ヘッダー ファイルには、レベル 1 およびレベル 2 の API への準拠レベルで機能と関数のプロトタイプが含まれています。 Sqltypes.h ヘッダー ファイルには、型の定義と SQL データ型のインジケーターが含まれています。  
  
 すべてを含むヘッダー ファイル、 **#define**ODBCVER、アプリケーションやドライバー ODBC のさまざまなバージョンに対してコンパイルするように設定できます。  
  
 ISO CLI と開いているグループの CLI に合うようには、ヘッダー ファイルはへの呼び出しで使用される情報の種類のエイリアスを含める。 **SQLGetInfo**です。 次の表では、列「ODBC 名」はで情報の種類の ODBC 名前を示します。 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)です。 「ヘッダー ファイル内の別名」の列は、ISO CLI と開いているグループ CLI で使用される名前を示します。 次のマニフェスト名の実際の数値では、ODBC と標準の Cli の両方で同じです。 これらの別名には、ODBC 3 でコンパイルするには、標準に準拠したアプリケーションまたはドライバーが有効にする*.x*ヘッダー ファイルです。  
  
 これらの別名では、名前がわかりやすくなるように、ODBC 名の省略形の拡張を含めます。 "OUTER_JOIN"を「複数」、"OJ"および「トランザクション」に"TXN"に、"MAX"を「最大」、"LEN"に「長さ」、"MULT"に拡張します。  
  
|ODBC 名|ヘッダー ファイル内の別名|  
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
