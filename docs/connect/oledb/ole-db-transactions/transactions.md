---
title: トランザクション |Microsoft Docs
description: OLE DB Driver for SQL Server のセッション
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 3cf4aa84b59e41976383b6d5d567579ba2b457bf
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022331"
---
# <a name="transactions"></a>トランザクション
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server の OLE DB Driver は、ローカル トランザクションのサポートを実装します。 コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。 複数のセッションにまたがってトランザクションを制御する必要があるコンシューマーの場合、OLE DB Driver for SQL Server を使用して、MS DTC によって起動および管理されるトランザクションを結合できます。  
  
 OLE DB Driver for SQL Server では、既定で自動コミット トランザクション モードが使用されます。このモードでは、コンシューマー セッションでの個々の操作が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに対する 1 つの完全なトランザクションを構成します。 OLE DB Driver for SQL Server の自動コミット モードはローカルなモードなので、自動コミット トランザクションが複数のセッションにまたがることはありません。  
  
 OLE DB Driver for SQL Server で公開される **ITransactionLocal** インターフェイスにより、コンシューマーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに対する 1 つの接続で、明示的および暗黙的に開始されたトランザクションを使用できます。 OLE DB Driver for SQL Server では、入れ子になったローカル トランザクションはサポートしません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ローカル トランザクションのサポート](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [分散トランザクションのサポート](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [分離レベル&#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
