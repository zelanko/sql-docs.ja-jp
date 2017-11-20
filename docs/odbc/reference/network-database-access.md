---
title: "データベースへのアクセスをネットワーク |Microsoft ドキュメント"
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5220da346aea15e2dc56224001b0d803c90e0047
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="network-database-access"></a>データベースのネットワーク アクセス
ネットワーク経由でデータベースにアクセスするには、コンポーネント、それぞれから独立しておりの下にある、プログラミング インターフェイスの数が必要です。 次の図は、これらのコンポーネントについて示しています。  
  
 ![ネットワーク経由でデータベースにアクセスするにはコンポーネント](../../odbc/reference/media/pr04.gif "pr04")  
  
 各コンポーネントの詳細説明に従います。  
  
-   **プログラミング インターフェイス**プログラミング インターフェイスにはこのセクションで前述したよう、アプリケーションによって行われた呼び出しが含まれています。 これらのインターフェイス (埋め込まれた SQL では、SQL モジュール、および呼び出しレベルのインターフェイス) が、通常、ANSI または ISO 標準に基づいている、各 DBMS に一般的に固有のものです。  
  
-   **データ ストリーム プロトコル**データ ストリーム プロトコルは、データベース管理システムとクライアント間のデータ転送のストリームをについて説明します。 たとえば、プロトコルがストリームの残りの部分に含まれる内容を記述する最初のバイトを必要があります: SQL ステートメントを実行すると、返されたエラー値、またはデータが返されました。 このフラグは、ストリーム内のデータの残りの部分の形式が決まります。 たとえば、エラー ストリームには、フラグ、2 バイト整数エラー コード、2 バイト整数エラー メッセージの長さ、およびエラー メッセージが含まれます。  
  
     データ ストリーム プロトコルは、論理プロトコルでは、基になるネットワークによって使用されるプロトコルに依存しません。 したがって、1 つのデータ ストリーム プロトコルは、別のネットワークの数に一般的に使用できます。 データ ストリーム プロトコルは通常専用であり、特定の DBMS を使用する最適化されてます。  
  
-   **プロセス間通信メカニズム**プロセス間通信 (IPC) メカニズムが 1 つのプロセス間で通信するプロセスです。 例としては、名前付きパイプ、TCP/IP ソケット、DECnet sockets です。 IPC メカニズムの選択は、オペレーティング システムと使用されているネットワークによって制限されます。  
  
-   **ネットワーク プロトコル**ネットワーク経由でのデータ ストリームの転送に使用するネットワーク プロトコルです。 組み込みサポート、データを実装するために使用する IPC のメカニズムがストリーミング プロトコルだけでなくファイルの転送などの基本的なネットワーク操作をサポートして、プリンターの共有と見なされることができます。 ネットワーク プロトコルは、NetBEUI、TCP/IP、DECnet、および SPX/IPX され、各ネットワークに固有です。

