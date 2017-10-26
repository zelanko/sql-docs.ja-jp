---
title: "Standard ゲートウェイ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9375bc6bf5054bdfeddd4fc5e53a1494d74eb88b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="standard-gateway"></a>Standard ゲートウェイ
A*ゲートウェイ*は、別のように 1 つの DBMS の原因となるソフトウェアの一部です。 ゲートウェイは、受け取りプログラミング インターフェイス、SQL の文法とデータ ストリーム プロトコルは単一の DBMS のプログラミングのインターフェイスでは、SQL の文法に変換されますおよびデータ ストリームの非表示の DBMS のプロトコル。 たとえば、Microsoft® SQL Server™ を使用するアプリケーションもアクセスできる DB2 データ ゲートウェイを介して、Micro Decisionware DB2;この製品は、DB2 SQL Server のように表示します。 ゲートウェイを使用している場合は、ターゲット データベースごとに別のゲートウェイを書き込む必要があります。  
  
 ゲートウェイは、Dbms のアーキテクチャの違いによる制限は、標準化のための適切な候補では。 ただし、すべての Dbms が、プログラミング インターフェイスを標準化する場合は、SQL の文法、およびデータ ストリーム プロトコルが DBMS が、標準として選択するのには、1 つの DBMS のですか。 確かに商用の DBMS ベンダーとは考えられません競合他社の製品を標準化することに同意します。 あり場合は、標準的なプログラミング インターフェイス、SQL の文法とデータ ストリーム プロトコルを開発すると、ゲートウェイは必要ありません。

