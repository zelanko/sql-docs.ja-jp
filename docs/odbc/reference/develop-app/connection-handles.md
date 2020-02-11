---
title: 接続ハンドル |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ab8b94835fb9a6103436026a669c86f2401d57b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036431"
---
# <a name="connection-handles"></a>接続ハンドル
*接続*は、ドライバーとデータソースで構成されます。 接続ハンドルは、各接続を識別します。 接続ハンドルは、使用するドライバーだけでなく、そのドライバーと共に使用するデータソースを定義します。 ODBC (ドライバーマネージャーまたはドライバー) を実装するコードのセグメント内では、接続ハンドルは、次のような接続情報を含む構造体を識別します。  
  
-   接続の状態  
  
-   現在の接続レベルの診断  
  
-   接続で現在割り当てられているステートメントと記述子のハンドル  
  
-   各接続属性の現在の設定  
  
 ODBC では、ドライバーが複数の同時接続をサポートしている場合、その接続を防ぐことはできません。 そのため、特定の ODBC 環境では、複数の接続ハンドルが、さまざまなドライバーとデータソース、同じドライバーとさまざまなデータソース、または同じドライバーとデータソースへの複数の接続にポイントしている場合があります。 一部のドライバーでは、サポートするアクティブな接続の数が制限されています。**SQLGetInfo**の SQL_MAX_DRIVER_CONNECTIONS オプションは、特定のドライバーがサポートするアクティブな接続の数を指定します。  
  
 接続ハンドルは、主にデータソースへの接続 (**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**)、データソースからの切断 **(sqldisconnect**)、ドライバーとデータソース (**SQLGetInfo**) に関する情報の取得、診断の取得 (**SQLGetDiagField**と**SQLGetDiagRec**)、およびトランザクションの実行 (**SQLEndTran**) に使用されます。 また、接続属性 (**SQLSetConnectAttr**と**Sqlgetconnectattr**) を設定および取得するとき、および SQL ステートメントのネイティブ形式 (**sqlnativesql**) を取得するときにも使用されます。  
  
 接続ハンドルは**SQLAllocHandle**で割り当てられ、 **sqlfreehandle**で解放されます。
