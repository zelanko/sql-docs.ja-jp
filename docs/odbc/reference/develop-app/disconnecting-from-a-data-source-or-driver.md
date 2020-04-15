---
title: データ ソースまたはドライバからの切断 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 154a571bce3a337d539216ce89c32420ab981bd8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300462"
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>データ ソースまたはドライバーからの切断
アプリケーションがデータ ソースの使用を終了すると **、SQLDisconnect**が呼び出されます。 **SQLDisconnect**は、接続に割り当てられているすべてのステートメントを解放し、データ ソースからドライバーを切断します。 トランザクションが処理中の場合は、エラーを返します。  
  
 切断後、アプリケーションは**SQLFreeHandle**を呼び出して接続を解放できます。 接続を解放した後、ODBC 関数の呼び出しで接続のハンドルを使用するのは、アプリケーション プログラミング エラーです。そうすることは、未定義だが、おそらく致命的な結果をもたらす。 **SQLFreeHandle**が呼び出されると、ドライバーは、接続に関する情報を格納するために使用される構造体を解放します。  
  
 アプリケーションは、別のデータ ソースに接続するか、同じデータ ソースに再接続するために、接続を再利用することもできます。 接続を維持する決定は、後で切断して再接続するのではなく、アプリケーション作成者が各オプションの相対的なコストを考慮する必要があります。データ ソースへの接続と接続の残りの両方は、接続メディアによっては比較的コストがかかる場合があります。 正しいトレードオフを行う場合、アプリケーションは、同じデータ ソースに対するさらなる操作の可能性とタイミングについても想定する必要があります。
