---
title: データからの切断ソースまたはドライバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2189c0fcc65fd4192e94da140e2d55ac86826137
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706420"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>データ ソースまたはドライバーからの切断
アプリケーションは、データ ソースの使用が完了したら、それを呼び出す**SQLDisconnect**します。 **SQLDisconnect**接続に割り当てられているすべてのステートメントを解放し、データ ソースからドライバーを切断します。 トランザクションがプロセスの場合は、エラーを返します。  
  
 アプリケーションを呼び出して、その後、 **SQLFreeHandle**接続を解放します。 これは、接続を解放した後、ODBC 関数呼び出しで、接続のハンドルを使用するアプリケーション プログラミング エラーこれには結果が未定義であるが、致命的な可能性があります。 ときに**SQLFreeHandle**を呼び出すと、ドライバーのリリースの接続に関する情報を格納する構造体を使用します。  
  
 また、アプリケーションすることは別のデータ ソースに接続するか、同じデータ ソースに再接続するのいずれかへの接続を再利用できます。 切断して、後で再接続するのではなく、接続されたままにするかどうかは、アプリケーションの作成者が各オプションの相対コストを検討することが必要です。データ ソースへの接続と接続の両方が比較的コストの高い接続メディアによってできます。 適切なトレードオフを行うには、アプリケーションは、尤度と同じデータ ソースの他の操作のタイミングについて想定を加える必要があります。
