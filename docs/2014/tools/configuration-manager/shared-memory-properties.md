---
title: 共有メモリのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe28d3a716403975170c2d0b5deea2564b688c89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244122"
---
# <a name="shared-memory-properties"></a>[共有メモリのプロパティ] ダイアログ ボックス
  **[共有メモリのプロパティ]** ダイアログ ボックスの **[プロトコル]** ページは、共有メモリ プロトコルを有効または無効にするために使用します。 共有メモリは、使用できる最も単純なプロトコルであり、構成可能な設定はありません。 共有メモリ プロトコルを使用するクライアントは、同じコンピューター上で実行されている [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにしか接続できないため、ほとんどのデータベース操作にとって実用的ではありません。 共有メモリ プロトコルは、他のプロトコルが正しく構成されていない可能性がある場合に、トラブルシューティングを行うために使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動しないと、このプロトコルを有効または無効にできません。  
  
## <a name="options"></a>および  
 **Enabled**  
 可能な値は、 **[はい]** と **[いいえ]** です。 既定では、共有メモリ プロトコルは有効になっています。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルの選択](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [共有メモリ プロトコルを使用した有効な接続文字列の作成](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
