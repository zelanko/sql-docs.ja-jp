---
title: トランザクション |Microsoft ドキュメント
description: SQL Server の OLE DB ドライバーでのトランザクション
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31122886213b721eb36a452f651ad4ebd845e941
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="transactions"></a>トランザクション
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server の OLE DB Driver は、ローカル トランザクションのサポートを実装します。 コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。 複数のセッションにまたがるトランザクション制御を必要とすると、コンシューマー、OLE DB Driver for SQL Server は起動および MS DTC によって管理されるトランザクションを結合できます。  
  
 既定では、SQL Server の OLE DB Driver は、コンシューマー セッションでの個々 の操作がのインスタンスに対して完全なトランザクションを構成、自動コミット トランザクション モードを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 自動コミット モードの SQL Server の OLE DB Driver は、ローカルと、自動コミット トランザクションが 1 つのセッションよりも多くまたがることはありません。  
  
 OLE DB Driver for SQL Server を公開、 **ITransactionLocal**インターフェイスは、明示的に使用して、暗黙的にトランザクションのインスタンスへの接続を 1 つのコンシューマー[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 SQL Server の OLE DB Driver は、入れ子になったローカル トランザクションをサポートしません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ローカル トランザクションのサポート](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [分散トランザクションのサポート](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [分離レベル&#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
