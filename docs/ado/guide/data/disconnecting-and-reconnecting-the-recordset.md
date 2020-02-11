---
title: レコードセットの切断と再接続 |Microsoft Docs
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
ms.openlocfilehash: 9829ddfd7e625941c97bd3b2027c328a1fba93d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925510"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>レコードセットの切断と再接続
ADO で最も強力な機能の1つとして、データソースからクライアント側のレコードセットを開き、データソースからレコードセットを切断する機能があります。 レコードセットが切断されると、データソースへの接続を閉じることができます。これにより、管理に使用されたサーバー上のリソースが解放されます。 接続が切断された状態で、レコードセット内のデータを引き続き表示および編集し、後でデータソースに再接続して更新をバッチモードで送信することができます。  
  
 レコードセットを切断するには、カーソル位置を adUseClient にして開き、[ActiveConnection] プロパティを [なし] に設定します。 (C++ ユーザーは、ActiveConnection を NULL に設定して切断する必要があります)。  
  
 このセクションの後半では、切断されたレコードセットを使用します。このシナリオでは、レコードセットの永続化について説明し、クライアントコンピューターがネットワークに接続されていない状態で、レコードセット内のデータをアプリケーションで使用できるようにする必要があるシナリオに対処します。  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
