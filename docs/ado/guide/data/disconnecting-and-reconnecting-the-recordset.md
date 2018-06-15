---
title: 切断し、レコード セットを再接続 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b0aa191cc98716934c8fc87c12cb9fff39ecd73
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271471"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>接続を切断および再接続をレコード セット
ADO で見つかった最も強力な機能の 1 つは、データ ソースからクライアント側のレコード セットを開くし、データ ソースからレコード セットを切断する機能です。 レコード セットが切断されると、データ ソースへの接続をするを閉じることが、それを維持するために使用されるサーバー上のリソースを解放します。 引き続き表示および切断されているときに、レコード セット内のデータを編集し、後で、データ ソースに再接続し、バッチ モードで、更新を送信できます。  
  
 レコード セットを切断するには、adUseClient のカーソル位置で開き、ActiveConnection プロパティを Nothing に設定します。 (C++ ユーザーを設定、ActiveConnection を切断する null)。  
  
 おが切断されたレコード セット後このセクションのときに使用する必要があります、クライアント コンピューターがネットワークに接続されていないときに、アプリケーションで使用できるレコード セットからデータを持つようにシナリオに対応するレコード セットの保存について説明します。  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
