---
title: "共有メモリのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 431107cdbdfdcfd97027500e77ea3cf35a989957
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="shared-memory-properties"></a>[共有メモリのプロパティ] ダイアログ ボックス
  **[共有メモリのプロパティ]**ダイアログ ボックスの **[プロトコル]** ページは、共有メモリ プロトコルを有効または無効にするために使用します。 共有メモリは、使用できる最も単純なプロトコルであり、構成可能な設定はありません。 共有メモリ プロトコルを使用するクライアントは、同じコンピューター上で実行されている [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにしか接続できないため、ほとんどのデータベース操作にとって実用的ではありません。 共有メモリ プロトコルは、他のプロトコルが正しく構成されていない可能性がある場合に、トラブルシューティングを行うために使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするにまたはプロトコルを無効に再起動する必要があります。  
  
## <a name="options"></a>オプション  
 **有効**  
 可能な値は **Yes** と **No**です。 既定では、共有メモリ プロトコルは有効になっています。  
  
## <a name="see-also"></a>参照  
 [ネットワーク プロトコルを選択します。](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [共有メモリ プロトコルを使用して有効な接続文字列を作成します。](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
