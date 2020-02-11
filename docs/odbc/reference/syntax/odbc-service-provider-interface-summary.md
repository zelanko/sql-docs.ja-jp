---
title: ODBC サービスプロバイダーインターフェイスの概要 |Microsoft Docs
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
ms.openlocfilehash: 0a97bed3bb921b9c881a98d8d9a9031ef7630f26
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111906"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC サービス プロバイダー インターフェイスの概要
次の表では、ODBC サービスプロバイダーのインターフェイス関数について説明します。 各関数の構文とセマンティクスの詳細については、「 [ODBC サービスプロバイダーインターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)」を参照してください。  
  
|関数名|目的|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)と同じですが、接続ハンドルではなく、接続情報トークンの属性を設定します。|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|接続文字列を、アプリケーションの[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出しの接続情報トークンに設定します。|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|データソース、ユーザー ID、およびパスワードを、アプリケーションの[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出しの接続情報トークンに設定します。|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID を取得します。|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|ドライバーが接続プール内の既存の接続を再利用できるかどうかを決定します。|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール内の接続を再利用できない場合は、新しい接続を作成します。|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID がタイムアウトしたことをドライバーに通知します。|
