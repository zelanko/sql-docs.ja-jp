---
title: ODBC サービス プロバイダ インターフェイスの概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2f7e459cc7b89106bf1b7ebcd49c699d43da9f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298899"
---
# <a name="odbc-service-provider-interface-summary"></a>ODBC サービス プロバイダー インターフェイスの概要
次の表は、ODBC サービス プロバイダー インターフェイス関数について説明します。 各関数の構文とセマンティクスの詳細については[、「ODBC サービス プロバイダ インターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)」を参照してください。  
  
|関数名|目的|  
|-------------------|-------------|  
|[を使用します。](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)と同じですが、接続ハンドルではなく接続情報トークンに属性を設定します。|  
|[接続情報](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|アプリケーションの[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出しの接続文字列を接続文字列を接続文字列に設定します。|  
|[接続情報](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|アプリケーションの[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出しの接続情報トークンに、データ ソース、ユーザー ID、およびパスワードを設定します。|  
|[を使用します。](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID を取得します。|  
|[接続](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|ドライバーが接続プール内の既存の接続を再利用できるかどうかを決定します。|  
|[コネクト](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール内の接続を再利用できない場合は、新しい接続を作成します。|  
|[接続プール ID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|プール ID がタイムアウトしたことをドライバーに通知します。|
