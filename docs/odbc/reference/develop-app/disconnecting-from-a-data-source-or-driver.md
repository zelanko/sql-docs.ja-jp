---
title: データからの切断ソースまたはドライバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1e0e89632c1c39df415c8db3a9f29c9c724c2d9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>データからの切断ソースまたはドライバー
アプリケーションは、データ ソースの使用が完了したら、それを呼び出す**SQLDisconnect**です。 **SQLDisconnect**接続に割り当てられているすべてのステートメントを解放し、データ ソースからドライバーを切断します。 プロセスがトランザクションの場合は、エラーを返します。  
  
 切断後、アプリケーションが呼び出すことができます**SQLFreeHandle**接続を解放します。 これは、接続を解放した後、ODBC 関数の呼び出しで、接続ハンドルを使用するアプリケーション プログラミング エラーこれには定義されていないが、おそらく致命的な影響します。 ときに**SQLFreeHandle**が呼び出されると、ドライバーのリリースの接続に関する情報を格納する構造体を使用します。  
  
 また、アプリケーションすることは別のデータ ソースへの接続または再接続するに同じデータ ソースに、接続再利用できます。 切断して、後で再接続するとは異なり、接続されたままにするかどうかは、アプリケーションの作成者が各オプションの相対コストを検討することが必要です。データ ソースへの接続と接続の両方を比較的コストの高い接続メディアによって指定できます。 適切なバランスを取ってで、アプリケーションは尤度と同じデータ ソース上の他の操作のタイミングに関する前提条件を加える必要があります。
