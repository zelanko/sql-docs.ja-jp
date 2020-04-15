---
title: ネットワーク データベースへのアクセス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2237c725d6fe3696d1f28d80c09f22183f718de8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295585"
---
# <a name="network-database-access"></a>ネットワーク データベース アクセス
ネットワーク経由でデータベースにアクセスするには、プログラミング インターフェイスに依存しないコンポーネントが必要です。 次の図は、これらのコンポーネントについて示しています。  
  
 ![ネットワーク経由でデータベースにアクセスするコンポーネント](../../odbc/reference/media/pr04.gif "pr04")  
  
 各コンポーネントの詳細は、次のとおりです。  
  
-   **プログラミング・インターフェース**このセクションで前述したように、プログラミング インターフェイスには、アプリケーションによって行われた呼び出しが含まれています。 これらのインタフェース (組み込み SQL、SQL モジュール、および呼び出しレベルのインタフェース) は、通常は ANSI または ISO 標準に基づいていますが、通常は各 DBMS に固有です。  
  
-   **データ ストリーム プロトコル**データ ストリーム プロトコルは、DBMS とそのクライアント間で転送されるデータのストリームを記述します。 たとえば、プロトコルでは、ストリームの残りの部分に含まれる内容を記述するために最初のバイトが必要になる場合があります。 ストリーム内の残りのデータの形式は、このフラグに依存します。 たとえば、エラー ストリームには、フラグ、2 バイト整数エラー コード、2 バイト整数エラー メッセージ長、およびエラー メッセージが含まれます。  
  
     データ ストリーム プロトコルは論理プロトコルであり、基盤となるネットワークで使用されるプロトコルとは独立しています。 したがって、単一のデータ ストリーム プロトコルは、一般的に、さまざまなネットワークで使用できます。 データ ストリーム プロトコルは、通常は独自に使用され、特定の DBMS で動作するように最適化されています。  
  
-   **プロセス間通信機構**プロセス間通信 (IPC) メカニズムは、プロセス間で通信するプロセスです。 例としては、名前付きパイプ、TCP/IP ソケット、および DECnet ソケットが含まれます。 IPC メカニズムの選択は、使用するオペレーティング システムとネットワークによって制約されます。  
  
-   **ネットワーク プロトコル**ネットワーク プロトコルは、ネットワーク経由でデータ ストリームを転送するために使用されます。 データ ストリーム プロトコルの実装に使用される IPC メカニズムをサポートする配管と見なすことができるだけでなく、ファイル転送や印刷共有などの基本的なネットワーク操作をサポートします。 ネットワーク プロトコルには、NetBEUI、TCP/IP、DECnet、および SPX/IPX が含まれ、各ネットワークに固有です。
