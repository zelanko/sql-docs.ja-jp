---
title: 標準のデータベース アクセス アーキテクチャ |Microsoft ドキュメント
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
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99e0a0eee2636a04d182076bb580b1ccf8069921
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="standard-database-access-architectures"></a>標準のデータベース アクセスのアーキテクチャ
前のセクションで説明されているデータベース アクセスのコンポーネントを調べて、結局のところ、2 つの — プログラミング インターフェイスと、データ ストリーム プロトコル — 適した候補となる標準化します。 その他の 2 つのコンポーネント: IPC メカニズムとネットワーク プロトコル-低すぎるレベルで存在するだけでなく、どちらも、ネットワークとオペレーティング システムに大きく依存します。 3 番目のアプローチもがある-ゲートウェイ — 標準化の可能性を提供します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [標準のプログラミング インターフェイス](../../odbc/reference/standard-programming-interface.md)  
  
-   [標準のデータ ストリーム プロトコル](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [標準のゲートウェイ](../../odbc/reference/standard-gateway.md)
