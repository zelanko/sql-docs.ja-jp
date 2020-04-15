---
title: スタンダードゲートウェイ |マイクロソフトドキュメント
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
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67551845c0dd8c6a28c0c4bc1c50f54ee8232df1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280075"
---
# <a name="standard-gateway"></a>標準のゲートウェイ
*ゲートウェイ*とは、ある DBMS が別の DBMS のように見えるソフトウェアです。 つまり、ゲートウェイは、単一の DBMS のプログラミング インターフェイス、SQL 文法、およびデータ ストリーム プロトコルを受け入れ、それをプログラミング インターフェイス、SQL 文法、および非表示の DBMS のデータ ストリーム プロトコルに変換します。 たとえば、Microsoft® SQL Server を使用するように記述されたアプリケーションは™マイクロディシジョンウェア DB2 ゲートウェイを介して DB2 データにアクセスすることもできます。この製品は、DB2 が SQL Server のように見えるようにします。 ゲートウェイを使用する場合は、ターゲットデータベースごとに異なるゲートウェイを作成する必要があります。  
  
 ゲートウェイは、DBMS 間のアーキテクチャの違いによって制限されますが、標準化の候補として適しています。 ただし、すべての DBMS が単一の DBMS のプログラミング インターフェイス、SQL 文法、およびデータ ストリーム プロトコルを標準化する場合、DBMS を標準として選択する必要がありますか。 確かに、商用 DBMS ベンダーは、競合他社の製品を標準化することに同意する可能性は低い。 また、標準のプログラミングインターフェイス、SQL文法、データストリームプロトコルが開発されている場合、ゲートウェイは必要ありません。
