---
title: "接続ハンドル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba20d3fcb6d943f4669774013dcb62c8ad896d8d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connection-handles"></a>接続ハンドル
A*接続*ドライバーと、データ ソースで構成されます。 接続ハンドルでは、各接続を識別します。 接続ハンドルは、使用するドライバーだけでなくそのドライバーを使用するデータ ソースを定義します。 ODBC ドライバー マネージャー (ドライバー) を実装するコードのセグメント内では、接続ハンドルは、次のような接続情報を格納する構造体を識別します。  
  
-   接続の状態  
  
-   現在の接続レベルの診断  
  
-   ステートメントとの接続で現在割り当てられている記述子のハンドル  
  
-   各接続の属性の現在の設定  
  
 ODBC は、ドライバーによってサポートされる場合、複数の同時接続を防止できません。 そのため、ODBC の特定の環境では、複数接続ハンドルは、さまざまなドライバーと同じドライバーをデータ ソースとデータ ソース、または同じドライバーとデータ ソースに対して複数の接続にもさまざまなをポイント可能性があります。 一部のドライバーをサポートします。 アクティブな接続の数を制限します。オプション、SQL_MAX_DRIVER_CONNECTIONS **SQLGetInfo**特定のドライバーをサポートしているアクティブな接続の数を指定します。  
  
 接続ハンドルは、主に使用して、データ ソースに接続するときに (**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**)、データから切断していますソース (**SQLDisconnect**)、ドライバーとデータ ソースに関する情報の取得 (**SQLGetInfo**)、診断を取得する (**SQLGetDiagField**と**SQLGetDiagRec**)、トランザクションを実行して (**SQLEndTran**)。 設定または接続属性を取得するときにも使用されます (**SQLSetConnectAttr**と**SQLGetConnectAttr**) SQL ステートメントのネイティブ形式を取得するときに、(**SQLNativeSql**).  
  
 接続ハンドルが割り当てられます**SQLAllocHandle**およびに解放された**SQLFreeHandle**です。

