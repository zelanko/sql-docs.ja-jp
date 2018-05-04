---
title: Standard ゲートウェイ |Microsoft ドキュメント
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
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: e1e75f97ded8f999d5fa945e0aafb04322d51540
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="standard-gateway"></a>Standard ゲートウェイ
A*ゲートウェイ*は、別のように 1 つの DBMS の原因となるソフトウェアの一部です。 ゲートウェイは、受け取りプログラミング インターフェイス、SQL の文法とデータ ストリーム プロトコルは単一の DBMS のプログラミングのインターフェイスでは、SQL の文法に変換されますおよびデータ ストリームの非表示の DBMS のプロトコル。 たとえば、Microsoft® SQL Server™ を使用するアプリケーションもアクセスできる DB2 データ ゲートウェイを介して、Micro Decisionware DB2;この製品は、DB2 SQL Server のように表示します。 ゲートウェイを使用している場合は、ターゲット データベースごとに別のゲートウェイを書き込む必要があります。  
  
 ゲートウェイは、Dbms のアーキテクチャの違いによる制限は、標準化のための適切な候補では。 ただし、すべての Dbms が、プログラミング インターフェイスを標準化する場合は、SQL の文法、およびデータ ストリーム プロトコルが DBMS が、標準として選択するのには、1 つの DBMS のですか。 確かに商用の DBMS ベンダーとは考えられません競合他社の製品を標準化することに同意します。 あり場合は、標準的なプログラミング インターフェイス、SQL の文法とデータ ストリーム プロトコルを開発すると、ゲートウェイは必要ありません。
