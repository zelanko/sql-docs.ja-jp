---
title: ロックの種類 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AdLockBatchOptimistic [ADO]
- AdLockReadOnly [ADO]
- AdLockUnspecified [ADO]
- locks [ADO], types
- AdLockOptimistic [ADO]
- AdLockPessimistic [ADO]
ms.assetid: 12a978c0-b8a0-4ef0-87f0-a43c13659272
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d0ebfa4b6a822b0a18906c584af77a903b9bc93
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="types-of-locks"></a>ロックの種類
## <a name="adlockbatchoptimistic"></a>adLockBatchOptimistic  
 オプティミスティック バッチ更新を示します。 バッチ更新モードに必要です。  
  
 多くのアプリケーションでは、一度に多数の行をフェッチし、し、挿入、更新、または削除する行のセット全体を含む更新プログラムを調整する必要があります。 バッチ カーソルを 1 つのみのサーバーへのラウンド トリップが必要な更新プログラムのパフォーマンスを向上させるため、ネットワーク トラフィックが軽減されます。 バッチ カーソル ライブラリを使用して、静的カーソルを作成し、データ ソースから切断できます。 この時点での行に変更を加えると、後で再接続してバッチ内のデータ ソースに変更内容を投稿します。  
  
## <a name="adlockoptimistic"></a>adLockOptimistic  
 プロバイダーがオプティミスティック ロックを使用することを示します: レコードのロックを呼び出すときにのみ、**更新**メソッドです。 レコードとを呼び出したときに編集することを意味する可能性がある別のユーザーが、時間の間のデータを変更することがあります**更新**、これは、競合を作成します。 競合が発生する可能性が不足している状況でこの種類のロックを使用または衝突がすぐに解決できます。  
  
## <a name="adlockpessimistic"></a>adLockPessimistic  
 レコードごとの排他的ロックを指定します。 プロバイダーは、新機能は、通常は、データ ソースを編集する前に、すぐにレコードをロックして、レコードの編集を成功したことを確認するために必要です。 もちろん、つまり、呼び出すことにより、ロックが解放されるまでの編集を開始した後に、レコードが他のユーザーに使用できないこと**更新します。** 無理予約システムになど、データへの同時変更をシステムでこの種類のロックを使用します。  
  
## <a name="adlockreadonly"></a>adLockReadOnly  
 読み取り専用のレコードを示します。 データを変更することはできません。 読み取り専用ロックは、「最も高速」型のロックのレコードのロックを維持するために、サーバーは必要ないためです。  
  
## <a name="adlockunspecified"></a>adLockUnspecified  
 ロックの種類は指定しません。
