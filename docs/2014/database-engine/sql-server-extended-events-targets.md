---
title: SQL Server 拡張イベント ターゲット |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
caps.latest.revision: 50
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dbd3b218390cc1a49f7256a7f2cb79228ff8c3c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074220"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server 拡張イベント ターゲット
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 拡張イベント ターゲットは、イベントのコンシューマーです。 ターゲットは、ファイルに書き込んだり、イベント データをメモリ バッファーに格納したり、イベント データを集計することができます。 ターゲットは、データを同期的または非同期的に処理できます。  
  
 拡張イベントの設計上、ターゲットは、セッションごとに 1 回だけイベントを受け取ります。  
  
 拡張イベント セッションで使用できる、拡張イベントに用意されたターゲットは次のとおりです。  
  
-   [イベント カウンター](../../2014/database-engine/event-counter-target.md)  
  
     拡張イベント セッション中に発生した、すべての指定されたイベントをカウントします。 完全なイベント コレクションのオーバーヘッドを追加しなくても、負荷の特性に関する情報を取得できます。 これは、同期ターゲットです。  
  
-   [イベント ファイル](../../2014/database-engine/event-file-target.md)  
  
     イベント セッション出力を、メモリ バッファー全体からディスクに書き込みます。 これは、非同期ターゲットです。  
  
-   [イベント ペアリング](../../2014/database-engine/event-pairing-target.md)  
  
     ロックの取得とロックの解放など、対で発生するイベントが数多く存在します。 指定された 1 対のイベントの組み合わせが一致するかどうかを判定します。 これは、非同期ターゲットです。  
  
-   [Event Tracing for Windows (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] イベントを、Windows オペレーティング システムまたはアプリケーション イベント データと関連付けます。 これは、同期ターゲットです。  
  
-   [ヒストグラム](../../2014/database-engine/histogram-target.md)  
  
     指定されたイベント列またはアクションに基づいて、指定されたイベントが発生する回数をカウントします。 これは、非同期ターゲットです。  
  
-   [リング バッファー](../../2014/database-engine/ring-buffer-target.md)  
  
     先入れ先出し (FIFO) 順またはイベントごとの FIFO に基づいて、イベント データをメモリに格納します。 これは、非同期ターゲットです。  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../relational-databases/extended-events/extended-events.md)   
 [SQL Server 拡張イベント パッケージ](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [SQL Server 拡張イベント セッション](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [SQL Server 拡張イベント エンジン](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  