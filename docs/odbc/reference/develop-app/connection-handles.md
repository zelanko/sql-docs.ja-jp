---
title: 接続ハンドル |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5b03e0733e35984350d2a218b885dc148ca8f8f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299022"
---
# <a name="connection-handles"></a>接続ハンドル
*接続*は、ドライバーとデータ ソースで構成されます。 接続ハンドルは、各接続を識別します。 接続ハンドルは、使用するドライバーだけでなく、そのドライバーで使用するデータ ソースを定義します。 ODBC (ドライバー マネージャーまたはドライバー) を実装するコードのセグメント内で、接続ハンドルは、次のような接続情報を含む構造体を識別します。  
  
-   接続の状態  
  
-   現在の接続レベルの診断  
  
-   接続に現在割り当てられているステートメントおよび記述子のハンドル  
  
-   各接続属性の現在の設定  
  
 ODBC では、ドライバーが複数の同時接続をサポートしている場合、それらを防ぐわけではありません。 したがって、特定の ODBC 環境では、複数の接続ハンドルが、さまざまなドライバーとデータ ソース、同じドライバーとさまざまなデータ ソース、あるいは同じドライバーとデータ ソースへの複数の接続を指している場合があります。 一部のドライバは、サポートするアクティブな接続の数を制限します。**SQLGetInfo**のSQL_MAX_DRIVER_CONNECTIONS オプションは、特定のドライバーがサポートするアクティブな接続の数を指定します。  
  
 接続ハンドルは、主に、データ ソース **(SQLConnect、SQLDriverConnect**、または**SQLBrowseConnect)** への接続、データ ソースからの切断 (**SQLDisconnect**) 、ドライバとデータ ソースに関する情報の取得 (**SQLGetInfo**) 、診断 (**SQLGetDiagField および SQLGetDiagRec** ) の取得、およびトランザクションの実行 (**SQLEndTran**) の実行時に使用されます。 **SQLDriverConnect** **SQLGetDiagRec** また、接続属性 (**SQLSetConnectAttr および SQLGetConnectAttr** ) を設定および取得する場合や、SQL ステートメントのネイティブ形式 (**SQLNativeSql**) を取得する場合にも使用されます。 **SQLGetConnectAttr**  
  
 接続ハンドルは**SQLAllocHandle**で割り当てられ **、SQLFreeHandle**で解放されます。
