---
title: "共有メモリのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 71ed92d7b9ceffa23b89082526b69a10504c7ef6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="shared-memory-properties"></a>[共有メモリのプロパティ] ダイアログ ボックス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
**[共有メモリのプロパティ]**ダイアログ ボックスの **[プロトコル]** ページは、共有メモリ プロトコルを有効または無効にするために使用します。 共有メモリは、使用できる最も単純なプロトコルであり、構成可能な設定はありません。 共有メモリ プロトコルを使用するクライアントは、同じコンピューター上で実行されている [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにしか接続できないため、ほとんどのデータベース操作にとって実用的ではありません。 共有メモリ プロトコルは、他のプロトコルが正しく構成されていない可能性がある場合に、トラブルシューティングを行うために使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動しないと、このプロトコルを有効または無効にできません。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は **Yes** と **No**です。 既定では、共有メモリ プロトコルは有効になっています。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルを選択します。](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [共有メモリ プロトコルを使用して有効な接続文字列を作成します。](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
