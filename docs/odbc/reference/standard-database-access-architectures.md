---
title: "標準のデータベース アクセス アーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9d41800-9068-4b76-895a-32b2853692dd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff9ebb61d8a0446f4c6015dd5c0ae56c22ebfc45
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="standard-database-access-architectures"></a>標準のデータベース アクセスのアーキテクチャ
前のセクションで説明されているデータベース アクセスのコンポーネントを調べて、結局のところ、2 つの — プログラミング インターフェイスと、データ ストリーム プロトコル — 適した候補となる標準化します。 その他の 2 つのコンポーネント: IPC メカニズムとネットワーク プロトコル-低すぎるレベルで存在するだけでなく、どちらも、ネットワークとオペレーティング システムに大きく依存します。 3 番目のアプローチもがある-ゲートウェイ — 標準化の可能性を提供します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [標準的なプログラミング インターフェイス](../../odbc/reference/standard-programming-interface.md)  
  
-   [標準のデータ ストリーム プロトコル](../../odbc/reference/standard-data-stream-protocol.md)  
  
-   [Standard ゲートウェイ](../../odbc/reference/standard-gateway.md)

