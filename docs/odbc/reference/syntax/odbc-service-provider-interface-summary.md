---
title: ODBC サービス プロバイダー インターフェイスの概要 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5f3c133b105c905b79589d86952658b6d39f0f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653389"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC サービス プロバイダー インターフェイスの概要
次の表では、ODBC サービス プロバイダー インターフェイスの機能について説明します。 構文とセマンティクスの各関数の詳細については、次を参照してください。 [ODBC サービス プロバイダー インターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)します。  
  
|関数名|目的|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|同じ[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)が接続ハンドルの代わりに、接続情報トークンの属性を設定します。|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|接続文字列をアプリケーションの接続情報のトークンに設定[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出します。|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|アプリケーションの接続情報のトークンに、データ ソース、ユーザーの ID とパスワードを設定する[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出します。|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID を取得します。|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|ドライバーが接続プール内の既存の接続を再利用できるかどうかを決定します。|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール内の接続を再利用できるない場合は、新しい接続を作成します。|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID がタイムアウトになったドライバーに通知します。|
