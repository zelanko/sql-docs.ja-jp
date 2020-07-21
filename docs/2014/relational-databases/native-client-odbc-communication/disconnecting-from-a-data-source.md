---
title: データソースからの切断 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: rothja
ms.author: jroth
ms.openlocfilehash: 5db3b83ab65d854f3a4d2182d9a4a1314e097681
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021064"
---
# <a name="disconnecting-from-a-data-source"></a>データ ソースからの切断
  アプリケーションでデータソースの使用が完了すると、 **Sqldisconnect**が呼び出されます。 **Sqldisconnect**は、接続に割り当てられているすべてのステートメントを解放し、データソースからドライバーを切断します。 切断後、アプリケーションは[Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md)を呼び出して接続ハンドルを解放できます。 終了する前に、アプリケーションは**Sqlfreehandle**を呼び出して環境ハンドルを解放します。  
  
 切断後は、割り当てられていた接続ハンドルを再利用して、別のデータ ソースに接続したり、同じデータ ソースに再接続したりできます。 切断してから後で再接続するか、接続した状態を維持するかを決める際、アプリケーションの作成者は各操作の相対コストを考慮する必要があります。 接続メディアによっては、データ ソースに接続し、接続した状態を維持するのに比較的コストがかかる場合があります。 両者を比較検討する場合は、アプリケーションで同じデータ ソースに追加操作が行われる可能性やタイミングについて想定することも必要です。 また、アプリケーションで複数の接続が必要になる場合もあります。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;SQL Server との通信](communicating-with-sql-server-odbc.md)  
  
  
