---
title: 接続属性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c295ce88eedf1d4cddc4173f5dea39c44b01f83d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299043"
---
# <a name="connection-attributes"></a>接続属性
接続属性は、接続の特性です。 たとえば、トランザクションは接続レベルで行われるので、トランザクション分離レベルは 1 つの接続属性になります。 同様に、ログイン タイムアウト、またはタイムアウト前に接続を試行する間に待機する秒数は、接続属性です。  
  
 接続属性は **、SQLSetConnectAttr**と、その現在の設定を**使用**して設定されます。 ドライバーが読み込まれる前に**SQLSetConnectAttr**が呼び出された場合、ドライバー マネージャーは、接続構造体に属性を格納し、接続プロセスの一部としてドライバーに設定します。 アプリケーションが接続属性を設定する必要はありません。すべての接続属性にはデフォルトがあり、一部はドライバー固有です。  
  
 接続属性は、接続の前または後に設定するか、または属性とドライバーに応じて設定できます。 ログイン タイムアウト (SQL_ATTR_LOGIN_TIMEOUT) は接続プロセスに適用され、接続前に設定されている場合にのみ有効です。 ODBC カーソル ライブラリは、ドライバー マネージャーとドライバーの間に存在するため、ドライバーの前に読み込む必要があるため、ODBC カーソル ライブラリ (SQL_ATTR_ODBC_CURSORS) とネットワーク パケット サイズ (SQL_ATTR_PACKET_SIZE) を使用するかどうかを指定する属性は、接続する前に設定する必要があります。  
  
 データ ソースが読み取り専用か読み取り/書き込み (SQL_ATTR_ACCESS_MODE) か、現在のカタログ (SQL_ATTR_CURRENT_CATALOG) をドライバーに応じて、接続の前または後に設定できるかどうかを指定する属性。 ただし、接続後にこれらの変更をサポートしていないドライバもあるため、相互運用可能なアプリケーションは接続前に設定します。  
  
 接続属性の中には、接続が確立される前にデフォルトを持つものもあれば、デフォルトでないものもあります。 SQL_ATTR_ACCESS_MODE、SQL_ATTR_AUTOCOMMIT、SQL_ATTR_LOGIN_TIMEOUT、SQL_ATTR_ODBC_CURSORS、SQL_ATTR_TRACE、SQL_ATTR_TRACEFILEです。  
  
 接続後に変換接続属性 (SQL_ATTR_TRANSLATE_DLLおよびSQL_ATTR_TRANSLATE_OPTION) を設定する必要があります。  
  
 その他の接続属性は、いつでも設定できます。 詳細については[、SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明を参照してください。 (接続属性は **、SQLSetEnvAttr**の呼び出しによって環境レベルで設定することはできません。
