---
title: トランザクション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1cdf0cbca45fc12dc5e61e4dca913d2e16af5ab5
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704473"
---
# <a name="transactions"></a>トランザクション
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、ローカルトランザクションサポートを実装します。 コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。 複数のセッションにまたがるトランザクション制御を必要とするコンシューマーの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは MS DTC によって開始および管理されるトランザクションに参加できます。  
  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは自動コミットトランザクションモードを使用します。このモードでは、コンシューマーセッションの各個別アクションがのインスタンスに対する完全なトランザクションで構成さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの自動コミットモードはローカルであり、自動コミットトランザクションが1つ以上のセッションにまたがることはありません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **ITransactionLocal**インターフェイスを公開します。これにより、コンシューマーは、のインスタンスへの1つの接続で、明示的かつ暗黙的にトランザクションを開始でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、入れ子になったローカルトランザクションをサポートしていません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ローカル トランザクションのサポート](supporting-local-transactions.md)  
  
-   [分散トランザクションのサポート](supporting-distributed-transactions.md)  
  
-   [分離レベル &#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
