---
title: 切断と再接続 Recordset |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a263903ab4f51d583b6533b6802fabd6c888f479
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700789"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>レコードセットの切断と再接続
ADO で検出された最も強力な機能の 1 つは、データ ソースからクライアント側のレコード セットを開いて、データ ソースからレコード セットを切断する機能です。 レコード セットを切断すると、データ ソースへの接続をするを閉じることが、それを維持するために使用されるサーバー上のリソースを解放します。 表示して、切断されているときに、レコード セット内のデータを編集し、後で、データ ソースに再接続し、バッチ モードで、更新を送信できます。  
  
 レコード セットを切断するには、adUseClient のカーソル位置で開くことと ActiveConnection プロパティを Nothing に設定します。 (C++ ユーザーが設定 ActiveConnection を切断する null)。  
  
 ときに使います切り離されたレコード セット後でこのセクションでは、クライアント コンピューターがネットワークに接続されていないつつ、アプリケーションで使用できるレコード セット内のデータを確保することが必要になるシナリオに対応するレコード セットの永続化について説明します。  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
