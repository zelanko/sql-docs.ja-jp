---
title: "ODBC のサービス プロバイダー インターフェイスの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e8f12f28d7163fbfeb92a257ebc12324cad664c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
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
