---
title: ODBC のサービス プロバイダー インターフェイスの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bea3ed9605ae079a7ee1dce68c778c908ebf2fbd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916677"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC のサービス プロバイダー インターフェイスの概要
次の表では、ODBC サービス プロバイダー インターフェイスの機能について説明します。 各関数のセマンティクスと構文に関する詳細については、次を参照してください。 [ODBC サービス プロバイダー インターフェイス (SPI) 参照](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)です。  
  
|関数名|用途|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|同じ[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)が、接続ハンドルでの代わりに、接続情報トークンで属性を設定します。|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|アプリケーションのためのトークンの接続情報に、接続文字列を設定[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出します。|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|アプリケーションのためのトークンの接続情報に、データ ソース、ユーザー ID とパスワードを設定[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出します。|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID を取得します|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|ドライバーが接続プール内で既存の接続を再利用できるかどうかを判断します。|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール内の接続を再利用できるない場合は、新しい接続を作成します。|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID にタイムアウトになりましたことドライバーに通知します。|
