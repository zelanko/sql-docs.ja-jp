---
title: トランザクション |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dae1a7fc812e28c9ac51c1a2dc3f404ce8c420b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071161"
---
# <a name="transactions"></a>トランザクション
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーはローカル トランザクションのサポートを実装します。 コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。 複数のセッションにまたがるトランザクション制御を必要とするコンシューマー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが開始され、MS DTC で保持されているトランザクションに参加できます。  
  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コンシューマー セッションでの個々 の操作がのインスタンスに対して完全なトランザクションを構成、自動コミット トランザクション モードを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの自動コミット モードがローカルで、自動コミット トランザクションが 1 つのセッションよりも多くまたがることはありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **ITransactionLocal**インターフェイスは、明示的に使用して、暗黙的にトランザクションのインスタンスへの接続を 1 つのコンシューマー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが入れ子になったローカル トランザクションをサポートしていません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ローカル トランザクションのサポート](supporting-local-transactions.md)  
  
-   [分散トランザクションのサポート](supporting-distributed-transactions.md)  
  
-   [分離レベル&#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  