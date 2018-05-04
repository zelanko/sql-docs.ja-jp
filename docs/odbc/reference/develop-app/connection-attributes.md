---
title: 接続属性 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90119e72be2ea64da85fc6790b4e28b9e679a8f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connection-attributes"></a>接続属性
接続属性は、接続の特性です。 たとえば、トランザクションは接続レベルで行われるので、トランザクション分離レベルは 1 つの接続属性になります。 同様に、ログイン タイムアウト、または、タイムアウトするまでに接続しているときに待機する秒数は、接続属性です。  
  
 接続属性が設定されて**SQLSetConnectAttr**その現在の設定を使用して取得および**SQLGetConnectAttr**です。 場合**SQLSetConnectAttr**が呼び出されたとき、ドライバーが読み込まれると、ドライバー マネージャー ストアとの接続構造内の属性と、接続処理の一部としてドライバーに設定します。 アプリケーションが任意の接続属性を設定する必要はありません。すべての接続属性では、これらの一部は、ドライバー固有の既定値があります。  
  
 接続属性は、接続、またはいずれかと、ドライバーの属性に応じて前に、または後に設定できます。 ログイン タイムアウト (SQL_ATTR_LOGIN_TIMEOUT) が接続処理に適用され、有効な場合にのみ接続する前に設定します。 ドライバー マネージャーとドライバーの間に、ODBC カーソル ライブラリが存在しないため、接続する前に、ODBC カーソル ライブラリ (SQL_ATTR_ODBC_CURSORS) とネットワーク パケット サイズ (SQL_ATTR_PACKET_SIZE) を使用するかどうかを指定する属性を設定する必要があります、そのため読み込む必要がある、ドライバーの前にします。  
  
 属性を指定して、データ ソースは読み取り専用かどうか、または前に、または接続した後、ドライバーによって、読み取り/書き込み (SQL_ATTR_ACCESS_MODE) と、現在のカタログ (SQL_ATTR_CURRENT_CATALOG) を設定できます。 ただし、相互運用可能なアプリケーション設定に接続する前に一部のドライバーは接続後にこれらの変更をサポートしていないためです。  
  
 いくつかの接続属性では、そうでないときに、接続が行われる前に、既定値があります。 そうでは SQL_ATTR_ACCESS_MODE、SQL_ATTR_AUTOCOMMIT、SQL_ATTR_LOGIN_TIMEOUT、SQL_ATTR_ODBC_CURSORS、SQL_ATTR_TRACE、および SQL_ATTR_TRACEFILE です。  
  
 接続した後、翻訳接続属性 (SQL_ATTR_TRANSLATE_DLL SQL_ATTR_TRANSLATE_OPTION) を設定する必要があります。  
  
 その他のすべての接続属性は、いつでも設定できます。 詳細については、次を参照してください。、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)関数の説明。 (への呼び出しによって環境レベルの接続属性を設定することはできません**SQLSetEnvAttr**)。
